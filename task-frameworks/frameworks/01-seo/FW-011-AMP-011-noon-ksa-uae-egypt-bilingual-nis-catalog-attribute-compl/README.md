# `FW-011` — Noon KSA, UAE & Egypt Bilingual NIS Catalog & Attribute Completeness Playbook
## دليل التشغيل الثنائي اللغة لكتالوجات نون (`Noon KSA / UAE / Egypt`) لضمان الظهور في الواجهة العربية

- **One-Sentence Promise (EN)**: Populate Noon Importer Sheet (NIS) feeds with complete Arabic + English attributes so listings never vanish from the Arabic Noon storefront.
- **الوعد التطبيقي في جملة واحدة (AR)**: تعبئة قوالب رفع المنتجات في نون (`NIS`) باللغتين العربية والإنجليزية معاً لضمان عدم اختفاء المنتجات من واجهة المتجر العربية في السعودية والإمارات ومصر.
- **Selected Artifact Type**: `PLAYBOOK` *(Chosen because: Noon Partner Help Center makes English mandatory and Arabic 'optional' in NIS sheets, yet explicitly warns that English-only products can be hidden from the Arabic site (and does not machine-translate seller copy automatically); an operational PLAYBOOK prevents accidental invisibility to Arabic-browsing shoppers.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-023`, `AMP-035`, `AMP-047`, `AMP-059`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-503`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever onboarding or updating catalog feeds on Noon (`noon.com` KSA, UAE, or Egypt) via Noon Seller Lab.
- **داعي الاستخدام (AR)**: يُستخدم عند رفع أو تحديث كتالوجات المنتجات على منصة نون (`Noon Seller Lab`) في السعودية أو الإمارات أو مصر.
- **Do NOT Use When**: Do not claim exact percentage weights for Noon's internal organic ranking algorithm (`AMP-548` — Noon publishes eligibility and ad relevance factors, not organic rank weights).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Noon Category-Specific NIS Template (`.xlsx` / `.tsv`) downloaded from Noon Seller Lab
   - English Master SKU Data (Brand, Title, 5 Feature Bullets, Technical Specifications)
   - Verified Arabic Keyword & Attribute Glossary (`AMP-001` & `AMP-002`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `PLAYBOOK` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `PLAYBOOK` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
