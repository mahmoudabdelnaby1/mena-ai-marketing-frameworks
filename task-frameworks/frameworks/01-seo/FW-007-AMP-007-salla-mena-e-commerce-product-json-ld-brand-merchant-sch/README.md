# `FW-007` — Salla & MENA E-Commerce Product JSON-LD `brand` & Merchant Schema Injection Checklist
## قائمة فحص وحقن خاصية العلامة التجارية (`brand`) والبيانات المهيكلة `Product JSON-LD` في متاجر سلة والمنطقة

- **One-Sentence Promise (EN)**: Patch missing `brand`, `sku`, `gtin`, and `priceValidUntil` properties in Salla and regional e-commerce `Product` JSON-LD so pages qualify for full Google Merchant & AI Search rich snippets.
- **الوعد التطبيقي في جملة واحدة (AR)**: استكمال حقل العلامة التجارية (`brand`) ورموز `sku/gtin` في البيانات المهيكلة `Product JSON-LD` لمتاجر سلة والمنطقة لضمان التوافق الكامل مع النتائج الغنية في جوجل ومحركات الذكاء الاصطناعي.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: VOCTOS's Oct 2026 audit found 0 of 10 Salla stores included the `brand` property in their default `Product` JSON-LD (whereas 9 of 10 Zid stores included it); a technical CHECKLIST with a drop-in JSON-LD enrichment snippet fixes Google Search Console Merchant Listing warnings immediately.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-019`, `AMP-031`, `AMP-043`, `AMP-055`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when Google Search Console shows 'Missing field "brand"' under Merchant Listings / Product snippets on Salla, WooCommerce, or Shopify stores.
- **داعي الاستخدام (AR)**: تُستخدم عند ظهور تنبيه «الحقل المفقود brand» في تقارير المنتجات داخل Google Search Console لمتاجر سلة أو ووكومرس أو شوبيفاي.
- **Do NOT Use When**: Do not inject fabricated `aggregateRating` or fake review counts into JSON-LD (`AMP-392`)—Google issues manual actions for deceptive structured data.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Live product URL and Google Rich Results Test output
   - Verified Brand Name (`Brand` object name in Arabic/English)
   - Product `sku`, `gtin13`/`mpn` (if applicable), and currency (`SAR`, `AED`, `EGP`)
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
