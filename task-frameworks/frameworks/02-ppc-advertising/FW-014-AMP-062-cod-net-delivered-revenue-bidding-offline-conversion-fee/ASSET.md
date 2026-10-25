# FW-014: COD Net-Delivered Revenue Bidding & Offline Conversion Feedback Workflow (Egypt & KSA)
## مسار عمل تدريب خوارزميات الإعلانات على «طلبات الدفع عند الاستلام المسلّمة فعلياً» بدلاً من الطلبات الوهمية (مصر والسعودية)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-072`, `AMP-082`, `AMP-092`, `AMP-102`, `AMP-112`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Stop Meta and Google AI bidding from optimizing toward high-return Cash-on-Delivery (COD) impulse clickers by discounting front-end COD pixel values and feeding back courier-delivered conversions.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إيقاف خوارزميات Meta وGoogle عن استهداف شرائح العملاء الأكثر إلغاءً ورفضاً لطلبات الدفع عند الاستلام (COD) عبر خصم القيمة المبدئية للطلب وتغذية المنصة بالطلبات المسلّمة فعلياً.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: In Egypt and KSA, COD cancellations and courier refusals inflate front-end platform conversion metrics by 20–40% (23HubLab 2026 benchmark); an end-to-end OPERATING_FRAMEWORK aligning pixel event rules, value multipliers, and courier CAPI/Offline feedback fixes the optimization signal.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تؤدي إلغاءات ومرتجعات الدفع عند الاستلام (COD) في مصر والسعودية إلى تضخم التحويلات الظاهرية في المنصات الإعلانية بنسبة 20–40%؛ ويعالج هذا الإطار التشغيلي إشارة التحسين من البكسل حتى تسليم شركة الشحن.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when the merchant wants to evaluate delivered-order contribution, COD costs, and acquisition economics using its own order and courier data.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند الحاجة إلى تقييم هامش الطلبات المسلّمة وتكلفة الدفع عند الاستلام واقتصاديات اكتساب العميل اعتمادًا على بيانات المتجر نفسه.
- **When NOT to Use It (EN)**: Do not delay the primary browser/CAPI `Purchase` signal by 5–7 days waiting for physical courier delivery if that starves Meta's 7-day attribution window—use the Dual-Signal Expected-Value Multiplier below instead.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بإلغاء حدث `Purchase` الفوري تماماً والانتظار 5–7 أيام حتى تسليم المندوب إذا كان ذلك سيكسر نافذة الإحالة (7 أيام)؛ استخدم نظام المعامل الموزون المزدوج أدناه.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Historical Courier Delivery Rate (`Delivered_Rate = Delivered_Orders / Placed_Orders`) segmented by Payment Method (`Prepaid/Card/InstaPay/Tabby` vs. `COD`) and Governorate/Region
2. Meta Conversions API (CAPI) & Google Ads Enhanced Conversions for Leads / Offline Conversion Import access
3. WhatsApp/Phone Order Confirmation workflow (`AMP-448`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Conversions API (CAPI) & Google Ads Conversion Value Rules / Adjustments** | `supported` | [Official Reference](https://developers.facebook.com/documentation/ads-commerce/conversions-api) (`2026-10-25`) | Both Meta CAPI and Google Ads support dynamic `value` payloads at checkout and offline conversion adjustments up to 7 days (Meta) / 55–90 days (Google Ads). | If server-side courier webhook integration is unavailable, apply the checkout JS payment-method multiplier in Google Tag Manager immediately. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-072`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Prepaid card/Apple Pay/InstaPay-only checkout flows or server-side CAPI offline events triggered only on 'Delivered & Paid' OMS status.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-082`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Prepaid card/Apple Pay/InstaPay-only checkout flows or server-side CAPI offline events triggered only on 'Delivered & Paid' OMS status.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-092`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Prepaid card/Apple Pay/InstaPay-only checkout flows or server-side CAPI offline events triggered only on 'Delivered & Paid' OMS status.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-102`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Prepaid card/Apple Pay/InstaPay-only checkout flows or server-side CAPI offline events triggered only on 'Delivered & Paid' OMS status.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-112`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Prepaid card/Apple Pay/InstaPay-only checkout flows or server-side CAPI offline events triggered only on 'Delivered & Paid' OMS status.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Cairo Footwear & Apparel Brand (`1,200 EGP` average order value).
- **Historical Data**: Prepaid (Card/InstaPay/valU) delivery rate = `95%`; Cairo/Giza COD delivery rate = `74%`; Upper Egypt/Delta unconfirmed COD delivery rate = `58%`.
- **Problem**: Platform-reported Meta ROAS looked like `4.8x`, but after `34%` blended COD refusals and double-way courier fees (`95 EGP` per returned parcel), actual bank-collected ROAS was `2.6x`.
- **Human Review & Key Edits Applied**: 1. **Accounting vs. Bidding Separation**: Kept raw `order_total` (`1,200 EGP`) in a custom parameter `gross_order_value` for finance reporting while passing the expected-delivered value in the standard `value` field used by Meta's tROAS bidder.
2. **Prepaid Incentive Pairing**: Added a `50 EGP` instant discount / free shipping badge for InstaPay & Card on the checkout page (`AMP-386`) to reinforce the bidding shift.
- **Final Usable Output**: - Meta and Google Value-Bidding (`tROAS`) now optimize on risk-adjusted net delivered revenue (`value`) with daily Bosta/Aramex webhook sync updating Delivered Customer Lists.
- **What Can Go Wrong**: A media buyer switches the primary campaign conversion event to 'Courier Delivered' (which happens 5–8 days after the click in remote governorates); because Meta's optimal learning signal relies heavily on conversions within 24–72 hours of click, ad sets get stuck in 'Learning Limited'.
- **Correction & Fallback**: Always keep the immediate checkout `Purchase` event (with risk-discounted `value`) or same-hour `WhatsApp_Confirmed_Order` as the primary optimization event, and use 5-day Courier Delivered webhooks for Value Adjustments and Seed Audience building.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Net Collected Revenue ROAS (`Cash Collected from Courier + Prepaid / Total Ad Spend`) and COD Refusal Rate (`%`).
- **Baseline Definition**: Prior 30-day gap between Platform-Reported Revenue and Courier-Settled Cash.
- **Observation Window**: 28 days (covering 2 full courier settlement cycles and payday). *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Fixing bidding signals stops ads from chasing chronic COD non-receivers, but courier SLA speed and phone confirmation (`AMP-448`) still govern physical delivery success.
