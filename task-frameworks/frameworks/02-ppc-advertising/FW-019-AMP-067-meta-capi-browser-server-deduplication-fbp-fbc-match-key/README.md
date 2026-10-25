# `FW-019` — Meta CAPI Browser/Server Deduplication & `fbp`/`fbc` Match-Key Checklist for MENA Checkouts
## قائمة فحص منع ازدواجية التحويلات (`Deduplication`) وتمرير مفاتيح `fbp`/`fbc` في `Meta CAPI` لمتاجر المنطقة

- **One-Sentence Promise (EN)**: Fix Meta Pixel + Conversions API (CAPI) double-counting and missing `_fbp`/`_fbc` cookies across Salla, Zid, Shopify, and third-party payment redirects (Paymob, Moyasar, Tap, HyperPay, Tabby, Tamara).
- **الوعد التطبيقي في جملة واحدة (AR)**: إصلاح مشكلة حساب التحويل مرتين (`Double-Counting`) وفقدان معرفات `_fbp` و`_fbc` عند الانتقال لبوابات الدفع (Paymob, Moyasar, Tap, HyperPay, Tabby, Tamara) في متاجر سلة وزد وشوبيفاي.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: In MENA e-commerce, 25–40% of browser pixel events fail inside Instagram/TikTok/Snapchat in-app browsers or during off-domain payment redirects (Tabby, Tamara, Paymob, Mada 3DS), while misconfigured CAPI plugins send mismatched `event_id` values that double-count purchases; a technical CHECKLIST resolves both defects.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-077`, `AMP-087`, `AMP-097`, `AMP-107`, `AMP-117`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-507`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when configuring or auditing Meta Pixel + Conversions API (`CAPI`) on Salla, Zid, Shopify, WooCommerce, or custom checkouts in Egypt and the GCC.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد أو تدقيق ربط `Meta Pixel` مع `Conversions API (CAPI)` على سلة أو زد أو شوبيفاي أو ووكومرس في مصر والخليج.
- **Do NOT Use When**: Do not send unhashed raw phone numbers or emails to third-party endpoints—normalize and SHA-256 hash customer identifiers per Meta CAPI specification and Saudi/UAE/Egypt PDPL rules.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Meta Events Manager access (`Overview -> Purchase -> View Details -> Event Deduplication & Event Match Quality`)
   - List of active checkout redirect gateways (e.g., Tabby, Tamara, Moyasar, HyperPay, Tap, Paymob, Fawry, Kashier)
   - Sample test order ID (`order_id`) to trace in Meta Events Manager `Test Events`
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
