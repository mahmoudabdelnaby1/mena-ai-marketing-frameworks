# End-to-End Worked Example & Failure Recovery — `FW-086` (`AMP-444`)

- **Framework**: GA4 MENA Marketplace & E-Commerce Referral Reclassification Checklist (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`)
- **العنوان بالعربية**: قائمة فحص إعادة تصنيف المتاجر والأسواق العربية (`amazon.sa`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`) في `GA4` بدلاً من ضياعها في `Referral`
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Riyadh & Cairo Beauty Brand selling D2C on its own site (with Tabby, Tamara, and Paymob) AND linking from brand store pages/campaigns on `amazon.sa`, `noon.com`, and `niceonesa.com`.
- **Audit Findings Before Fix**:
  1. `38%` of all paid conversions in GA4 were attributed to `tabby.ai / referral`, `tamara.co / referral`, and `accept.paymob.com / referral` (destroying paid ad ROAS visibility!).
  2. Traffic arriving from `amazon.sa`, `amazon.eg`, and `noon.com` was buried inside generic `Referral` instead of `Shopping`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Applied Part 1 & Part 2 Configurations**:
  1. Added all 16 MENA payment/BNPL gateways (`tabby.ai`, `tamara.co`, `paymob.com`, `moyasar.com`, etc.) to `List Unwanted Referrals` (`_gl` session continuity preserved).
  2. Added the MENA Marketplace Regex to `Organic Shopping` and `Paid Shopping` in the Custom Channel Group above `Referral`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified `ignore_referrer=true` on Payment Return**: Confirmed in GA4 DebugView that completing a test order via Tabby and Paymob preserves the original `utm_source=meta / utm_medium=paid_social` session instead of starting a new `referral` session.
2. **Retroactive Verification**: Confirmed historical `amazon.sa` and `noon.com` sessions moved cleanly from `Referral` into `Organic/Paid Shopping`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Eliminated payment-gateway self-referral hijacking (`38%` of revenue restored to true acquisition channels) and classified all MENA marketplaces (`Amazon.sa/.ae/.eg`, `Noon`, `NiceOne`, `Haraj`, `B.TECH`) under `Shopping`.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An analyst puts `salla.sa` into the `Organic Shopping` Channel Group rule on a store whose own checkout is hosted on a `salla.sa` subdomain WITHOUT adding `salla.sa` to `Unwanted Referrals`—causing every checkout redirect to be counted as a new 'Organic Shopping' session!
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always complete **Part 1 (`List Unwanted Referrals`) FIRST** for your own store/checkout/payment domains, and reserve **Part 2 (`Shopping` Channel Regex)** for external third-party marketplaces where users discover your brand.
