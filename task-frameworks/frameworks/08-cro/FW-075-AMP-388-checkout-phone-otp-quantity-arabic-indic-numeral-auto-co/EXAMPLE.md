# End-to-End Worked Example & Failure Recovery — `FW-075` (`AMP-388`)

- **Framework**: Checkout Phone, OTP & Quantity Arabic-Indic Numeral (`٠١٢٣٤٥٦٧٨٩`) Auto-Conversion Checklist
- **العنوان بالعربية**: قائمة فحص وكود التحويل التلقائي للأرقام العربية-الهندية (`٠١٢٣٤٥٦٧٨٩`) في حقول الهاتف ورموز التحقق (`OTP`) بصفحة الدفع
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Riyadh & Cairo Healthcare Booking & Pharmacy Delivery App.
- **Problem**: Analytics showed a `28%` drop-off on the mobile phone & SMS OTP verification step among iOS users browsing the Arabic interface. Session replays revealed users typing `٠٥٠...` (or pasting their number from iOS Contacts with invisible `‪` marks) and getting blocked by `"يرجى إدخال رقم جوال صحيح"`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Deployed `attachMenaNumeralNormalizer()` + Server-Side Fallback**:
  - Client-side listener converts `٠-٩` to `0-9` and strips iOS BiDi invisible marks on `input`.
  - Backend API endpoint runs the exact same normalization before validating and hashing for CAPI (`AMP-067`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added Flexible Saudi/Egypt Prefix Acceptance**: Allowed users in KSA to enter `0551234567`, `551234567`, `966551234567`, or `+966 55 123 4567` (and in Egypt `010...`, `10...`, `+2010...`) and normalized all formats to E.164 automatically instead of forcing a rigid 9-digit mask.
2. **Added WebOTP (`autocomplete="one-time-code"`)**: Enabled 1-tap iOS/Android SMS OTP autofill.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Phone/OTP step validation error rate dropped from `28%` to `1.1%`, recovering thousands of blocked mobile checkouts.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A developer only normalizes Arabic-Indic digits on the frontend JS, but a user submitting via an in-app browser autofill bypasses the `input` event and hits the backend PHP/Node validator with `٠١٠...` or `‪`, causing a `422 Unprocessable Entity` error.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always run `toAsciiDigits()` on **BOTH the frontend `input` listener AND the backend API request body middleware** before running validation rules.
