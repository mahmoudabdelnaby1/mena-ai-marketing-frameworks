# `FW-052` — COD Serial-Returner Exclusion & Prepaid-Upgrade Win-Back Decision Aid (Egypt & KSA)
## أداة قرار استبعاد «كثيري رفض استلام طلبات COD» وتحويلهم للدفع المسبق في حملات استعادة العملاء (`Win-Back`)

- **One-Sentence Promise (EN)**: Prevent automated AI win-back and VIP discount flows from sending margin-destroying coupon codes to chronic Cash-on-Delivery (COD) non-receivers (`>40%` refusal rate) in Egypt and Saudi Arabia.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع سلاسل استعادة العملاء الآلية (`Win-Back`) من إرسال أكواد خصم مجزية للعملاء ذوي السجل المرتفع في رفض استلام طلبات الدفع عند الاستلام (`أكثر من 40% مرتجعات COD`) في مصر والسعودية، وتوجيههم حصرياً لعروض الدفع المسبق.
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: AI CRM segmentation tools normally trigger win-back discounts based on `Placed_Orders >= 2 AND Days_Since_Last_Order >= 60` without checking whether those orders were actually **delivered** or refused at the doorstep (`COD Returned to Sender`, which costs the merchant double shipping fees); a quantitative DECISION_AID segments win-back flows by Net Delivery Ratio.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-250`, `AMP-260`, `AMP-270`, `AMP-280`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when building VIP tiers, win-back flows, replenishment reminders, or birthday/seasonal coupon automations in Egypt, KSA, or wider MENA.
- **داعي الاستخدام (AR)**: تُستخدم عند بناء شرائح العملاء المميزين (`VIP`) أو سلاسل استعادة العملاء (`Win-Back`) أو كوبونات الخصم الآلية في مصر والسعودية.
- **Do NOT Use When**: Never define a 'High-Value / VIP Customer' in Klaviyo, HubSpot, Salla, or Zid using `Total Placed Orders` (`إجمالي الطلبات`)—always filter by `Fulfilled / Delivered & Collected Orders` (`الطلبات المكتملة والمسلمة`).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Customer Historical Order Counts: `orders_placed_count`, `orders_delivered_count`, `orders_cod_refused_count`
   - Round-trip Courier Cost per Refused COD Parcel (`~75–110 EGP` in Egypt / `~28–45 SAR` in KSA)
   - Prepaid-Only Promo Code capability in storefront (`InstaPay / Card / Mada / Tabby / Tamara only`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `DECISION_AID` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `DECISION_AID` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
