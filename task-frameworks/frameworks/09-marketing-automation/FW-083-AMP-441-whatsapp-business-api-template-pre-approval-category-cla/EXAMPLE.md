# End-to-End Worked Example & Failure Recovery — `FW-083` (`AMP-441`)

- **Framework**: WhatsApp Business API Template Pre-Approval & Category Classification Checklist (`MARKETING` vs. `UTILITY`)
- **العنوان بالعربية**: قائمة فحص اعتماد قوالب `WhatsApp Business API` ومنع الرفض الآلي (تصنيف `Marketing` مقابل `Utility` وأمثلة المتغيرات `{{1}}`)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Submission**: Saudi E-Commerce Store submitting an Order Confirmation template under `UTILITY`.
- **Rejected Draft**:
  `"{{1}}، تم تأكيد طلبك {{2}} {{3}}! استخدم كود VIP10 لخصم 10% على طلبك القادم من هنا: https://bit.ly/3xyz — {{4}}"` (Submitted with empty variable sample fields).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **`lint_whatsapp_template()` Output (`4 Fatal Rejection Reasons Found`)**:
  1. `FAIL`: Starts with `{{1}}` and ends with `{{4}}` (bare variables at start and end).
  2. `FAIL`: Adjacent variables `{{2}} {{3}}` with no separating words.
  3. `FAIL`: Promotional text (`"استخدم كود VIP10 لخصم 10%"`) and `bit.ly` shortener inside a `UTILITY` template.
  4. `FAIL`: Missing sample values for `{{1}}..{{4}}`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Rewrote into Pure `UTILITY` Template with Fixed Wrapping Words**:
   `"أهلاً بك يا {{1}}، تم تأكيد طلبك رقم {{2}} بقيمة {{3}} ريال سعودي بنجاح. يمكنك متابعة حالة الشحنة عبر الرابط الرسمي للمتجر بالأسفل. شكراً لثقتك بنا."`
2. **Attached Realistic Arabic Sample Values**: `{{1}}: "أحمد"`, `{{2}}: "#ORD-99412"`, `{{3}}: "349.00"`, and replaced `bit.ly` with a dynamic button pointing to `https://store.sa/orders/{{1}}`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Template approved by Meta WhatsApp Manager in `< 2 minutes` under `UTILITY` pricing with `0` rejections.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A marketer submits a template with `{{1}}` and `{{3}}` (skipping `{{2}}` after editing a sentence); Meta's API rejects the payload with `Invalid parameter: variable parameters must be sequential`.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always run `lint_whatsapp_template()` before clicking Submit in WhatsApp Manager or Wati/Respond.io.
