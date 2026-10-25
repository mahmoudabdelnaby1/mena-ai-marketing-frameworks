# `FW-083` — WhatsApp Business API Template Pre-Approval & Category Classification Checklist (`MARKETING` vs. `UTILITY`)
## قائمة فحص اعتماد قوالب `WhatsApp Business API` ومنع الرفض الآلي (تصنيف `Marketing` مقابل `Utility` وأمثلة المتغيرات `{{1}}`)

- **One-Sentence Promise (EN)**: Prevent Meta from rejecting ~1 in 3 WhatsApp Business API templates by choosing the right category (`MARKETING` vs. `UTILITY`), embedding mandatory realistic Arabic sample values for every `{{1}}` variable, and never starting or ending a template with a bare variable.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع الرفض التلقائي لثلث قوالب `WhatsApp Business API` عبر مطابقة التصنيف الصحيح (`Marketing` مقابل `Utility`)، وإرفاق أمثلة حقيقية لكل متغير `{{1}}`، وعدم بدء أو إنهاء القالب بمتغير مجرد.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: AsisteClick and Tenreply 2026 audits show ~33% of WhatsApp API templates are rejected on submission because marketers (a) submit promotional/upsell copy under the cheaper `UTILITY` category, (b) omit the mandatory `example` payload for `{{1}}` variables, or (c) place `{{1}}` at the very start/end of a line or adjacent to `{{2}}`; a pre-submission CHECKLIST + validator guarantees first-pass approval.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-451`, `AMP-461`, `AMP-471`, `AMP-481`, `AMP-491`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-541`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before submitting any Arabic or English message template in Meta WhatsApp Manager, Wati, Respond.io, Infobip, Unifonic, or Twilio.
- **داعي الاستخدام (AR)**: تُستخدم قبل إرسال أي قالب رسالة (`Message Template`) للمراجعة في مدير أعمال واتساب (`Meta WhatsApp Manager`) أو منصات الربط.
- **Do NOT Use When**: Never submit a template containing a discount code, cross-sell offer, cart recovery nudge, or win-back message under the `UTILITY` category—Meta's classifier will reject it or force-reclassify it to `MARKETING`.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Draft Arabic/English WhatsApp Template Body, Header, Footer, and Buttons
   - Intended Template Category (`MARKETING`, `UTILITY`, or `AUTHENTICATION`)
   - Sample Realistic Values for every numbered placeholder (`{{1}}`, `{{2}}`, `{{3}}`)
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
