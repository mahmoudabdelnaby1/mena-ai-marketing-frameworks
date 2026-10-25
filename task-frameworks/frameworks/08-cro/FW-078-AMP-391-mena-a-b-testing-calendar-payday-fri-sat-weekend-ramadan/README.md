# `FW-078` — MENA A/B Testing Calendar & Payday / Fri-Sat Weekend / Ramadan Cycle Decision Aid
## أداة قرار ضبط مدة اختبارات `A/B Testing` في مصر والخليج (مراعاة دورة الرواتب `25–30 الشهر`، عطلة الجمعة والسبت، ومواسم رمضان)

- **One-Sentence Promise (EN)**: Prevent AI experimentation tools (`VWO`, `Optimizely`, `Convert`, `Meta A/B Test`) from declaring false winners after 3–5 days by enforcing full weekly (`Sun–Thu` vs `Fri–Sat`) and monthly salary-cycle (`25th–5th` vs `10th–24th`) observation windows.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع أدوات اختبار `A/B` بالذكاء الاصطناعي من إعلان نتائج مضللة بعد 3–5 أيام فقط عبر إلزام الاختبار بتغطية دورة الأسبوع العربي (`الأحد–الخميس` مقابل `الجمعة–السبت`) ودورة صرف الرواتب الشهرية (`25–5 الشهر`).
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: In Saudi Arabia, UAE, and Egypt, conversion rate and AOV swing dramatically between mid-month (`10th–24th`, when liquidity is tight and BNPL share spikes) and salary week (`25th–5th`, including the `27th` KSA government payday when cash/Mada purchases surge 2x–3x), as well as between the Friday/Saturday weekend (especially Friday prayer hours `11:30 AM – 1:30 PM` vs Thursday/Friday late nights); stopping an A/B test or switching ad creative after 4 days mistakes calendar seasonality for treatment lift!)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-401`, `AMP-411`, `AMP-421`, `AMP-431`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever designing, running, or evaluating landing page, checkout, pricing, or creative A/B tests in KSA, UAE, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند تصميم أو تقييم أي اختبار مقارن (`A/B Test`) لصفحات الهبوط أو الأسعار أو الإعلانات في السعودية والإمارات ومصر.
- **Do NOT Use When**: Never run a sequential test ('Version A ran from the 15th to the 21st, and Version B ran from the 25th to the 30th') and attribute the payday surge to Version B!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Experiment Start Date & Planned Duration (in multiples of **7 full days**: `7, 14, 21, or 28 days`)
   - Baseline Daily Conversions (`minimum 350 conversions per variation` before evaluating)
   - Payday / Hijri / Seasonal Overlay (`AMP-125`)
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
