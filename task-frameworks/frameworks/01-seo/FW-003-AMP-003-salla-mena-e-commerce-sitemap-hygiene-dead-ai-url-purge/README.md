# `FW-003` — Salla & MENA E-Commerce Sitemap Hygiene & Dead-AI-URL Purge Checklist
## قائمة فحص وتطهير خرائط المواقع (`sitemap.xml`) في متاجر سلة والتجارة الإلكترونية من الروابط المعطوبة والمحذوفة

- **One-Sentence Promise (EN)**: Audit and clean `sitemap.xml` files so Googlebot stops wasting up to 60% of crawl budget on 302/301 redirected or 410 Gone AI-generated product URLs.
- **الوعد التطبيقي في جملة واحدة (AR)**: تدقيق وتنظيف ملفات `sitemap.xml` لمنع استنزاف 60% من ميزانية الزحف (Crawl Budget) في جوجل على روابط منتجات محذوفة أو محولة (`302/301/410`).
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Sitemap rot after bulk AI catalog generation or seasonal SKU archiving is a structural technical SEO failure (documented in VOCTOS's Oct 2026 Salla audit where 88 of 146 sampled sitemap URLs redirected or returned 410); a deterministic CHECKLIST with a verification script resolves it reliably.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-015`, `AMP-027`, `AMP-039`, `AMP-051`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use after bulk-importing AI-generated product listings, hiding seasonal SKUs (Ramadan/White Friday), or diagnosing 'Page with redirect' and 'Not found (404/410)' spikes in Google Search Console.
- **داعي الاستخدام (AR)**: تُستخدم بعد الاستيراد الجماعي للمنتجات المولدة بالذكاء الاصطناعي، أو إخفاء منتجات المواسم (رمضان/الجمعة البيضاء)، أو عند ظهور تنبيهات التحويل (`302/410`) في Google Search Console.
- **Do NOT Use When**: Do not delete URLs of temporarily out-of-stock evergreen products that will restock within 30 days—keep them `200 OK` with an in-stock notification capture instead of unpublishing.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Live store `sitemap.xml` URL (e.g., `https://store.com/sitemap.xml`)
   - Google Search Console Page Indexing export (`Excluded by redirect`, `404`, `410`, `Crawled - currently not indexed`)
   - Catalog export of Hidden / Draft / Deleted SKUs from Salla, Zid, Shopify, or WooCommerce
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
