# `FW-020` — Snapchat Dynamic Product Ads (DPA) Gulf & Egypt Catalog Feed Validator Checklist
## قائمة فحص وتدقيق كتالوجات إعلانات المنتجات الديناميكية في سناب شات (`Snapchat DPA`) لأسواق الخليج ومصر

- **One-Sentence Promise (EN)**: Format Snapchat product catalog feeds with mandatory 3-letter ISO currency codes (`199.00 SAR`, `199.00 AED`, `950.00 EGP`) and matching pixel `item_ids` so Snap Dynamic Ads never fail feed ingestion.
- **الوعد التطبيقي في جملة واحدة (AR)**: تنسيق ملفات كتالوج المنتجات في سناب شات برموز العملات القياسية الثلاثية (`SAR`، `AED`، `EGP`) ومطابقة معرفات `item_ids` مع البكسل لمنع رفض الكتالوج أو تعطل الاستهداف الديناميكي.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Snapchat's catalog validator rejects bare non-USD numbers (`199` or `١٩٩ ر.س`) and breaks dynamic retargeting when Snap Pixel `item_ids` pass variant IDs while the catalog uses parent SKU IDs; a deterministic CHECKLIST with a feed scrubber prevents broken Gulf campaigns.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-078`, `AMP-088`, `AMP-098`, `AMP-108`, `AMP-118`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-508`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before connecting a product feed (CSV/TSV/XML or Salla/Zid/Shopify catalog link) to Snapchat Business Manager for Dynamic Product Ads in KSA, UAE, Kuwait, Qatar, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم قبل ربط ملف كتالوج المنتجات بمدير أعمال سناب شات (`Snapchat Business Manager`) لتشغيل إعلانات الكتالوج الديناميكية في السعودية أو الإمارات أو الكويت أو قطر أو مصر.
- **Do NOT Use When**: Do not assume Salla's native Snapchat catalog link has identical `item_ids` to your custom GTM Snap Pixel without inspecting a live `PAGE_VIEW`/`ADD_CART` event (`AMP-544`).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Snapchat Product Catalog Feed URL or XML/CSV export
   - Snap Pixel Helper Chrome extension output on a live Product Page and Add-to-Cart event
   - Store currency (`SAR`, `AED`, `KWD`, `QAR`, `BHD`, `OMR`, `EGP`)
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
