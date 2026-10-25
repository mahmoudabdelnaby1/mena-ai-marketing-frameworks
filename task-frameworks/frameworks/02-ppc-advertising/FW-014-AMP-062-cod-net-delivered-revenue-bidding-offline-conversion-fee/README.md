# `FW-014` — COD Net-Delivered Revenue Bidding & Offline Conversion Feedback Workflow (Egypt & KSA)
## مسار عمل تدريب خوارزميات الإعلانات على «طلبات الدفع عند الاستلام المسلّمة فعلياً» بدلاً من الطلبات الوهمية (مصر والسعودية)

- **One-Sentence Promise (EN)**: Stop Meta and Google AI bidding from optimizing toward high-return Cash-on-Delivery (COD) impulse clickers by discounting front-end COD pixel values and feeding back courier-delivered conversions.
- **الوعد التطبيقي في جملة واحدة (AR)**: إيقاف خوارزميات Meta وGoogle عن استهداف شرائح العملاء الأكثر إلغاءً ورفضاً لطلبات الدفع عند الاستلام (COD) عبر خصم القيمة المبدئية للطلب وتغذية المنصة بالطلبات المسلّمة فعلياً.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: In Egypt and KSA, COD cancellations and courier refusals inflate front-end platform conversion metrics by 20–40% (23HubLab 2026 benchmark); an end-to-end OPERATING_FRAMEWORK aligning pixel event rules, value multipliers, and courier CAPI/Offline feedback fixes the optimization signal.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-072`, `AMP-082`, `AMP-092`, `AMP-102`, `AMP-112`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when the merchant wants to evaluate delivered-order contribution, COD costs, and acquisition economics using its own order and courier data.
- **داعي الاستخدام (AR)**: يُستخدم عند الحاجة إلى تقييم هامش الطلبات المسلّمة وتكلفة الدفع عند الاستلام واقتصاديات اكتساب العميل اعتمادًا على بيانات المتجر نفسه.
- **Do NOT Use When**: Do not delay the primary browser/CAPI `Purchase` signal by 5–7 days waiting for physical courier delivery if that starves Meta's 7-day attribution window—use the Dual-Signal Expected-Value Multiplier below instead.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Historical Courier Delivery Rate (`Delivered_Rate = Delivered_Orders / Placed_Orders`) segmented by Payment Method (`Prepaid/Card/InstaPay/Tabby` vs. `COD`) and Governorate/Region
   - Meta Conversions API (CAPI) & Google Ads Enhanced Conversions for Leads / Offline Conversion Import access
   - WhatsApp/Phone Order Confirmation workflow (`AMP-448`)
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
