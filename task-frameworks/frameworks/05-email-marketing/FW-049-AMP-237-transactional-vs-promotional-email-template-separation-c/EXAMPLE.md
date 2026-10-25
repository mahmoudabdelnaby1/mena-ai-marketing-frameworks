# End-to-End Worked Example & Failure Recovery — `FW-049` (`AMP-237`)

- **Framework**: Transactional vs. Promotional Email Template Separation Checklist (Saudi & UAE PDPL Compliance)
- **العنوان بالعربية**: قائمة فحص الفصل بين رسائل المعاملات (`الفواتير وتأكيد الطلب`) والرسائل الترويجية (الامتثال لنظام `PDPL` السعودي والإماراتي)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Riyadh & Dubai Home Decor Store on Shopify + Klaviyo.
- **Problem**: The default AI-designed `Order Confirmation` email had a huge `"🔥 25% OFF YOUR NEXT ORDER + 4 RECOMMENDED SOFAS"` banner taking up 60% of the email above the fold, sent to 100% of buyers (including 62% who did not tick the marketing opt-in box). Gmail routed the store's tax receipts into the `Promotions` tab and unconsented buyers complained.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Template Remediation**:
  1. Removed the top promotional hero banner and the 4-sofa upsell grid from the base `Order Confirmation` template.
  2. Moved the repeat-purchase offer into a separate `Post-Purchase Thank You` email triggered 3 days after delivery **strictly filtered to `marketing_consent == true`**.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **ZATCA e-Invoice QR Check**: Moved the itemized invoice summary and downloadable PDF link directly to the top of the `Order Confirmation` email so Saudi and UAE buyers see their receipt immediately.
2. **Verified Primary Tab Placement**: Tested the cleaned receipt on Gmail iOS/Web—landed 100% in the `Primary` inbox tab.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Pure transactional receipt template live for all buyers (`Primary` tab placement), with promotional cross-sells strictly isolated to opted-in subscribers (`marketing_consent == true`).

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A merchant adds `'تابعوا عروض الجمعة البيضاء بخصم 50% على الرابط...'` to the footer of their WhatsApp `UTILITY` shipping-update template; Meta automatically reclassifies the template from `UTILITY` to `MARKETING`, increasing per-message cost and blocking delivery to users capped on marketing messages (`AMP-441`).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Keep transactional Email, SMS, and WhatsApp `UTILITY` templates **100% free of promotional links, discount codes, or cross-sell calls to action**.
