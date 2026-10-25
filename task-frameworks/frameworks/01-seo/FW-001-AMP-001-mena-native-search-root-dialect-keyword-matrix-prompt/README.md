# `FW-001` — MENA Native Search Root & Dialect Keyword Matrix Prompt
## قالب هندسة الكلمات المفتاحية العربية حسب الجذر اللغوي واللهجة المحلية (مصر والخليج)

- **One-Sentence Promise (EN)**: Generate intent-grouped Arabic and bilingual keyword clusters from native Saudi, Emirati, and Egyptian search roots instead of zero-volume literal English translations.
- **الوعد التطبيقي في جملة واحدة (AR)**: توليد مجموعات كلمات مفتاحية عربية وثنائية اللغة مبنية على الجذور الصرفية ومصطلحات البحث الفعلية في السعودية والإمارات ومصر بدلاً من الترجمة الحرفية عديمة الجدوى.
- **Selected Artifact Type**: `PROMPT_TEMPLATE` *(Chosen because: Keyword ideation from English seed lists is a recurring generative task; a structured PROMPT_TEMPLATE with locked lexical-root rules, regional synonym tables, and output verification prevents literal calques at generation time.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-013`, `AMP-025`, `AMP-037`, `AMP-049`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-501`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when launching or localizing product, category, or service pages for Saudi Arabia (Salla/Zid/Shopify), UAE, or Egypt where seed product data is in English or MSA.
- **داعي الاستخدام (AR)**: يُستخدم عند إطلاق أو تعريب صفحات المنتجات أو الفئات أو الخدمات لأسواق السعودية (سلة/زد/شوبيفاي) أو الإمارات أو مصر عندما تكون بيانات المنتجات الأولية بالإنجليزية أو الفصحى.
- **Do NOT Use When**: Do not use for strictly English-only technical API documentation or developer-only SaaS products where 95%+ of local queries occur in English.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Product/Service Catalog Seed List (English or MSA names, SKU category, price tier in SAR/AED/EGP)
   - Target Market & City Tier (e.g., KSA Riyadh/Jeddah/Dammam vs. Egypt Cairo/Alexandria vs. UAE Dubai/Abu Dhabi)
   - Search Console or Marketplace Autocomplete Seed Export (at least 10 verified native queries)
   - Payment & Fulfilment Hooks relevant to commercial intent (e.g., Tabby/Tamara/Mada in KSA/UAE; COD/InstaPay/Fawry/valU in Egypt)
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
