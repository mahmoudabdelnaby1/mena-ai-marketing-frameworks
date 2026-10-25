# End-to-End Worked Example & Failure Recovery — `FW-043` (`AMP-231`)

- **Framework**: Arabic HTML Email `dir='rtl'` & Unicode `<bdi>` Isolation Rendering Checklist (Gmail, Outlook & Apple Mail)
- **العنوان بالعربية**: قائمة فحص وقالب برمجة رسائل البريد العربية (`dir='rtl'` وعزل `<bdi>`) لمنع تشوه المحاذاة وانعكاس الأرقام في Gmail وOutlook
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **ESP**: Klaviyo Abandoned Cart Flow for a Saudi & UAE Perfume Store.
- **Broken AI HTML Output**: Used a standard LTR Klaviyo drag-and-drop block without `dir="rtl"` or `<bdi>`. In Gmail and Outlook, the line `"استخدم كود خصم VIP25 للحصول على خصم 25% والاتصال على +966 50 000 0000"` rendered flushed left as `"0000 000 50 966+ %25 VIP25..."` with the `+` sign and `%` sign detached and reversed.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Applied Master RTL Wrapper + `<bdi>` Isolation**:
  - Wrapped `VIP25`, `25%`, `299.00 SAR`, and `+966 50 000 0000` in `<bdi style="direction:ltr; unicode-bidi:isolate;">` inside `<td dir="rtl" align="right">`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Outlook Desktop VML Button Check**: Added `direction:rtl;` inside the CTA button table cell so the left-pointing arrow (`← أكملي طلبك الآن`) points in the natural RTL reading direction (`AMP-389`).
2. **Tested Across 4 Clients**: Verified rendering on Gmail iOS, Gmail Web, Apple Mail, and Outlook 365 Desktop (Windows).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Production Klaviyo HTML template passing 100% RTL alignment and BiDi number/code isolation across Gmail, Outlook, and Apple Mail.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A customer registers their first name in English (`"Sarah"`) on an Arabic store; in the welcome email `'مرحباً Sarah، شكراً لتسجيلك!'`, the Arabic comma `،` jumps to the right of `Sarah` because an unisolated Latin token at the start of an RTL line flips adjacent neutral punctuation.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always wrap `{{ first_name }}` in `<bdi>{{ first_name }}</bdi>&rlm;` (followed by the Right-to-Left Mark entity `&rlm;`) whenever a merge tag can contain either Arabic or Latin script.
