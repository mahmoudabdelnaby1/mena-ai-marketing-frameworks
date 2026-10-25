# COD Serial-Returner Exclusion & Prepaid-Upgrade Win-Back Decision Aid (Egypt & KSA)
## <span dir="rtl">أداة قرار استبعاد «كثيري رفض استلام طلبات COD» وتحويلهم للدفع المسبق في حملات استعادة العملاء (`Win-Back`)</span>

> **Asset ID**: `FW-052` (`AMP-240`) | **Artifact Type**: `DECISION_AID` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent automated AI win-back and VIP discount flows from sending margin-destroying coupon codes to chronic Cash-on-Delivery (COD) non-receivers (`>40%` refusal rate) in Egypt and Saudi Arabia.
- **AR**: <span dir="rtl">منع سلاسل استعادة العملاء الآلية (`Win-Back`) من إرسال أكواد خصم مجزية للعملاء ذوي السجل المرتفع في رفض استلام طلبات الدفع عند الاستلام (`أكثر من 40% مرتجعات COD`) في مصر والسعودية، وتوجيههم حصرياً لعروض الدفع المسبق.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when building VIP tiers, win-back flows, replenishment reminders, or birthday/seasonal coupon automations in Egypt, KSA, or wider MENA.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند بناء شرائح العملاء المميزين (`VIP`) أو سلاسل استعادة العملاء (`Win-Back`) أو كوبونات الخصم الآلية في مصر والسعودية.</span>
- **When NOT to Use It (EN)**: Never define a 'High-Value / VIP Customer' in Klaviyo, HubSpot, Salla, or Zid using `Total Placed Orders` (`إجمالي الطلبات`)—always filter by `Fulfilled / Delivered & Collected Orders` (`الطلبات المكتملة والمسلمة`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تعرّف شريحة «العملاء المميزين VIP» بناءً على «إجمالي الطلبات المسجلة»؛ بل اعتمد حصرياً على «الطلبات المكتملة والمحصّلة فعلياً».</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Customer Historical Order Counts: `orders_placed_count`, `orders_delivered_count`, `orders_cod_refused_count`
- Round-trip Courier Cost per Refused COD Parcel (`~75–110 EGP` in Egypt / `~28–45 SAR` in KSA)
- Prepaid-Only Promo Code capability in storefront (`InstaPay / Card / Mada / Tabby / Tamara only`)

## 2. The Working `DECISION_AID` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Customer Net-Delivery Ratio (`NDR`) Win-Back Decision Matrix

#### 1. Calculate Customer Net-Delivery Ratio (`NDR`) & Refusal Tier
```python
def classify_customer_winback_tier(placed: int, delivered: int, cod_refused: int, net_revenue: float):
    if placed == 0:
        return "PROSPECT"
    refusal_rate = cod_refused / max(placed, 1)
    if cod_refused >= 2 and refusal_rate >= 0.40:
        return "TIER_3_CHRONIC_COD_RETURNER_PREPAID_ONLY"
    elif cod_refused == 1 and delivered == 0:
        return "TIER_2_SINGLE_UNFULFILLED_COD_NO_COUPON"
    elif delivered >= 2 and refusal_rate < 0.15:
        return "TIER_1_VERIFIED_DELIVERED_VIP"
    return "TIER_1B_STANDARD_DELIVERED_BUYER"
```

#### 2. Win-Back & Coupon Routing Table
| Customer Tier | Win-Back Eligibility | Allowed Incentive & Payment Constraint | Operational Action |
| :--- | :--- | :--- | :--- |
| **`TIER_1_VERIFIED_DELIVERED_VIP`** (`>= 2` delivered orders, `<15%` COD refusal) | **Full Win-Back + VIP Early Access** | Standard or VIP coupon (`10%–15%`) valid across all payment methods (`Prepaid`, `Tabby/Tamara`, `COD`). | Priority courier dispatch & loyalty rewards. |
| **`TIER_2_SINGLE_UNFULFILLED_COD_NO_COUPON`** (`1` placed COD order that was cancelled/refused, `0` delivered) | **Conditional Prepaid Nudge Only** | **Zero unconditional COD discount**. Offer free shipping or `10%` off **ONLY when paying via Prepaid (`InstaPay / Card / Mada / Tabby / Fawry Paid`)**. | Require WhatsApp OTP/address confirmation (`AMP-448`) if they choose COD again. |
| **`TIER_3_CHRONIC_COD_RETURNER_PREPAID_ONLY`** (`>= 2` refused COD parcels AND `>= 40%` refusal rate) | **`SUPPRESS FROM ALL COD PROMOTIONS`** | **Block COD option at checkout** (or restrict coupon code strictly to `Prepaid / Card / InstaPay / Mada`). | Exclude from Meta/Google Paid Remarketing custom audiences so ad spend is never wasted re-acquiring serial non-receivers (`AMP-062`). |

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Egyptian & Saudi D2C Skincare & Apparel Store (`18,000` past buyer profiles in Klaviyo).
- **Audit Discovery**: Klaviyo's default `'Win-Back Lapsed VIPs (3+ Orders)'` segment contained `1,140` profiles who had placed 3 to 6 COD orders and refused delivery on **every single one** (costing the store `~95,000 EGP` in wasted courier shipping fees), and the automated flow was emailing them `20% OFF + Free COD Shipping` every 45 days!

### Step B: Initial Output (`المخرج الأولي`)
- **Segmentation Overhaul**:
  1. Created `TIER_3_CHRONIC_COD_RETURNER` segment (`1,140` profiles with `>=2` refused COD orders and `>=40%` refusal rate) -> **Excluded from all COD win-back emails and paid Meta/Google retargeting audiences**.
  2. Updated `VIP` and `Standard Win-Back` segments to count **strictly `Fulfilled_Delivered_Orders >= 1` AND `COD_Refusal_Rate < 0.25`**.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added Prepaid Rehabilitation Path**: For `TIER_2` customers (`1` failed delivery, often due to courier timing while traveling), sent a polite win-back offering **`"خصم 10% إضافي + أولوية التوصيل عند الدفع المسبق عبر إنستاباي أو البطاقة البنكية أو مدى"`**.
2. **Synced Courier Webhook Status**: Verified that Bosta (Egypt) and SMSA/Aramex (KSA) `Returned_to_Sender / RTO` webhooks increment `orders_cod_refused_count` on the customer profile automatically.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `1,140` chronic COD non-receivers suppressed from COD discount flows and paid remarketing, cutting repeat RTO courier losses while preserving VIP incentives for genuinely delivered buyers.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An ESP syncs Shopify/Salla's `Orders Count` metric when the order is initially placed (`Financial Status: Pending` for COD) and never decrements it when the courier marks the parcel `RTO / Refused` 6 days later.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Base all lifecycle segmentation on the **`Delivered / Paid & Fulfilled`** webhook event (`Fulfillment Status == Fulfilled AND Financial Status == Paid`), never on initial `Placed Order` count.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Salla / Zid / Shopify / WooCommerce Order Status Sync to Klaviyo & HubSpot** | `supported` | [Official Docs](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) (`2026-10-25`) | In COD-heavy markets (Egypt merchant-measured payment mix from recent order records; KSA 15–30% COD), initial order creation (`Placed Order`) does not equal revenue collection; courier RTO status must update CRM profile properties. | Filter all win-back and VIP segments by `Financial Status == Paid` (which for COD only triggers after courier cash collection). |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: RTO (Return-to-Origin) Rate on Win-Back Campaign Orders (`Target: <10%`) and Net Margin per Win-Back Email Sent.
- **Baseline**: Prior 60-day RTO rate and courier loss on win-back orders.
- **Observation Window**: 30 days post-segmentation update.
- **Interpretation Boundary**: Filtering out chronic COD returners stops self-inflicted courier losses, while courier call-before-delivery protocols (`AMP-448`) govern first-time buyer delivery rates.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
- [E-commerce Growth in Egypt vs. Saudi Arabia vs. UAE](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) — *23HubLab* (Published `2026-05-01`, Accessed `2026-10-25`): Contrasts Egypt's high raw volume and high COD return risk with KSA/UAE higher AOV and digital payment adoption; highlights underexploited Egyptian Arabic SEO vs paid-only dependence.
- [Common Mistakes When Using AI in B2B Sales and Marketing](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) — *Founderz* (Published `2026-08-15`, Accessed `2026-10-25`): Automating B2B outreach and lead generation on top of uncleaned CRM data or without sales-marketing ICP alignment amplifies errors and lengthens the sales cycle.
