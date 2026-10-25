# MENA A/B Testing Calendar & Payday / Fri-Sat Weekend / Ramadan Cycle Decision Aid
## <span dir="rtl">أداة قرار ضبط مدة اختبارات `A/B Testing` في مصر والخليج (مراعاة دورة الرواتب `25–30 الشهر`، عطلة الجمعة والسبت، ومواسم رمضان)</span>

> **Asset ID**: `FW-078` (`AMP-391`) | **Artifact Type**: `DECISION_AID` | **Channel**: CRO - Conversion Rate Optimization | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent AI experimentation tools (`VWO`, `Optimizely`, `Convert`, `Meta A/B Test`) from declaring false winners after 3–5 days by enforcing full weekly (`Sun–Thu` vs `Fri–Sat`) and monthly salary-cycle (`25th–5th` vs `10th–24th`) observation windows.
- **AR**: <span dir="rtl">منع أدوات اختبار `A/B` بالذكاء الاصطناعي من إعلان نتائج مضللة بعد 3–5 أيام فقط عبر إلزام الاختبار بتغطية دورة الأسبوع العربي (`الأحد–الخميس` مقابل `الجمعة–السبت`) ودورة صرف الرواتب الشهرية (`25–5 الشهر`).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever designing, running, or evaluating landing page, checkout, pricing, or creative A/B tests in KSA, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تصميم أو تقييم أي اختبار مقارن (`A/B Test`) لصفحات الهبوط أو الأسعار أو الإعلانات في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Never run a sequential test ('Version A ran from the 15th to the 21st, and Version B ran from the 25th to the 30th') and attribute the payday surge to Version B!
- **متى لا تستخدمها (AR)**: <span dir="rtl">إياك وإجراء اختبار تتابعي (تشغيل النسخة A من يوم 15 إلى 21، ثم النسخة B من يوم 25 إلى 30 وقت نزول الرواتب) ونسب ارتفاع المبيعات للنسخة B!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Experiment Start Date & Planned Duration (in multiples of **7 full days**: `7, 14, 21, or 28 days`)
- Baseline Daily Conversions (`minimum 350 conversions per variation` before evaluating)
- Payday / Hijri / Seasonal Overlay (`AMP-125`)

## 2. The Working `DECISION_AID` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### MENA Experimentation Validity & Minimum Duration Decision Matrix

#### 1. The 4 Mandatory MENA A/B Testing Guardrails
| Testing Trap | Why It Corrupts AI Bandit / A/B Winners in MENA | Mandatory Operational Rule (`PASS`) |
| :--- | :--- | :--- |
| **1. Sequential Before/After Testing Across the 25th–30th Salary Window** | KSA (`27th` gov salary + `25th–30th` private) and Egypt/UAE payday week sees `1.6x–2.8x` higher natural conversion rate than the `12th–22nd` mid-month trough. | **Strictly Concurrent 50/50 Split Only** (Never compare Week 2 vs. Week 4 sequentially!). For pricing, BNPL (`AMP-387`), or AOV tests, include **both a pre-payday week (`15th–22nd`) and a payday week (`25th–2nd`)** (`14–21 days total`). |
| **2. Stopping Tests After 3–4 Days (Ignoring the `Thu Night – Sat` Weekend Cycle)** | B2B traffic peaks `Sun–Wed 9 AM–4 PM`, whereas B2C retail conversions peak `Thu 8 PM – Sat 11 PM` (with a sharp dip during **Friday Jumu'ah prayer `11:00 AM – 1:30 PM`**). | **Strict Multiple-of-7-Days Rule**: Every test MUST run for **`7`, `14`, `21`, or `28` exact full 24-hour days** so every day of the week is weighted equally. |
| **3. Enabling 'Auto-Allocate Traffic to Winner (Multi-Armed Bandit)' on Day 2** | An AI bandit shifts 80% of traffic to Variation B on Tuesday based on 15 early conversions, starving Variation A before Thursday/Friday weekend shoppers arrive. | **Lock 50/50 Fixed Traffic Split** until each variation reaches **`>= 350` net delivered conversions** AND at least **7 full days** have elapsed (use bandits only for short 72-hour flash sales). |
| **4. Optimizing on Front-End COD Order Placement Instead of Net Delivered Orders (`AMP-062`)** | A variation with a '1-Click No-Confirmation COD Button' inflates placed orders by 30% while increasing fake/refused COD orders by 45%! | For any checkout or COD test in Egypt/KSA, the Primary Evaluation Metric MUST be **Net Confirmed / Delivered Revenue per Visitor (`RPV`)**, not raw front-end order clicks! |

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Riyadh Electronics Store testing Variation A (`Free Shipping over 300 SAR`) vs. Variation B (`10% Off Coupon`).
- **Previous Flawed Test**: Ran Variation A from `18–22 October` (pre-payday trough, CVR `1.4%`), then switched the site to Variation B from `26–30 October` (Saudi salary week, CVR `2.9%`) and concluded Variation B 'doubled conversion rate'.

### Step B: Initial Output (`المخرج الأولي`)
- **Audit Verdict**: **`INVALID SEQUENTIAL TEST (Confounded by KSA 27th October Salary Surge)`**
- **Re-Run Valid Concurrent Protocol**:
  - Launched a 50/50 concurrent split (`Variation A` vs. `Variation B` running simultaneously on the exact same days) for **14 full days (`18 Oct – 31 Oct`)**, covering both the pre-payday week and the salary week across two full `Fri/Sat` weekends.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Segmented Results by Payday Window**: The valid 14-day concurrent test revealed that `Variation A (Free Shipping Threshold)` actually beat `Variation B` by `+11%` in net margin during payday week (`26–31 Oct`), whereas `Tabby/Tamara Installment Highlight` drove higher conversion during the mid-month trough (`18–24 Oct`).
2. **Locked Minimum Sample Gate**: Added a hard rule in the VWO/Optimizely runbook: zero winner declarations under `14 days` and `350 conversions/arm`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Established a 14-day concurrent A/B testing SOP anchored to KSA/Egypt payday and Fri/Sat weekend cycles, eliminating false-positive bandit switches.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An e-commerce manager runs a checkout test during the last 5 days of Sha'ban and continues it into the first 5 days of Ramadan (`AMP-125`), when hourly traffic shifts completely from daytime (`12 PM–5 PM`) to post-Iftar/Suhoor (`9 PM–3 AM`).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Never span a single A/B test across a major **Regime Boundary** (`Sha'ban -> Ramadan`, `Ramadan -> Eid`, or `Normal Week -> White Friday`); close pre-season tests before the regime shift and run dedicated in-season tests.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **VWO, Optimizely, Convert & Meta/Google Experimentation Statistical Engines** | `supported` | [Official Docs](https://23hublab.com/digital-advertising-landscape-in-egypt/) (`2026-10-25`) | Standard frequentist and Bayesian A/B engines assume stationary conversion rates over time; because MENA conversion rates exhibit strong non-stationary payday (25th–30th) and Fri/Sat weekly cycles, fixed 50/50 splits over full 7/14-day multiples are mandatory. | Always use fixed 50/50 traffic allocation for 14 full days instead of early-stopping auto-bandits. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Net Delivered Revenue per Visitor (`RPV`) across a full 14-day concurrent window (`p < 0.05`, power `>= 80%`).
- **Baseline**: Control variation (`50%` concurrent traffic).
- **Observation Window**: Minimum 14 full days (2 weekly cycles + payday alignment).
- **Interpretation Boundary**: A 14-day test validates conversion lift under current traffic mix; re-validate winners if channel mix shifts significantly.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
- [Paid Media Cost Comparison: Egypt vs. UAE vs. Saudi Arabia](https://23hublab.com/paid-media-cost-comparison-egypt-vs-uae-vs-saudi-arabia/) — *23HubLab* (Published `2026-04-10`, Accessed `2026-10-25`): UAE CPMs run 4-5x higher than Egypt CPMs, and Saudi CPMs run 60-80% of UAE levels; Ramadan increases Egyptian Meta CPMs by 40-70%; pooling Egypt and GCC into a single automated budget/ad set causes algorithms to dump spend into cheap Egyptian clicks.
- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
