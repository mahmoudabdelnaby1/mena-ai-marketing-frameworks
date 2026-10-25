# `FW-075` — Checkout Phone, OTP & Quantity Arabic-Indic Numeral (`٠١٢٣٤٥٦٧٨٩`) Auto-Conversion Checklist
## قائمة فحص وكود التحويل التلقائي للأرقام العربية-الهندية (`٠١٢٣٤٥٦٧٨٩`) في حقول الهاتف ورموز التحقق (`OTP`) بصفحة الدفع

- **One-Sentence Promise (EN)**: Auto-convert Arabic-Indic (`٠-٩`) and Eastern Arabic (`۰-۹`) digits into standard ASCII (`0-9`) on every phone, OTP, postal code, and quantity input field so mobile shoppers with Arabic keyboards are never blocked by validation errors.
- **الوعد التطبيقي في جملة واحدة (AR)**: التحويل التلقائي اللحظي للأرقام الهندية (`٠١٢٣٤٥٦٧٨٩`) إلى الأرقام القياسية (`0123456789`) في حقول رقم الجوال ورمز التحقق (`OTP`) والكمية لمنع رفض الطلبات للمستخدمين الذين يكتبون بلوحة المفاتيح العربية.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Millions of iOS and Android users in KSA, Egypt, and the GCC have their phone keyboard set to Arabic, which outputs Unicode Arabic-Indic digits (`٠–٩`: `٠٥٥١٢٣٤٥٦٧` or `٠١٠١٢٣٤٥٦٧٨`); Western regex validators (`/^[0-9]{10,11}$/`) reject `٠٥٥...` as 'Invalid Phone Number (`رقم الجوال غير صحيح`)' without telling the user why, causing instant checkout abandonment; a 10-line JS auto-normalizer + CHECKLIST eliminates this friction.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-398`, `AMP-408`, `AMP-418`, `AMP-428`, `AMP-438`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-538`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use on every checkout form, WhatsApp lead capture popup, OTP verification modal, and coupon/quantity input across MENA websites and apps.
- **داعي الاستخدام (AR)**: تُستخدم في جميع نماذج الدفع والتسجيل ونوافذ التحقق (`OTP`) وحقول الكمية وأكواد الخصم في المواقع والتطبيقات العربية.
- **Do NOT Use When**: Never display an error message saying `'Please enter English numbers only'`—convert the digits silently in the background on `input` so the user never sees an error!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Checkout / Lead Form HTML `<input>` selectors (`type="tel"`, `name="phone"`, `name="otp"`, `name="quantity"`)
   - Country Mobile Regex Rules (`KSA: 05XXXXXXXX / +9665XXXXXXXX`, `Egypt: 01[0125]XXXXXXXX`, `UAE: 05XXXXXXXX`)
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
