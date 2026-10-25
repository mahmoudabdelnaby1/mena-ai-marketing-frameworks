# FW-027: MENA Dual Hijri-Gregorian & National-Occasion AI Content Calendar Workflow
## مسار عمل بناء خطط المحتوى بالذكاء الاصطناعي بالتقويمين الهجري والميلادي (رصد تداخل رمضان مع الأعياد الوطنية والمواسم)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-135`, `AMP-145`, `AMP-155`, `AMP-165`, `AMP-175`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Build quarterly and annual MENA content calendars anchored to verified Hijri-Gregorian dates, payday windows, and overlapping national occasions (such as February 2027 when Ramadan, Saudi Founding Day, and Kuwait National Day converge in the same month).
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: بناء خطط المحتوى السنوية والربع سنوية بربط التقويمين الهجري والميلادي ومواسم الرواتب وتداخل المناسبات الوطنية والدينية (مثل فبراير 2027 حيث يتقاطع رمضان مع يوم التأسيس السعودي والعيد الوطني الكويتي).
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Generic LLMs build Gregorian-only calendars based on Western retail holidays (or outdated Hijri dates from prior years because the lunar calendar shifts ~11 days earlier each year); an OPERATING_FRAMEWORK with a verified 2026–2027 Hijri-Gregorian anchor table prevents embarrassing scheduling collisions.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تعتمد النماذج اللغوية افتراضياً على التقويم الميلادي الغربي أو تواريخ هجرية قديمة من سنوات سابقة (رغم تقدم التقويم الهجري ~11 يوماً كل عام)؛ لذا يضمن هذا الإطار التشغيلي تطابق الخطط مع التقويم الفعلي وتداخلات المواسم.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when planning monthly, quarterly, or annual content, social, email, and promotional calendars for Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إعداد خطط المحتوى والحملات الشهرية أو الربع سنوية أو السنوية لأسواق الخليج ومصر.
- **When NOT to Use It (EN)**: Do not let an LLM guess Hijri dates from its internal memory—always inject the verified Umm al-Qura / local astronomical reference table into the prompt context first.
- **متى لا تستخدم هذه الأداة (AR)**: لا تسمح للنموذج اللغوي بتخمين التواريخ الهجرية من ذاكرته الداخلية؛ احقن دائماً جدول تقويم أم القرى الموثق داخل البرومبت أولاً (`مع مراعاة ثبوت الرؤية الشرعية`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Verified Umm al-Qura (`تقويم أم القرى`) & National Holiday Reference Table for Q4 2026 – Q2 2027
2. Target Markets (`KSA`, `UAE`, `Egypt`, `Kuwait`, `Qatar`) and Monthly Payday Windows (`25th–30th` Gregorian + `27th` Saudi government salary date)
3. Lead-time requirements for Regulatory Permits (`AMP-064` KSA Discount Permit, `AMP-281` Mawthooq Creator Booking)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 1. Verified Q4 2026 – H1 2027 MENA Calendar & Overlap Anchor Table
*(Inject this block verbatim into every AI Content Calendar prompt)*

```xml
<verified_mena_calendar_2026_2027>
- **11 Nov 2026**: Singles' Day (11.11) E-Commerce Flash Sale (KSA, UAE, Egypt).
- **20–30 Nov 2026**: White Friday / Yellow Friday Peak Week (Requires GMC sale_price pre-upload by 18 Nov — AMP-063).
- **02 Dec 2026**: UAE 55th Eid Al Etihad / National Day (Peak UAE retail, hospitality & national pride campaigns).
- **16 Dec 2026**: Bahrain National Day | **18 Dec 2026**: Qatar National Day.
- **25–30 Monthly**: Private-sector & regional payday conversion window (`+27th` of Gregorian month for KSA government salaries).
- **CRITICAL FEBRUARY 2027 TRIPLE OVERLAP (1448 AH)**:
  - **~08 Feb 2027** (Subject to moon sighting / 1 Ramadan 1448 AH): **Start of Ramadan 2027**.
  - **22 Feb 2027** (15 Ramadan 1448 AH): **Saudi Founding Day (`يوم التأسيس`) falls RIGHT INSIDE MID-RAMADAN 2027!**
  - **25–26 Feb 2027** (18–19 Ramadan 1448 AH): **Kuwait National & Liberation Days fall INSIDE RAMADAN 2027!**
  - *Operational Rule for Feb 2027*: Never schedule separate conflicting tone campaigns for Valentine's Day (14 Feb) or upbeat Founding Day concerts in KSA during Ramadan 2027—unify Founding Day (`يوم بدينا`) heritage storytelling with Ramadan spiritual/family warmth (`رمضان يجمعنا`).
- **~10 Mar 2027** (1 Shawwal 1448 AH): **Eid Al-Fitr 2027**.
- **~16 May 2027** (10 Dhu al-Hijjah 1448 AH): **Eid Al-Adha 2027**.
</verified_mena_calendar_2027>
```

### 2. 4-Step Calendar Generation Workflow
1. **Step 1 — Lock the Reference Table**: Paste `<verified_mena_calendar_2026_2027>` into the prompt and forbid the LLM from inventing any unverified Hijri date.
2. **Step 2 — Map Tonal & Visual Transitions**:
   - **Pre-Ramadan (`Sha'ban` / Late Jan 2027)**: Stock-up, home preparation, kitchenware, grocery, early Ramadan gifting.
   - **Ramadan Days 1–20 (`Feb 2027`)**: Evening peak posting (`9:00 PM – 2:00 AM` post-Iftar/Suhoor), zero upbeat music (`AMP-065`), heritage fusion on 22 Feb for Saudi Founding Day.
   - **Ramadan Last 10 Nights (`Late Feb – Early Mar 2027`)**: Shift to Eid Al-Fitr fashion/gifting (`ملابس العيد / عطور العيد / العيديات`) with explicit courier last-order cutoff dates (`آخر موعد للطلب قبل العيد`).
3. **Step 3 — Attach Moon-Sighting Contingency Variants (`Variant A: 29-Day Month` vs. `Variant B: 30-Day Month`)**:
   - Pre-draft two versions of the "Ramadan Mubarak" and "Eid Mubarak" posts so the social manager publishes within 5 minutes of official Supreme Court / Dar Al-Ifta moon-sighting confirmation.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **LLM Internal Training Cutoffs vs. Hijri Lunar Calendar Progression** | `unsupported` | [Official Reference](https://thegrower.ai/gcc-marketing) (`2026-10-25`) | Grower AI 2026 GCC playbook highlights the critical Feb 2027 overlap where Ramadan (~8 Feb 2027), Saudi Founding Day (22 Feb), and Kuwait National Day (25 Feb) converge; ungrounded LLMs routinely hallucinate outdated Hijri dates. | Always supply `<verified_mena_calendar_2026_2027>` inside the prompt context. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-135`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Dual Hijri-Gregorian calendar prompt templates with 6-week creative lock lead times.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-145`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Dual Hijri-Gregorian calendar prompt templates with 6-week creative lock lead times.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-155`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Dual Hijri-Gregorian calendar prompt templates with 6-week creative lock lead times.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-165`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Dual Hijri-Gregorian calendar prompt templates with 6-week creative lock lead times.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-175`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Dual Hijri-Gregorian calendar prompt templates with 6-week creative lock lead times.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-515`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-155 (Social Media Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Brand**: GCC & Egypt Luxury Chocolate & Dates Gifting Brand planning Q1 2027 (`Jan–Mar 2027`).
- **Draft AI Mistake**: Without `<verified_mena_calendar_2026_2027>`, the LLM placed Ramadan in March/April (using 2023/2024 training data), scheduled daytime food delivery flash ads at `1:00 PM` on 15 Feb 2027 (during fasting hours!), and treated 22 Feb Saudi Founding Day as a standalone party campaign unconnected to Ramadan.
- **Human Review & Key Edits Applied**: 1. **Daytime Fasting Ad Schedule Rule**: Set paid food/chocolate video ads in KSA, UAE, Kuwait, Qatar, and Egypt to daypart from **`4:30 PM (Pre-Iftar)` to `2:30 AM (Suhoor)`** during Ramadan (`08 Feb – 09 Mar 2027`), pausing sensory food close-ups during morning/midday fasting hours.
2. **Permit Lead-Time Gate**: Added a calendar milestone on `15 Jan 2027` to obtain the Saudi Ministry of Commerce Discount Permit (`AMP-064`) and confirm `Mawthooq` creator licenses (`AMP-281`).
- **Final Usable Output**: - Complete Q1 2027 Bilingual Content & Campaign Calendar delivered with verified 1448 AH Hijri overlaps, dayparting rules, and moon-sighting contingency slots.
- **What Can Go Wrong**: An automated scheduling tool (Buffer/Hootsuite/Sprout) is pre-set to publish `'عيد فطر مبارك!'` at `7:00 AM` on the 30th day of Ramadan, but the moon is sighted the evening of the 29th—leaving the brand 12 hours late (or 24 hours early if the month completes 30 days).
- **Correction & Fallback**: Never put `1 Ramadan` or `1 Shawwal (Eid)` greeting posts on unattended auto-publish; stage them as **`Approved Draft — Hold for Official Moon Sighting Confirmation`**.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero calendar/cultural timing errors, on-time pre-season permit clearance (`>=14 days` before peak), and seasonal campaign ROAS.
- **Baseline Definition**: Prior Ramadan / Founding Day campaign prep timeline and engagement rate.
- **Observation Window**: Full seasonal cycle (`Sha'ban` through `Shawwal`). *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Accurate Hijri-Gregorian alignment prevents cultural missteps and missed shipping cutoffs, while creative and inventory readiness drive total revenue.
