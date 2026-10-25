# End-to-End Worked Example & Failure Recovery — `FW-051` (`AMP-239`)

- **Framework**: Cross-Border GCC & Egypt Automated Lifecycle Email Currency, VAT & BNPL Localization Checklist
- **العنوان بالعربية**: قائمة فحص توطين العملات وضريبة القيمة المضافة (`15% KSA / 5% UAE / 0% Qatar / 14% Egypt`) وخيارات الدفع في الرسائل الآلية
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: GCC & Egypt Luxury Oud & Perfumes Brand headquartered in Riyadh (`Base Currency: SAR`) selling across KSA, UAE, Kuwait, Qatar, and Egypt.
- **Problem**: Browse Abandonment email showed `450.00 SAR (شامل ضريبة 15% - ادفع عبر مدى)` to shoppers in Dubai (`AED`), Kuwait City (`KWD`), Doha (`QAR`), and Cairo (`EGP`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Deployed Dynamic Country-Aware Liquid Footer & Price Macro**:
  - Saudi Recipient (`SA`): `<bdi>450.00 ر.س</bdi> (شامل ضريبة القيمة المضافة 15%) | الدفع عبر: مدى، Apple Pay، تابي، تمارا`
  - UAE Recipient (`AE`): `<bdi>440.00 د.إ</bdi> (شامل ضريبة القيمة المضافة 5%) | الدفع عبر: Apple Pay، تابي، تمارا`
  - Kuwait Recipient (`KW`): `<bdi>36.500 د.ك</bdi> | الدفع عبر: كي نت (KNET)، Apple Pay، تابي`
  - Egypt Recipient (`EG`): `<bdi>4,950 ج.م</bdi> (شامل الضريبة) | الدفع عبر: إنستاباي، فوري، فاليو، أو عند الاستلام`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified URL Locale Parameter**: Appended `?currency={{ presentment_currency }}&country={{ person.country_code }}` to the email CTA link so clicking from the email opens the storefront pre-switched to the exact same currency shown in the email (`AMP-063`).
2. **Checked KWD 3-Decimal Formatting**: Confirmed Kuwaiti Dinar prices format cleanly to 3 decimal places.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Cross-border lifecycle templates live across all 7 MENA markets with 100% currency, VAT-rate, and local payment-method accuracy.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An email displays `440 AED` to a Dubai shopper, but clicking the product link opens the website in `SAR` (`450 ر.س`) because the deep link lacked the currency/market parameter.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always pass the market/currency deep-link parameter (`?country=AE&currency=AED` or country subfolder `/ae-ar/`) on every product link inside cross-border emails.
