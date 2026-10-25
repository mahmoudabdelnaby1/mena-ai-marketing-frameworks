# End-to-End Worked Example & Failure Recovery — `FW-016` (`AMP-064`)

- **Framework**: Saudi, UAE & Egyptian False-Discount & Promotional Compliance Checklist
- **العنوان بالعربية**: قائمة فحص الامتثال لقوانين التخفيضات والعروض الترويجية في السعودية والإمارات ومصر (منع غرامات التخفيضات الوهمية)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: Riyadh & Cairo Electronics Store White Friday Meta + Google Ad Copy.
- **Draft AI Copy**: `"🔥 جنون الجمعة البيضاء! خصم 75% على كل الموقع لمدة ساعتين فقط! السعر قبل: 2000 ريال — الآن: 499 ريال فقط! الكمية على وشك النفاد!"`
- **Actual Store Ledger**: The item sold for `599 SAR` all of October (never `2,000 SAR`), store-wide discounts range from `10% to 30%`, and the Saudi Ministry of Commerce discount permit number was omitted.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Audit Verdict**: **`BLOCKED — CRITICAL STATUTORY VIOLATION (KSA & EGYPT)`**
  1. Fake baseline price (`2,000 SAR` vs actual 30-day price `599 SAR`) violates Saudi E-Commerce Law and Egypt Law 181/2018 (`غرامة تصل لمليون ريال / 2 مليون جنيه`).
  2. False `"75% على كل الموقع"` claim when actual range is `10%–30%`.
  3. Missing Saudi Ministry of Commerce Discount License display.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Corrected Price Maths**: Set `السعر السابق: 599 ر.س` and `السعر بعد الخصم: 499 ر.س (شامل الضريبة)` (an honest `16.7%` saving).
2. **Added Permit & Window**: Added `"مثال افتراضي: [مرجع التصريح الذي يقدمه العميل] — تُراجع فترة العرض كما تظهر في المصدر الرسمي الحالي"`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- **Compliant KSA Ad Copy**:
  `"عروض الجمعة البيضاء المعتمدة! خصومات من 10% حتى 30% على الأجهزة المختارة. السعر قبل الخصم: 599 ر.س | السعر الآن: 499 ر.س (شامل الضريبة). متاح التقسيط عبر تابي وتمارا. مرجع التصريح: [رقم مطابق للوثيقة الرسمية]، وفترة العرض: [حسب التصريح]."`

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An automated Shopify/Salla AI compare-at-price script bulk-multiplies all current prices by `1.5x` and pastes that figure into the `Compare-at Price` (`السعر قبل الخصم`) field the night before White Friday.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Lock `Compare-at Price` to the immutable 30-day historical price snapshot stored in your ERP/warehouse log, and disable any plugin that calculates `Compare-at Price` as a formula of `Current_Price * 1.X`.
