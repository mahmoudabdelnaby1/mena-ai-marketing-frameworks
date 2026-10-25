# `FW-077` — Egypt & KSA Localized Checkout Address Form Workflow
## مسار تخصيص حقول العنوان في صفحة الدفع لمصر والسعودية

- **One-Sentence Promise (EN)**: Review checkout address fields against the merchant's platform, address-validation needs, and selected carrier; do not assume a postal-code rule is universal. An Egypt-specific option is `Governorate -> City/District -> Street/Building/Floor -> Landmark` structure and Saudi Arabia's `City + District + Optional National Address Short-Code / Map Pin`.
- **الوعد التطبيقي في جملة واحدة (AR)**: استبدال حقول العناوين الغربية (`State` والرمز البريدي الإجباري `Zip Code`) بهيكلة الشحن الفعلية في مصر (المحافظة ← المنطقة/الحي ← الشارع ورقم العقار والدور ← علامة مميزة) وفي السعودية (المدينة ← الحي ← الرمز المختصر للعنوان الوطني أو دبوس الخريطة).
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Default Shopify, WooCommerce, and Magento checkouts require a mandatory 'Zip / Postal Code' (`الرمز البريدي`) and 'State'; 95%+ of Egyptian shoppers do not know their postal code (they type `'00000'` or `'11111'` or abandon when regex rejects it!), while couriers in Egypt (Bosta/Mylerz/Aramex) require `Governorate + District + Landmark (علامة مميزة)` and couriers in KSA (SPL/SMSA/Aramex) rely on `City + District + WhatsApp Location Pin / SPL Short Address`; an OPERATING_FRAMEWORK aligns checkout fields directly with regional courier APIs.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-400`, `AMP-410`, `AMP-420`, `AMP-430`, `AMP-440`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-540`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when configuring checkout shipping address forms on Salla, Zid, Shopify, WooCommerce, Magento, or custom apps in Egypt, Saudi Arabia, and the UAE.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد نموذج عنوان الشحن في صفحة الدفع لمتاجر مصر والسعودية والإمارات.
- **Do NOT Use When**: Confirm whether a postal code is required by the merchant’s platform, carrier, address validation, or delivery market before making it mandatory.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Courier Partner Zone & City Picklist (`Bosta / Mylerz` 27 Governorates & Districts in Egypt; `SMSA / Aramex / SPL` Cities in KSA; Emirates & Areas in UAE)
   - Checkout Field Configuration in Shopify (`Settings -> Checkout -> Address options`), WooCommerce, Salla, or Zid
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
