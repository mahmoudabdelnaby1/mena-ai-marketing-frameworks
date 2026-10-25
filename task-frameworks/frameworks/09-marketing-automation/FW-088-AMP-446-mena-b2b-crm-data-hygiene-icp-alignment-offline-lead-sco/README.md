# `FW-088` — MENA B2B CRM Data Hygiene, ICP Alignment & Offline Lead-Scoring Feedback Framework
## الإطار التشغيلي لتنظيف بيانات `CRM` ومواءمة معايير العميل المثالي (`ICP`) بين التسويق والمبيعات في قطاع الأعمال (`B2B`)

- **One-Sentence Promise (EN)**: Clean duplicate/malformed Arabic-English CRM records, lock a shared Sales-Marketing Ideal Customer Profile (`ICP`), and feed back SQL status to Google/Meta/LinkedIn so AI lead-generation automation scales revenue instead of amplifying dirty data.
- **الوعد التطبيقي في جملة واحدة (AR)**: تنظيف سجلات `CRM` المكررة والمشوهة (بين العربية والإنجليزية)، وتوحيد تعريف «العميل المؤهل `MQL/SQL`» بين التسويق والمبيعات، وتغذية المنصات الإعلانية بالصفقات الحقيقية لمنع أتمتة الفوضى.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Founderz's 2026 B2B AI study and 23HubLab's Egypt/MENA lead-generation benchmarks demonstrate that deploying AI lead-scoring and outreach automation on top of a dirty CRM (where the same company is entered 4 times as `'شركة المراعي'`, `'Almarai'`, `'المراعي'`, and personal `@gmail.com` leads from job-seekers mix with C-suite buyers) amplifies errors at scale and floods sales reps in Riyadh, Dubai, and Cairo with junk leads; a 4-stage OPERATING_FRAMEWORK fixes data hygiene and ICP alignment first.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-456`, `AMP-466`, `AMP-476`, `AMP-486`, `AMP-496`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before deploying AI lead scoring, automated SDR sequences, or value-based lead bidding (`AMP-069`) for B2B, SaaS, real estate, industrial, or healthcare enterprises in MENA.
- **داعي الاستخدام (AR)**: تُستخدم قبل تشغيل أنظمة تقييم العملاء المحتملين بالذكاء الاصطناعي (`AI Lead Scoring`) أو أتمتة المبيعات في قطاعات الشركات (`B2B`) والعقارات والحلول التقنية.
- **Do NOT Use When**: Never automate outbound B2B emails/WhatsApp messages from CRM triggers until duplicate company records, Arabic-Indic phone numbers (`AMP-388`), and non-ICP disqualifiers (`Job Seeker / Student / Vendor`) are scrubbed.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - CRM Contact & Company Export (`HubSpot`, `Salesforce`, `Zoho`, `Pipedrive`, `Dynamics 365`)
   - Joint Sales + Marketing Signed ICP Charter (`Minimum Company Size, Commercial Registration / CR presence, Target Geography, Budget Floor`)
   - Google Ads `GCLID` / Meta `Lead_ID` Offline Conversion Import integration
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `OPERATING_FRAMEWORK` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `OPERATING_FRAMEWORK` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
