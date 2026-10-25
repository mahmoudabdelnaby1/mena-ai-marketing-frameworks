# `FW-029` — Saudi Marketing Team Planning & Nitaqat Verification Decision Aid
## أداة تخطيط فريق التسويق والتحقق من متطلبات نطاقات في السعودية

- **One-Sentence Promise (EN)**: Design AI-augmented marketing team structures, hiring budgets, and agency hybrid models in Saudi Arabia that comply with current Saudi labor-localization requirements, which must be checked against the establishment’s activity, size, workforce, and applicable official guidance.
- **الوعد التطبيقي في جملة واحدة (AR)**: تصميم هياكل فرق التسويق وميزانيات التوظيف ونماذج عمل الوكالات في المملكة العربية السعودية بما يلتزم بقرار وزارة الموارد البشرية والتنمية الاجتماعية بتوطين مهن التسويق بنسبة النسبة المحسوبة وفق الأداة الرسمية الحالية (الساري منذ 19 أبريل 2026).
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: Generic AI operating-plan prompts recommend hiring cheap offshore/non-Saudi in-house marketing headcount in Riyadh without knowing that effective 19 April 2026, Saudi localization requirements vary by activity and workforce and should be calculated using current official MHRSD/Qiwa tools; a DECISION_AID aligns headcount math, salary floors, and AI workflow automation.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-137`, `AMP-147`, `AMP-157`, `AMP-167`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when building a marketing hiring plan, agency staffing model, or AI automation roadmap for any company registered in Saudi Arabia.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد خطة توظيف فريق التسويق أو هيكلة الوكالة الإعلانية أو أتمتة المهام لأي منشأة مسجلة في المملكة العربية السعودية.
- **Do NOT Use When**: Do not misclassify marketing staff under unrelated visa professions (`مهن غير مطابقة للمسمى الفعلي`) to evade the النسبة المحسوبة وفق الأداة الرسمية الحالية marketing localization quota—this violates MHRSD / Qiwa labor inspection rules.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Planned total in-house marketing headcount in the Saudi entity (`Qiwa / GOSI` establishment record)
   - Covered Marketing Occupation Codes (Marketing Manager, Advertising Specialist, PR Specialist, Market Research, Graphic/Content roles per MHRSD procedural guide)
   - Minimum qualifying salary floor (`SAR 5,500` GOSI-registered wage to count as 1 full Saudi unit in localized marketing professions)
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
