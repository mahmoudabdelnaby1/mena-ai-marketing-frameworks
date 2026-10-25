# `FW-049` — Transactional vs. Promotional Email Template Separation Checklist (Saudi & UAE PDPL Compliance)
## قائمة فحص الفصل بين رسائل المعاملات (`الفواتير وتأكيد الطلب`) والرسائل الترويجية (الامتثال لنظام `PDPL` السعودي والإماراتي)

- **One-Sentence Promise (EN)**: Keep transactional order confirmations, ZATCA/ETA tax invoices, and shipping updates strictly free of unconsented promotional upsell banners so they remain lawful under contract-fulfillment basis and stay in the Primary inbox tab.
- **الوعد التطبيقي في جملة واحدة (AR)**: الفصل التام بين رسائل المعاملات التشغيلية (تأكيد الطلب، الفاتورة الضريبية، تتبع الشحنة) والعروض الترويجية لضمان مشروعيتها النظامية وعدم تصنيفها كرسائل تسويقية غير مصرح بها.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: E-commerce plugins and AI lifecycle builders frequently inject 'Buy 2 More at 30% Off!' promotional carousels into transactional Order Confirmation and Shipping Update emails sent to customers who NEVER opted into marketing; under Saudi PDPL Art. 25 and UAE PDPL Art. 4/17, adding predominant promotional content converts a contract-fulfillment notice into unlawful unconsented direct marketing (and pushes receipts into Gmail's Promotions tab).)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-247`, `AMP-257`, `AMP-267`, `AMP-277`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when auditing automated `Order Confirmation`, `ZATCA/ETA e-Invoice`, `Shipping Dispatch`, `Password Reset`, or `Warranty Registration` email/SMS/WhatsApp templates.
- **داعي الاستخدام (AR)**: تُستخدم عند مراجعة قوالب تأكيد الطلب، الفواتير الضريبية الإلكترونية، تحديثات الشحن، أو استعادة كلمة المرور.
- **Do NOT Use When**: Do not send a single template to all buyers if it contains cross-sell discounts; either strip promotional blocks from transactional receipts OR conditionally render them ONLY when `customer.marketing_consent == true`.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - All active Transactional Email & WhatsApp Templates (`Order Confirmed`, `Shipped`, `Delivered`, `Refunded`)
   - ESP Conditional Rendering syntax (`{% if person.marketing_consent == true %}` in Klaviyo/Liquid)
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
