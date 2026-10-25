# `FW-015` — Google Merchant Center White Friday Price-Update Cadence & Sale-Price Schema Checklist
## قائمة فحص وتوقيت تحديث الأسعار في Google Merchant Center خلال الجمعة البيضاء والمواسم لمنع رفض المنتجات

- **One-Sentence Promise (EN)**: Schedule promotional price updates in Google Merchant Center using `sale_price` and `sale_price_effective_date` instead of mutating base `price` more than once per day.
- **الوعد التطبيقي في جملة واحدة (AR)**: جدولة عروض الجمعة البيضاء والمواسم في Google Merchant Center باستخدام حقول `sale_price` و`sale_price_effective_date` بدلاً من تغيير السعر الأساسي أكثر من مرة يومياً وتجنب رفض المنتجات.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Google Merchant Center's 27 Sep 2026 policy explicitly warns that changing prices more than once a day causes automatic item updates to fail and risks item disapproval; a technical CHECKLIST for feed scheduling prevents mid-White-Friday Shopping/PMax blackouts.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-073`, `AMP-083`, `AMP-093`, `AMP-103`, `AMP-113`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before running White/Yellow Friday, Ramadan, Eid, Saudi National/Founding Day, or flash-sale campaigns linked to Google Merchant Center (`PMax` / `Shopping`).
- **داعي الاستخدام (AR)**: تُستخدم قبل تشغيل عروض الجمعة البيضاء أو رمضان أو العيد أو اليوم الوطني المرتبطة بحساب Google Merchant Center.
- **Do NOT Use When**: Do not use dynamic hourly repricing scripts or countdown-timer price mutations on URLs submitted to Google Merchant Center.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Promotional SKU list with Base Price (`price`), Promotional Price (`sale_price`), and exact start/end timestamps with timezone offset (`+03:00` KSA/Egypt DST or `+04:00` UAE)
   - Product page JSON-LD `offers` schema configuration
   - Statutory discount permit & baseline price history (`AMP-064`)
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
