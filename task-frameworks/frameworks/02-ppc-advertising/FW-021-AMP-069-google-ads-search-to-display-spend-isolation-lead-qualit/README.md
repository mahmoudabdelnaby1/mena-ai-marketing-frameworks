# `FW-021` — Google Ads Search Campaign Channel Allocation & Lead Quality Review
## مراجعة توزيع القنوات وجودة العملاء المحتملين في حملات البحث على Google Ads

- **One-Sentence Promise (EN)**: Review Search campaign channel settings, allocation controls, and lead-quality signals as Google rolls out channel-prioritization changes.
- **الوعد التطبيقي في جملة واحدة (AR)**: مراجعة توزيع القنوات وجودة العملاء المحتملين باستخدام إعدادات الحساب الحالية وبيانات العملاء المؤهلين، مع إعادة التحقق من التغييرات التي تطرحها Google تدريجياً.
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: Google is rolling out channel-prioritization and allocation changes. Their availability and behavior can vary by account and campaign, so a decision aid should help teams inspect current settings, campaign goals, and qualified outcomes before choosing a configuration.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-079`, `AMP-089`, `AMP-099`, `AMP-109`, `AMP-119`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-509`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when auditing or launching Google Search campaigns in KSA, UAE, or Egypt—especially for lead generation (real estate, clinics, B2B, education, automotive).
- **داعي الاستخدام (AR)**: تُستخدم عند تدقيق أو إطلاق حملات بحث جوجل (`Google Search`) في السعودية أو الإمارات أو مصر، خاصة في قطاعات توليد العملاء المحتملين (العقارات، العيادات، الشركات B2B، التعليم).
- **Do NOT Use When**: Review network and channel settings against the campaign objective, current account controls, and qualified outcome data; avoid universal setting rules.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Google Ads Campaign Settings -> `Networks` (`الشبكات`) status across all active Search campaigns
   - Search Campaign Spend Breakdown by Network (`Search` vs. `Search Partners` vs. `Display Expansion`)
   - Primary Conversion Action configuration (`Page View / Raw Form Submit` vs. `Qualified Lead / CRM SQL`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `DECISION_AID` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `DECISION_AID` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
