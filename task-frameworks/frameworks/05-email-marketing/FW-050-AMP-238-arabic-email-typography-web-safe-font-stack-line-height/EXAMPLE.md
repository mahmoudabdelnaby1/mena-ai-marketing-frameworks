# End-to-End Worked Example & Failure Recovery — `FW-050` (`AMP-238`)

- **Framework**: Arabic Email Typography, Web-Safe Font Stack & Line-Height Checklist (Preventing Tiny Times New Roman Fallback in Outlook)
- **العنوان بالعربية**: قائمة فحص خطوط البريد الإلكتروني العربية (`Font Stack`) وتباعد الأسطر لمنع الارتداد لخط `Times New Roman` غير المقروء في Outlook
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Template**: AI-generated HubSpot Newsletter for a Riyadh & Cairo FinTech platform.
- **Defects Found**:
  1. CTA button had `letter-spacing: 1.5px; text-transform: uppercase;`, tearing the button text `"افتح حسابك الآن"` into disconnected letters on Gmail.
  2. Body text used `font-family: 'Montserrat', sans-serif; font-size: 13px;`, rendering in tiny `13px Times New Roman` on Windows Outlook across corporate banking clients.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Applied Typographic Fix**:
  - Updated inline style on all `<td>`, `<p>`, and `<a>` elements to:
    `font-family: 'IBM Plex Sans Arabic', 'Segoe UI', Tahoma, Arial, sans-serif; font-size: 16px; line-height: 1.75; letter-spacing: 0px; font-style: normal;`
  - Added `<!--[if mso]>` conditional block forcing `'Segoe UI', Tahoma, Arial, sans-serif !important` on Windows Outlook.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Scannability Check**: Audited all subheadings (`<h2>`) and CTA buttons to ensure `letter-spacing: 0` and removed all `<i>`/`<em>` tags around Arabic text, replacing them with `<strong>` (`font-weight: 700`).
2. **Verified Outlook 365 Desktop Rendering**: Confirmed clean `16px Segoe UI` rendering with generous `1.75` line spacing.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Master HubSpot/Klaviyo Arabic typography CSS snippet deployed across all templates with zero `Times New Roman` fallbacks and zero broken cursive ligatures.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A designer uses an English luxury template where all `<h2>` headings and buttons inherit `letter-spacing: 2px` from the global stylesheet; every Arabic heading renders with ugly gaps between connected letters (`م ج م و ع ة`).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Add `letter-spacing: 0px !important; font-style: normal !important;` to your global `[dir="rtl"]` and inline Arabic style rules.
