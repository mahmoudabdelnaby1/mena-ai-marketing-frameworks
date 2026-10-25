# MENA Dual Hijri-Gregorian & National-Occasion AI Content Calendar Workflow
## <span dir="rtl">مسار عمل بناء خطط المحتوى بالذكاء الاصطناعي بالتقويمين الهجري والميلادي (رصد تداخل رمضان مع الأعياد الوطنية والمواسم)</span>

> **Asset ID**: `FW-027` (`AMP-125`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Build quarterly and annual MENA content calendars anchored to verified Hijri-Gregorian dates, payday windows, and overlapping national occasions (such as February 2027 when Ramadan, Saudi Founding Day, and Kuwait National Day converge in the same month).
- **AR**: <span dir="rtl">بناء خطط المحتوى السنوية والربع سنوية بربط التقويمين الهجري والميلادي ومواسم الرواتب وتداخل المناسبات الوطنية والدينية (مثل فبراير 2027 حيث يتقاطع رمضان مع يوم التأسيس السعودي والعيد الوطني الكويتي).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when planning monthly, quarterly, or annual content, social, email, and promotional calendars for Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد خطط المحتوى والحملات الشهرية أو الربع سنوية أو السنوية لأسواق الخليج ومصر.</span>
- **When NOT to Use It (EN)**: Do not let an LLM guess Hijri dates from its internal memory—always inject the verified Umm al-Qura / local astronomical reference table into the prompt context first.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تسمح للنموذج اللغوي بتخمين التواريخ الهجرية من ذاكرته الداخلية؛ احقن دائماً جدول تقويم أم القرى الموثق داخل البرومبت أولاً (`مع مراعاة ثبوت الرؤية الشرعية`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Verified Umm al-Qura (`تقويم أم القرى`) & National Holiday Reference Table for Q4 2026 – Q2 2027
- Target Markets (`KSA`, `UAE`, `Egypt`, `Kuwait`, `Qatar`) and Monthly Payday Windows (`25th–30th` Gregorian + `27th` Saudi government salary date)
- Lead-time requirements for Regulatory Permits (`AMP-064` KSA Discount Permit, `AMP-281` Mawthooq Creator Booking)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Brand**: GCC & Egypt Luxury Chocolate & Dates Gifting Brand planning Q1 2027 (`Jan–Mar 2027`).
- **Draft AI Mistake**: Without `<verified_mena_calendar_2026_2027>`, the LLM placed Ramadan in March/April (using 2023/2024 training data), scheduled daytime food delivery flash ads at `1:00 PM` on 15 Feb 2027 (during fasting hours!), and treated 22 Feb Saudi Founding Day as a standalone party campaign unconnected to Ramadan.

### Step B: Initial Output (`المخرج الأولي`)
- **Corrected February 2027 Calendar Matrix**:
  - `25 Jan – 06 Feb 2027 (Sha'ban Prep)`: Early Corporate & Family Ramadan Gift Box Pre-Orders (`27 Jan` KSA Salary Day Hook).
  - `07/08 Feb 2027 (1 Ramadan 1448 AH — Dual Moon-Sighting Ready)`: Launch `"هلال الخير"` Evening Collection (`Posting Window: 8:30 PM – 1:30 AM KSA/Cairo`).
  - `18–22 Feb 2027 (11–15 Ramadan — Saudi Founding Day x Ramadan Heritage Edition)`: Limited-Edition `"يوم بدينا × ليالي رمضان"` Heritage Tin featuring traditional Saudi Najdi/Hijazi motifs for Iftar Majlis hospitality.
  - `25 Feb – 05 Mar 2027 (18–26 Ramadan)`: Eid Al-Fitr Gifting Pre-Order + Courier Cutoff Countdown.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Daytime Fasting Ad Schedule Rule**: Set paid food/chocolate video ads in KSA, UAE, Kuwait, Qatar, and Egypt to daypart from **`4:30 PM (Pre-Iftar)` to `2:30 AM (Suhoor)`** during Ramadan (`08 Feb – 09 Mar 2027`), pausing sensory food close-ups during morning/midday fasting hours.
2. **Permit Lead-Time Gate**: Added a calendar milestone on `15 Jan 2027` to obtain the Saudi Ministry of Commerce Discount Permit (`AMP-064`) and confirm `Mawthooq` creator licenses (`AMP-281`).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Complete Q1 2027 Bilingual Content & Campaign Calendar delivered with verified 1448 AH Hijri overlaps, dayparting rules, and moon-sighting contingency slots.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An automated scheduling tool (Buffer/Hootsuite/Sprout) is pre-set to publish `'عيد فطر مبارك!'` at `7:00 AM` on the 30th day of Ramadan, but the moon is sighted the evening of the 29th—leaving the brand 12 hours late (or 24 hours early if the month completes 30 days).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Never put `1 Ramadan` or `1 Shawwal (Eid)` greeting posts on unattended auto-publish; stage them as **`Approved Draft — Hold for Official Moon Sighting Confirmation`**.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **LLM Internal Training Cutoffs vs. Hijri Lunar Calendar Progression** | `unsupported` | [Official Docs](https://thegrower.ai/gcc-marketing) (`2026-10-25`) | Grower AI 2026 GCC playbook highlights the critical Feb 2027 overlap where Ramadan (~8 Feb 2027), Saudi Founding Day (22 Feb), and Kuwait National Day (25 Feb) converge; ungrounded LLMs routinely hallucinate outdated Hijri dates. | Always supply `<verified_mena_calendar_2026_2027>` inside the prompt context. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero calendar/cultural timing errors, on-time pre-season permit clearance (`>=14 days` before peak), and seasonal campaign ROAS.
- **Baseline**: Prior Ramadan / Founding Day campaign prep timeline and engagement rate.
- **Observation Window**: Full seasonal cycle (`Sha'ban` through `Shawwal`).
- **Interpretation Boundary**: Accurate Hijri-Gregorian alignment prevents cultural missteps and missed shipping cutoffs, while creative and inventory readiness drive total revenue.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
