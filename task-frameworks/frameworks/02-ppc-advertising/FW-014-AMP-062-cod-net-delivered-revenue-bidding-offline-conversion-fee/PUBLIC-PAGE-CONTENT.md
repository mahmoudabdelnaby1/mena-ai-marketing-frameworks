# COD Net-Delivered Revenue Bidding & Offline Conversion Feedback Workflow (Egypt & KSA)
## <span dir="rtl">مسار عمل تدريب خوارزميات الإعلانات على «طلبات الدفع عند الاستلام المسلّمة فعلياً» بدلاً من الطلبات الوهمية (مصر والسعودية)</span>

> **Asset ID**: `FW-014` (`AMP-062`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Stop Meta and Google AI bidding from optimizing toward high-return Cash-on-Delivery (COD) impulse clickers by discounting front-end COD pixel values and feeding back courier-delivered conversions.
- **AR**: <span dir="rtl">إيقاف خوارزميات Meta وGoogle عن استهداف شرائح العملاء الأكثر إلغاءً ورفضاً لطلبات الدفع عند الاستلام (COD) عبر خصم القيمة المبدئية للطلب وتغذية المنصة بالطلبات المسلّمة فعلياً.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when the merchant wants to evaluate delivered-order contribution, COD costs, and acquisition economics using its own order and courier data.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند الحاجة إلى تقييم هامش الطلبات المسلّمة وتكلفة الدفع عند الاستلام واقتصاديات اكتساب العميل اعتمادًا على بيانات المتجر نفسه.</span>
- **When NOT to Use It (EN)**: Do not delay the primary browser/CAPI `Purchase` signal by 5–7 days waiting for physical courier delivery if that starves Meta's 7-day attribution window—use the Dual-Signal Expected-Value Multiplier below instead.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بإلغاء حدث `Purchase` الفوري تماماً والانتظار 5–7 أيام حتى تسليم المندوب إذا كان ذلك سيكسر نافذة الإحالة (7 أيام)؛ استخدم نظام المعامل الموزون المزدوج أدناه.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Historical Courier Delivery Rate (`Delivered_Rate = Delivered_Orders / Placed_Orders`) segmented by Payment Method (`Prepaid/Card/InstaPay/Tabby` vs. `COD`) and Governorate/Region
- Meta Conversions API (CAPI) & Google Ads Enhanced Conversions for Leads / Offline Conversion Import access
- WhatsApp/Phone Order Confirmation workflow (`AMP-448`)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 3-Layer COD Bidding Signal Architecture

#### Layer 1: Payment-Method Value Weighting on Immediate Checkout `Purchase`
Instead of passing 100% of order value for unconfirmed COD orders at checkout, multiply the `value` parameter sent in the immediate Pixel/CAPI `Purchase` event by your verified historical **Net Delivery Probability**:
```javascript
// Checkout Purchase Event Value Discounting (Egypt & KSA COD Guardrail)
function calculateBiddingPurchaseValue(orderTotal, paymentMethod, governorateTier) {
  const deliveryMultiplier = {
    PREPAID_CARD_INSTAPAY_TABBY: 0.96, // 96% net fulfillment rate
    COD_METRO_CAIRO_RIYADH: 0.72,      // 72% historical COD delivery rate
    COD_REMOTE_HIGH_RETURN_ZONE: 0.55  // 55% historical COD delivery rate
  };
  const key = paymentMethod !== 'COD'
    ? 'PREPAID_CARD_INSTAPAY_TABBY'
    : (governorateTier === 'METRO' ? 'COD_METRO_CAIRO_RIYADH' : 'COD_REMOTE_HIGH_RETURN_ZONE');
  return Number((orderTotal * deliveryMultiplier[key]).toFixed(2));
}
```
- **Why This Works Immediately**: Under Value-Based Bidding (`Maximize Conversion Value` / `tROAS`), a `1,000 EGP` InstaPay/Card order sends `960 EGP` of bidding weight, whereas an unconfirmed remote COD order sends `550 EGP`, training Meta/Google to favor prepaid and high-delivery-probability buyers within the 1-day/7-day attribution window!

#### Layer 2: Same-Day WhatsApp Confirmed-Order Gate (`ConfirmedPurchase` Custom/Secondary Event)
- Trigger automated WhatsApp confirmation + address validation within 2 minutes of COD checkout (`AMP-448`).
- Fire a Server-Side CAPI / Google Ads conversion (`Order_Confirmed_WhatsApp`) ONLY when the buyer confirms the order and street/landmark.
- Exclude unconfirmed/fake-phone COD orders from your Custom Lookalike and Value Seed audiences.

#### Layer 3: Courier Webhook Offline Reconciliation (Bosta / Mylerz / Aramex / SMSA -> Google Ads & Meta CAPI)
- When the courier webhook transitions status to `DELIVERED_COLLECTED` (within 2–5 days), upload the final realized revenue via Google Ads Offline Conversion Adjustments (`GCLID`) and Meta CAPI (`fbp`/`fbc` + hashed phone/email) to build your **"100% Delivered Buyers" Seed Audience**.

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Cairo Footwear & Apparel Brand (`1,200 EGP` average order value).
- **Historical Data**: Prepaid (Card/InstaPay/valU) delivery rate = `95%`; Cairo/Giza COD delivery rate = `74%`; Upper Egypt/Delta unconfirmed COD delivery rate = `58%`.
- **Problem**: Platform-reported Meta ROAS looked like `4.8x`, but after `34%` blended COD refusals and double-way courier fees (`95 EGP` per returned parcel), actual bank-collected ROAS was `2.6x`.

### Step B: Initial Output (`المخرج الأولي`)
- **Applied Layer 1 Value Multipliers**:
  - Order #101 (`1,200 EGP` via InstaPay): Sends `value: 1140.00 EGP` to Meta Pixel + CAPI.
  - Order #102 (`1,200 EGP` via COD in Nasr City, Cairo): Sends `value: 888.00 EGP`.
  - Order #103 (`1,200 EGP` via COD in High-Return Zone without landmark): Sends `value: 696.00 EGP`.
- **Applied Layer 2 Audience Hygiene**: Excluded `210` cancelled/refused COD orders from the 1% Purchaser Lookalike seed.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Accounting vs. Bidding Separation**: Kept raw `order_total` (`1,200 EGP`) in a custom parameter `gross_order_value` for finance reporting while passing the expected-delivered value in the standard `value` field used by Meta's tROAS bidder.
2. **Prepaid Incentive Pairing**: Added a `50 EGP` instant discount / free shipping badge for InstaPay & Card on the checkout page (`AMP-386`) to reinforce the bidding shift.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Meta and Google Value-Bidding (`tROAS`) now optimize on risk-adjusted net delivered revenue (`value`) with daily Bosta/Aramex webhook sync updating Delivered Customer Lists.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A media buyer switches the primary campaign conversion event to 'Courier Delivered' (which happens 5–8 days after the click in remote governorates); because Meta's optimal learning signal relies heavily on conversions within 24–72 hours of click, ad sets get stuck in 'Learning Limited'.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always keep the immediate checkout `Purchase` event (with risk-discounted `value`) or same-hour `WhatsApp_Confirmed_Order` as the primary optimization event, and use 5-day Courier Delivered webhooks for Value Adjustments and Seed Audience building.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Conversions API (CAPI) & Google Ads Conversion Value Rules / Adjustments** | `supported` | [Official Docs](https://developers.facebook.com/documentation/ads-commerce/conversions-api) (`2026-10-25`) | Both Meta CAPI and Google Ads support dynamic `value` payloads at checkout and offline conversion adjustments up to 7 days (Meta) / 55–90 days (Google Ads). | If server-side courier webhook integration is unavailable, apply the checkout JS payment-method multiplier in Google Tag Manager immediately. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Net Collected Revenue ROAS (`Cash Collected from Courier + Prepaid / Total Ad Spend`) and COD Refusal Rate (`%`).
- **Baseline**: Prior 30-day gap between Platform-Reported Revenue and Courier-Settled Cash.
- **Observation Window**: 28 days (covering 2 full courier settlement cycles and payday).
- **Interpretation Boundary**: Fixing bidding signals stops ads from chasing chronic COD non-receivers, but courier SLA speed and phone confirmation (`AMP-448`) still govern physical delivery success.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
- [E-commerce Growth in Egypt vs. Saudi Arabia vs. UAE](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) — *23HubLab* (Published `2026-05-01`, Accessed `2026-10-25`): Contrasts Egypt's high raw volume and high COD return risk with KSA/UAE higher AOV and digital payment adoption; highlights underexploited Egyptian Arabic SEO vs paid-only dependence.
- [Payment Gateway Egypt: Fees, Comparison & Best Providers (2026)](https://digitology.co/payment-gateway-egypt/) — *Digitology Egypt* (Published `2026-08-07`, Accessed `2026-10-25`): Reports Use the merchant’s recent order records to estimate payment mix; warns that card-only checkouts address less than a quarter of Egyptian shoppers.
