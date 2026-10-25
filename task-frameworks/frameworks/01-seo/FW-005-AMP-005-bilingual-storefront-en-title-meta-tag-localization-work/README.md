# `FW-005` — Bilingual Storefront `/en/` Title & Meta Tag Localization Workflow (Salla & Zid)
## مسار عمل تعريب وترجمة وسوم العناوين (`<title>`) والميتا للصفحات الإنجليزية في متاجر سلة وزد

- **One-Sentence Promise (EN)**: Eliminate untranslated Arabic-script `<title>` tags on `/en/` storefront pages through a structured bilingual catalog export-translate-validate workflow.
- **الوعد التطبيقي في جملة واحدة (AR)**: القضاء على بقاء وسوم `<title>` باللغة العربية داخل الصفحات الإنجليزية (`/en/`) عبر مسار عمل منظم لتصدير وترجمة وتدقيق حقول الـ SEO لكل لغة.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Because 4 of 6 Salla stores and 4 of 5 Zid stores with English enabled served Arabic-script `<title>` tags on `/en/` URLs in the Oct 2026 audit, teams need an end-to-end OPERATING_FRAMEWORK connecting catalog export, structured LLM JSON localization, and post-import HTML verification.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-017`, `AMP-029`, `AMP-041`, `AMP-053`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when managing bilingual (`/ar/` + `/en/`) product catalogs on Salla, Zid, Shopify, or WooCommerce in KSA, UAE, Qatar, Kuwait, or Egypt.
- **داعي الاستخدام (AR)**: يُستخدم عند إدارة كتالوجات منتجات ثنائية اللغة (`/ar/` و`/en/`) على سلة أو زد أو شوبيفاي أو ووكومرس في الخليج ومصر.
- **Do NOT Use When**: Do not run automated title updates without locking brand names, model numbers, and weight/volume units (`ml`, `g`, `SAR`, `AED`, `EGP`).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Catalog SEO CSV/Excel export containing both `title_ar`, `seo_title_ar` and `title_en`, `seo_title_en` columns
   - Brand Glossary (official English spelling of Arabic brand names, e.g., `عبدالصمد القرشي` -> `Abdul Samad Al Qurashi`)
   - Target character caps (`50–60` characters for Google SERP `<title>`, `<=75` chars if syncing to Amazon.sa/ae)
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
