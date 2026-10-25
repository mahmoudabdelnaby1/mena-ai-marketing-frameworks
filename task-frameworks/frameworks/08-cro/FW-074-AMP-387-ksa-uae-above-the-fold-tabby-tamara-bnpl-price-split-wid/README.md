# `FW-074` — KSA & UAE Above-the-Fold Tabby & Tamara BNPL Price-Split Widget Checklist
## قائمة فحص وضع شارات تقسيط «تابي» و«تمارا» (`Tabby & Tamara`) بجوار السعر مباشرة أعلى طية صفحة المنتج في السعودية والإمارات

- **One-Sentence Promise (EN)**: Place dynamic Tabby and Tamara 4-installment price calculators (`'أو 4 دفعات بقيمة 74.75 ر.س بدون فوائد أو رسوم'`) immediately beneath the product price above the fold on mobile PDPs in KSA and UAE.
- **الوعد التطبيقي في جملة واحدة (AR)**: إظهار حاسبة الدفعات الأربع لـ «تابي» و«تمارا» (`أو قسّمها على 4 دفعات بقيمة X ر.س/د.إ بدون فوائد`) مباشرة تحت سعر المنتج أعلى طية شاشة الجوال في السعودية والإمارات.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Huptech and Soluvide 2026 UAE/KSA CRO studies confirm that BNPL (Tabby & Tamara) accounts for ~14%+ of UAE/KSA Shopify checkout volume and significantly increases AOV, yet AI-generated landing pages and default themes hide BNPL logos in the page footer or only reveal them on the final payment step—after the shopper already bounced from sticker shock on the Product Detail Page (PDP)!)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-397`, `AMP-407`, `AMP-417`, `AMP-427`, `AMP-437`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-537`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use on every Product Detail Page (PDP), Slide-Out Cart Drawer, and Landing Page in Saudi Arabia, UAE, Kuwait, and Qatar where AOV is `>= 100 SAR / 100 AED`.
- **داعي الاستخدام (AR)**: تُستخدم في جميع صفحات المنتجات (`PDP`) وسلة التسوق الجانبية وصفحات الهبوط في السعودية والإمارات والكويت وقطر للمنتجات التي تزيد عن 100 ريال/درهم.
- **Do NOT Use When**: Do not display static image screenshots of Tabby/Tamara that show a fixed or wrong installment number when the shopper switches product size/variant price!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Mobile Product Detail Page (`PDP`) above-the-fold layout (`375x812px` iPhone viewport)
   - Official Tabby Promo Snippet & Tamara Product Widget script (or Salla/Zid native BNPL widget toggle)
   - Store currency (`SAR`, `AED`, `KWD`, `QAR`) and minimum/maximum eligible order thresholds
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
