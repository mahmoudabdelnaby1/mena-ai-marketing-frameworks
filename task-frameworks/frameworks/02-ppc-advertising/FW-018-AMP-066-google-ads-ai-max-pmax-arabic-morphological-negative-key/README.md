# `FW-018` — Google Ads AI Max & PMax Arabic Morphological Negative Keyword Generator Prompt
## قالب توليد قوائم الكلمات السلبية الصرفية واللهجية لحملات Google Ads AI Max وPerformance Max بالعربية

- **One-Sentence Promise (EN)**: Generate comprehensive Arabic negative keyword lists covering attached prefixes (`و، ف، ب، ل، ال`), Hamza/Taa variants, and regional freebie/job slang (`بلاش، مجانا، وظائف، مستعمل`) that Google's broad matching fails to block automatically.
- **الوعد التطبيقي في جملة واحدة (AR)**: توليد قوائم الكلمات المفتاحية السلبية الشاملة للصيغ الصرفية العربية (البوادئ المتصلة `و، ف، ب، ل، ال`، وتغيرات الهمزات، ومصطلحات المجاني والوظائف والمستعمل باللهجات) التي لا يحظرها جوجل تلقائياً.
- **Selected Artifact Type**: `PROMPT_TEMPLATE` *(Chosen because: Unlike positive broad match, Google Ads negative keywords do NOT automatically expand across Arabic morphological prefixes (`بالمجان`, `ومجانا`, `للبيع مستعمل`) or regional dialect synonyms (`بلاش`, `حراج`, `اوليكس`); a specialized PROMPT_TEMPLATE generates the exact morphological matrix ready to paste into Negative Keyword Lists.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-076`, `AMP-086`, `AMP-096`, `AMP-106`, `AMP-116`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever running Google Search (`Broad Match` / `AI Max for Search`) or `Performance Max` campaigns in Arabic across KSA, UAE, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند تشغيل حملات بحث جوجل (`Broad Match` أو `AI Max`) أو حملات `Performance Max` باللغة العربية في السعودية أو الإمارات أو مصر.
- **Do NOT Use When**: Do not add broad single-word negatives that overlap with your core product noun (e.g., never add `عروض` or `سعر` as negatives on an e-commerce account).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Core commercial category (e.g., B2B SaaS, Private Clinic, Luxury Real Estate, New Electronics E-Commerce)
   - Non-converting intent categories to block (e.g., `Free/Pirated`, `Second-hand/Used`, `Jobs/Careers`, `DIY/Repair`, `Student PDF/Research`)
   - Recent Google Ads Search Terms report (`تقرير عبارات البحث`) export
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
