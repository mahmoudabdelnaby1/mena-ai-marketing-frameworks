# `FW-002` — Arabic Orthographic Normalization Checklist (Hamza, Taa Marbuta, Alef Maqsura & Indic Digits)
## قائمة فحص تطبيع الحروف والأرقام العربية في البحث الداخلي والـ SEO (الهمزات، التاء المربوطة، الألف المقصورة، والأرقام الهندية)

- **One-Sentence Promise (EN)**: Eliminate false '0 results found' pages and missed organic matches caused by unnormalized Arabic letter variants (`أ/إ/آ/ا`, `ة/ه`, `ى/ي`) and Arabic-Indic numerals (`٠-٩`).
- **الوعد التطبيقي في جملة واحدة (AR)**: القضاء على صفحات «لا توجد نتائج» وفقدان الزيارات الناتجة عن اختلاف كتابة الهمزات (`أ/إ/آ/ا`) والتاء المربوطة (`ة/ه`) والألف المقصورة (`ى/ي`) والأرقام الهندية (`٠-٩`).
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Orthographic normalization is a deterministic technical & content QA task across site search, product feeds, and on-page copy; a verification CHECKLIST with copy-ready regex/JS normalization rules gives developers and SEO leads an immediate fix.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-014`, `AMP-026`, `AMP-038`, `AMP-050`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when configuring internal storefront search (Salla, Zid, Shopify, WooCommerce, custom Algolia/Elasticsearch) or auditing AI-generated Arabic product descriptions and tags.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد محرك البحث الداخلي للمتجر (سلة، زد، شوبيفاي، ووكومرس، أو Algolia/Elasticsearch) أو تدقيق أوصاف ووسوم المنتجات المولدة بالذكاء الاصطناعي.
- **Do NOT Use When**: Do not strip Hamzas or Taa Marbuta from visible H1 headings or formal brand copy—normalization happens in the search index, backend tags, and query parser, while visible prose stays grammatically correct.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Top 100 'Zero-Result' internal site search queries from GA4 (`view_search_results`) or platform analytics
   - Storefront search engine configuration or theme JS / backend search pipeline access
   - Product tag / synonym dictionary export (CSV/JSON)
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
