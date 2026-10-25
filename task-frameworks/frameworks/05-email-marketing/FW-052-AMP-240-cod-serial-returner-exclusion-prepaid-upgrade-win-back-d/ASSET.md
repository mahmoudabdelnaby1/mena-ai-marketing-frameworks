# FW-052: COD Serial-Returner Exclusion & Prepaid-Upgrade Win-Back Decision Aid (Egypt & KSA)
## أداة قرار استبعاد «كثيري رفض استلام طلبات COD» وتحويلهم للدفع المسبق في حملات استعادة العملاء (`Win-Back`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-250`, `AMP-260`, `AMP-270`, `AMP-280`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent automated AI win-back and VIP discount flows from sending margin-destroying coupon codes to chronic Cash-on-Delivery (COD) non-receivers (`>40%` refusal rate) in Egypt and Saudi Arabia.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع سلاسل استعادة العملاء الآلية (`Win-Back`) من إرسال أكواد خصم مجزية للعملاء ذوي السجل المرتفع في رفض استلام طلبات الدفع عند الاستلام (`أكثر من 40% مرتجعات COD`) في مصر والسعودية، وتوجيههم حصرياً لعروض الدفع المسبق.
- **Why `DECISION_AID` Fits This User Job (EN)**: AI CRM segmentation tools normally trigger win-back discounts based on `Placed_Orders >= 2 AND Days_Since_Last_Order >= 60` without checking whether those orders were actually **delivered** or refused at the doorstep (`COD Returned to Sender`, which costs the merchant double shipping fees); a quantitative DECISION_AID segments win-back flows by Net Delivery Ratio.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: تطلق أدوات أتمتة البريد والـ CRM حملات استعادة العملاء (`Win-Back`) بناءً على «عدد الطلبات المسجلة» دون فحص ما إذا كانت تلك الطلبات قد سُلّمت فعلاً أم رُفض استلامها عند الباب (مما يكبد المتجر رسوم شحن ذهاباً وإياباً)؛ لذا تفصل أداة القرار هذه الشرائح حسب نسبة التسليم الفعلي.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when building VIP tiers, win-back flows, replenishment reminders, or birthday/seasonal coupon automations in Egypt, KSA, or wider MENA.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند بناء شرائح العملاء المميزين (`VIP`) أو سلاسل استعادة العملاء (`Win-Back`) أو كوبونات الخصم الآلية في مصر والسعودية.
- **When NOT to Use It (EN)**: Never define a 'High-Value / VIP Customer' in Klaviyo, HubSpot, Salla, or Zid using `Total Placed Orders` (`إجمالي الطلبات`)—always filter by `Fulfilled / Delivered & Collected Orders` (`الطلبات المكتملة والمسلمة`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تعرّف شريحة «العملاء المميزين VIP» بناءً على «إجمالي الطلبات المسجلة»؛ بل اعتمد حصرياً على «الطلبات المكتملة والمحصّلة فعلياً».

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Customer Historical Order Counts: `orders_placed_count`, `orders_delivered_count`, `orders_cod_refused_count`
2. Round-trip Courier Cost per Refused COD Parcel (`~75–110 EGP` in Egypt / `~28–45 SAR` in KSA)
3. Prepaid-Only Promo Code capability in storefront (`InstaPay / Card / Mada / Tabby / Tamara only`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Salla / Zid / Shopify / WooCommerce Order Status Sync to Klaviyo & HubSpot** | `supported` | [Official Reference](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) (`2026-10-25`) | In COD-heavy markets (Egypt merchant-measured payment mix from recent order records; KSA 15–30% COD), initial order creation (`Placed Order`) does not equal revenue collection; courier RTO status must update CRM profile properties. | Filter all win-back and VIP segments by `Financial Status == Paid` (which for COD only triggers after courier cash collection). |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-250`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Filtering lifecycle retention segments by net delivered revenue and COD completion ratio.; Specifically impacts Egyptian brands operating in EGP where Cash on Delivery (merchant-measured payment mix from recent order records), Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-260`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Filtering lifecycle retention segments by net delivered revenue and COD completion ratio.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-270`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Filtering lifecycle retention segments by net delivered revenue and COD completion ratio.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-280`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Filtering lifecycle retention segments by net delivered revenue and COD completion ratio.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Egyptian & Saudi D2C Skincare & Apparel Store (`18,000` past buyer profiles in Klaviyo).
- **Audit Discovery**: Klaviyo's default `'Win-Back Lapsed VIPs (3+ Orders)'` segment contained `1,140` profiles who had placed 3 to 6 COD orders and refused delivery on **every single one** (costing the store `~95,000 EGP` in wasted courier shipping fees), and the automated flow was emailing them `20% OFF + Free COD Shipping` every 45 days!
- **Human Review & Key Edits Applied**: 1. **Added Prepaid Rehabilitation Path**: For `TIER_2` customers (`1` failed delivery, often due to courier timing while traveling), sent a polite win-back offering **`"خصم 10% إضافي + أولوية التوصيل عند الدفع المسبق عبر إنستاباي أو البطاقة البنكية أو مدى"`**.
2. **Synced Courier Webhook Status**: Verified that Bosta (Egypt) and SMSA/Aramex (KSA) `Returned_to_Sender / RTO` webhooks increment `orders_cod_refused_count` on the customer profile automatically.
- **Final Usable Output**: - `1,140` chronic COD non-receivers suppressed from COD discount flows and paid remarketing, cutting repeat RTO courier losses while preserving VIP incentives for genuinely delivered buyers.
- **What Can Go Wrong**: An ESP syncs Shopify/Salla's `Orders Count` metric when the order is initially placed (`Financial Status: Pending` for COD) and never decrements it when the courier marks the parcel `RTO / Refused` 6 days later.
- **Correction & Fallback**: Base all lifecycle segmentation on the **`Delivered / Paid & Fulfilled`** webhook event (`Fulfillment Status == Fulfilled AND Financial Status == Paid`), never on initial `Placed Order` count.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: RTO (Return-to-Origin) Rate on Win-Back Campaign Orders (`Target: <10%`) and Net Margin per Win-Back Email Sent.
- **Baseline Definition**: Prior 60-day RTO rate and courier loss on win-back orders.
- **Observation Window**: 30 days post-segmentation update. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Filtering out chronic COD returners stops self-inflicted courier losses, while courier call-before-delivery protocols (`AMP-448`) govern first-time buyer delivery rates.
