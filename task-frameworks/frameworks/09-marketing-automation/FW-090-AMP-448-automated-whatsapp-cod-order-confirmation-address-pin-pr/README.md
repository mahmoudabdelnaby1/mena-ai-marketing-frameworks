# `FW-090` — Automated WhatsApp COD Order Confirmation, Address-Pin & Prepaid-Switch Workflow (Egypt & KSA)
## مسار عمل التأكيد الآلي لطلبات الدفع عند الاستلام (`COD`) والتحقق من موقع التوصيل عبر واتساب قبل تسليم الشحنة للمندوب (مصر والسعودية)

- **One-Sentence Promise (EN)**: Cut Cash-on-Delivery (`COD`) courier return-to-origin (`RTO`) losses by 25–40% in Egypt and Saudi Arabia by automatically verifying the buyer's intent, street/landmark, or map pin on WhatsApp within 90 seconds of order placement before printing the courier AWB.
- **الوعد التطبيقي في جملة واحدة (AR)**: خفض نسبة مرتجعات الدفع عند الاستلام (`COD RTO`) في مصر والسعودية بنسبة 25–40% عبر إرسال رسالة تأكيد تفاعلية آلية على واتساب خلال 90 ثانية من الطلب للتحقق من الجدية وتثبيت العنوان/الموقع قبل إصدار بوليصة الشحن.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: In Egypt using the merchant’s measured COD share and KSA (15–30% COD), impulse social-media shoppers frequently enter a typo in their phone number, write a vague 2-word address (`'القاهرة - مدينة نصر'`), or order from 3 stores and only accept the first parcel that arrives; dispatching unconfirmed COD parcels blindly costs the merchant double shipping fees (`75–110 EGP` / `30–45 SAR` per returned box); a pre-dispatch WhatsApp confirmation OPERATING_FRAMEWORK filters fake/remorse orders before they leave the warehouse.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-458`, `AMP-468`, `AMP-478`, `AMP-488`, `AMP-498`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use on 100% of Cash-on-Delivery (`COD`) orders in Egypt, Saudi Arabia, UAE, and wider MENA.
- **داعي الاستخدام (AR)**: تُستخدم لجميع طلبات الدفع عند الاستلام (`COD`) في مصر والسعودية والإمارات قبل تسليمها لشركة الشحن.
- **Do NOT Use When**: Do not put already-paid orders (`Apple Pay`, `Mada`, `Card`, `InstaPay Verified`, `Tabby`, `Tamara`) on hold waiting for WhatsApp confirmation—ship prepaid orders immediately and send them a standard shipping notification!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Storefront `Order Created` Webhook (`payment_method == 'cod'`)
   - Approved WhatsApp `UTILITY` Order Confirmation Template (`AMP-441`) with 3 interactive Quick-Reply buttons
   - Courier API (`Bosta`, `Mylerz`, `Aramex`, `SMSA`, `J&T`) auto-dispatch tag (`Tag: COD_CONFIRMED_READY_TO_SHIP`)
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
