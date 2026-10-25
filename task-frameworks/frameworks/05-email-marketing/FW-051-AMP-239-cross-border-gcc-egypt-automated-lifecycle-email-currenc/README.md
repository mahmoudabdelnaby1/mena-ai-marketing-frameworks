# `FW-051` — Cross-Border GCC & Egypt Automated Lifecycle Email Currency, VAT & BNPL Localization Checklist
## قائمة فحص توطين العملات وضريبة القيمة المضافة (`15% KSA / 5% UAE / 0% Qatar / 14% Egypt`) وخيارات الدفع في الرسائل الآلية

- **One-Sentence Promise (EN)**: Prevent cross-border MENA lifecycle emails (abandoned cart, browse abandonment, back-in-stock, win-back) from displaying wrong currencies (`USD` or `SAR` to UAE/Egypt buyers) or omitting mandatory tax-inclusive VAT disclosures.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع رسائل البريد الآلية العابرة للحدود من عرض عملات خاطئة أو إغفال بيان شمول ضريبة القيمة المضافة الإلزامية (`15%` في السعودية، `5%` في الإمارات، `0%` في قطر، `14%` في مصر) وخيارات التقسيط المحلية.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Multi-country stores on Shopify Markets, Salla, Zid, or Magento frequently send dynamic product blocks in Klaviyo/Omnisend that pull the store's base currency (`SAR` or `USD`) regardless of the recipient's country, or omit mandatory tax-inclusive consumer pricing disclosures; a localization CHECKLIST with Liquid currency/VAT routing prevents checkout shock.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-249`, `AMP-259`, `AMP-269`, `AMP-279`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever operating automated lifecycle emails for a store selling across 2 or more MENA countries (KSA, UAE, Kuwait, Qatar, Bahrain, Oman, Egypt).
- **داعي الاستخدام (AR)**: تُستخدم عند تشغيل سلاسل البريد الآلي لمتجر يبيع في دولتين أو أكثر من دول الخليج ومصر.
- **Do NOT Use When**: Never display consumer product prices in Saudi Arabia or UAE as 'Tax-Exclusive' (`السعر غير شامل الضريبة`) in marketing emails only to add 15% or 5% VAT as a surprise at checkout.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Customer Country Property in ESP (`person.country_code`: `SA`, `AE`, `KW`, `QA`, `BH`, `OM`, `EG`)
   - Catalog Multi-Currency Price Attributes or Presentment Currency (`event.extra.presentment_currency`)
   - Country-Specific Payment & Shipping Threshold Table
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
