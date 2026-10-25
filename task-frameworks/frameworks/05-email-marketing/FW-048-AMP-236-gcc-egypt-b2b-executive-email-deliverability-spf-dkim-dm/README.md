# `FW-048` — GCC & Egypt B2B Executive Email Deliverability (SPF/DKIM/DMARC) & Bilingual Conciseness Checklist
## قائمة فحص موثوقية نطاق البريد (`SPF/DKIM/DMARC`) وهيكلة رسائل الشركات (`B2B`) ثنائية اللغة في الخليج ومصر

- **One-Sentence Promise (EN)**: Authenticate sending domains (`SPF`, `DKIM`, `DMARC`, `List-Unsubscribe`) and format B2B executive emails under 90 words per language block so messages land in Primary corporate inboxes in Riyadh, Dubai, Doha, and Cairo.
- **الوعد التطبيقي في جملة واحدة (AR)**: توثيق نطاقات الإرسال البريدي (`SPF`, `DKIM`, `DMARC`, `List-Unsubscribe`) وصياغة رسائل الشركات التنفيذية (`B2B`) في أقل من 90 كلمة لكل لغة لضمان وصولها لصندوق الوارد الرئيسي في الرياض ودبي والدوحة والقاهرة.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: B2B AI email tools generate 350-word walls of text and send them from unauthenticated root domains lacking DMARC/DKIM alignment or compliant opt-in (`AMP-232`); a combined DNS authentication + 90-word bilingual executive formatting CHECKLIST fixes both technical deliverability and executive scan rates.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-246`, `AMP-256`, `AMP-266`, `AMP-276`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-526`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before launching B2B lifecycle, event invitation, webinar follow-up, or account-based marketing emails to corporate domains (`.sa`, `.ae`, `.qa`, `.eg`, `.com`) in MENA.
- **داعي الاستخدام (AR)**: تُستخدم قبل إرسال رسائل الشركات (`B2B`) أو دعوات المؤتمرات أو متابعات المبيعات للنطاقات المؤسسية في الخليج ومصر.
- **Do NOT Use When**: Do not send bulk marketing sequences to unconsented scraped lists (`AMP-232`) or from your primary corporate root domain without subdomain isolation.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Sending Domain DNS records (`TXT` records for `SPF`, `DKIM`, `DMARC`)
   - Opt-in B2B Contact Segment (`Role`, `City`, `Language Preference: AR / EN / Bilingual`)
   - Single concrete value hook + 1 low-friction CTA
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
