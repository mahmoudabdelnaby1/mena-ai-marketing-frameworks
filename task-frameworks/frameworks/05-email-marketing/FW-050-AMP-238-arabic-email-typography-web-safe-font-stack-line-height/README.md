# `FW-050` — Arabic Email Typography, Web-Safe Font Stack & Line-Height Checklist (Preventing Tiny Times New Roman Fallback in Outlook)
## قائمة فحص خطوط البريد الإلكتروني العربية (`Font Stack`) وتباعد الأسطر لمنع الارتداد لخط `Times New Roman` غير المقروء في Outlook

- **One-Sentence Promise (EN)**: Configure Arabic HTML email font stacks, minimum pixel sizes (`>= 16px` body), and line-heights (`1.7–1.8`) so Windows Outlook, Gmail, and iOS Mail never fall back to cramped 12px Times New Roman.
- **الوعد التطبيقي في جملة واحدة (AR)**: ضبط سلسلة الخطوط البديلة (`Font Stack`) وحجم الخط (`16px` كحد أدنى) وتباعد الأسطر (`1.75`) في رسائل البريد العربية لمنع تحول النص في برنامج Outlook إلى خط `Times New Roman` الصغير غير المقروء.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: AI email builders default to Latin font stacks (`font-family: 'Inter', 'Helvetica Neue', Arial, sans-serif; font-size: 13px; line-height: 1.3;`). Because desktop Outlook ignores `@import` Google Fonts and Latin fonts lack Arabic glyphs, Outlook falls back to legacy `Times New Roman` at `13px`, rendering Arabic characters tiny and colliding; a typographic CHECKLIST + CSS snippet fixes readability across all clients.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-248`, `AMP-258`, `AMP-268`, `AMP-278`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use on every Arabic or bilingual HTML email template in Klaviyo, HubSpot, Mailchimp, Braze, or custom ESPs.
- **داعي الاستخدام (AR)**: تُستخدم في جميع قوالب البريد الإلكتروني العربية أو ثنائية اللغة على كافة منصات الإرسال.
- **Do NOT Use When**: Never set Arabic email body text smaller than `16px` or `line-height` smaller than `1.65`, and never use `letter-spacing` (`tracking > 0`) on Arabic text (positive `letter-spacing` breaks connected Arabic cursive ligatures!).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - HTML Email Template CSS styles (`font-family`, `font-size`, `line-height`, `letter-spacing`)
   - Brand Primary Arabic Web Font (e.g., `Tajawal`, `Cairo`, `IBM Plex Sans Arabic`, `Almarai`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `CHECKLIST` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `CHECKLIST` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
