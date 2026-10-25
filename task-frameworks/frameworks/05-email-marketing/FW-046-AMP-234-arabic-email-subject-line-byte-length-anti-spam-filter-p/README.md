# `FW-046` — Arabic Email Subject-Line Byte-Length & Anti-Spam Filter Prompt Template
## قالب صياغة عناوين رسائل البريد الإلكتروني العربية (ضبط طول البايتات `UTF-8` وتجنب فلاتر السبام والوعود المضللة)

- **One-Sentence Promise (EN)**: Write high-open-rate Arabic email subject lines and preheaders (`<= 38` Arabic chars) that never clip on iOS/Android mobile inboxes or trigger Gmail/Outlook spam filters.
- **الوعد التطبيقي في جملة واحدة (AR)**: كتابة عناوين رسائل بريد إلكتروني (`Subject Lines`) ونصوص معاينة (`Preheaders`) عربية موجزة (`38 حرفاً كحد أقصى`) لا تنقطع في شاشات الجوال ولا تستثير فلاتر البريد المزعج (`Spam`).
- **Selected Artifact Type**: `PROMPT_TEMPLATE` *(Chosen because: Unguided LLMs translate 60-character English subject lines into 65–80 character Arabic sentences filled with exclamation marks, emojis, and spam-triggering words (`'مجاناً 100%!!! اربح الآن'`), which both exceed RFC 2047 MIME UTF-8 header folding limits and get clipped at ~38–42 characters on mobile Gmail/iOS Mail; a constrained PROMPT_TEMPLATE fixes both length and deliverability.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-244`, `AMP-254`, `AMP-264`, `AMP-274`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-524`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when generating Arabic or bilingual email subject lines (`Subject`) and preview texts (`Preheader`) for newsletters, cart recovery, or promotional campaigns.
- **داعي الاستخدام (AR)**: تُستخدم عند صياغة عناوين الرسائل البريدية (`Subject Line`) ونص المعاينة (`Preheader`) للحملات والنشرات البريدية وسلاسل السلات المتروكة.
- **Do NOT Use When**: Do not put more than 1 emoji in an Arabic subject line, never use `RE:` / `رد:` or `FWD:` on a marketing email to fake a personal reply, and never exceed 42 Arabic characters.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Core Email Offer / Topic
   - Target Dialect/Register (`Saudi White Khaleeji`, `Egyptian Polite Ammiya`, or `Modern White MSA`)
   - Mandatory Prefix Requirement (e.g., if sending in UAE under TDRA promotional rules where applicable)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `PROMPT_TEMPLATE` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `PROMPT_TEMPLATE` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
