# MENA Paid Social Reach De-Duplication & Qualified Conversion Evaluation Aid (TikTok/Snap KSA & UAE)
## <span dir="rtl">أداة تقييم الوصول الفعلي والتحويلات المؤهلة في إعلانات التواصل الاجتماعي (معالجة تضخم أرقام الوصول في تيك توك وسناب شات بالخليج)</span>

> **Asset ID**: `FW-032` (`AMP-130`) | **Artifact Type**: `DECISION_AID` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Calibrate paid social media plans and executive reports in KSA and UAE where platform-reported ad reach exceeds 100% of the adult population due to multi-account and device duplication.
- **AR**: <span dir="rtl">معايرة خطط وتقارير الإعلانات الاجتماعية في السعودية والإمارات حيث يتجاوز «الوصول الإعلاني المعلن» 100% من عدد السكان البالغين بسبب تعدد الحسابات والأجهزة.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when evaluating media agency proposals, forecasting reach/frequency in KSA/UAE/Qatar/Kuwait, or building executive AI marketing performance reports.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند مراجعة عروض الوكالات الإعلانية أو التنبؤ بالوصول والتكرار (`Reach & Frequency`) في السعودية والإمارات وقطر والكويت أو إعداد تقارير الأداء التنفيذية.</span>
- **When NOT to Use It (EN)**: Do not sum 'Unique Reach' across TikTok + Snapchat + Instagram + YouTube in KSA or UAE and claim you reached '85 million people in Saudi Arabia' (`AMP-564`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم أبداً بجمع أرقام الوصول (`Reach`) عبر تيك توك وسناب شات وإنستغرام ويوتيوب في تقرير واحد والادعاء بالوصول إلى «80 مليون شخص في السعودية» (`AMP-564`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Platform-reported `Reach`, `Impressions`, `3-Second / 6-Second Focused Views`, and `Conversions` per channel
- Official Population / Target Demographic Ceiling (GASTAT KSA / UAE FCSC / CAPMAS Egypt)
- First-party verified downstream metrics (Unique Engaged Sessions in GA4, OTP-Verified Leads, or Net Delivered Orders)

## 2. The Working `DECISION_AID` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### MENA Reach De-Duplication & Executive Reporting Decision Matrix

#### 1. Why Raw Platform `Reach` Cannot Be Treated as Unique People in GCC
Per **DataReportal Digital 2026** (verified in `SOURCE-REGISTER.csv` & `AMP-564`):
- Platform ad-planning tools report **ad-addressable accounts/devices**, NOT deduplicated census individuals.
- In Saudi Arabia (`~34.4M` population) and the UAE (`~10.2M+` population), high multi-SIM ownership, work vs. personal phones, creator/business accounts, and international visitors push reported platform ad reach above `100%` of the adult population (`38.6M` on TikTok KSA; `118.8%` on TikTok UAE; `103.6%` in Qatar).

#### 2. Executive Reporting & Media Planning Decision Rules
| Common AI / Agency Reporting Mistake | Why It Fails | Mandatory Replacement Metric & Formula |
| :--- | :--- | :--- |
| **Mistake 1: Summing `Reach` across platforms** (`TikTok Reach 12M + Snap Reach 10M + IG Reach 8M = "30M Saudis Reached"`) | Counts the exact same Saudi shopper 3 to 5 times across apps and dual devices. | Report **Cross-Channel Reach strictly as `Max(Single_Platform_Reach)` + Overlapping Frequency**, and anchor the executive KPI on **Qualified Engaged Sessions (`GA4`)** or **Cost per 6-Second Focused View**. |
| **Mistake 2: Optimizing Top-of-Funnel on Cheap `1-Second Reach / Impressions`** | Buys low-attention scroll-past inventory across duplicate/inactive accounts. | Optimize video awareness on **6-Second Focused Views / ThruPlay (`Completed View`)** paired with a 2-second hook rate threshold (`>= 25%`). |
| **Mistake 3: Forecasting Market Saturation from Platform Audience Size** | Overestimates total addressable audience by `1.3x–1.6x`, leading to over-budgeting on narrow cohorts. | Apply a **`0.65x – 0.75x` Multi-Account Deflation Factor** to platform-estimated audience sizes in KSA, UAE, Qatar, and Kuwait when modeling unique household penetration. |

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Scenario**: A Riyadh retail brand's monthly AI-generated agency deck claimed: `"حققنا هذا الشهر وصولاً لـ 46 مليون مستخدم فريد في المملكة العربية السعودية عبر تيك توك وسناب شات وإنستغرام!"` (claiming 46M unique Saudis when the entire population of KSA is ~34.4M).

### Step B: Initial Output (`المخرج الأولي`)
- **Corrected Executive Scorecard (Reconciled & De-Duplicated)**:
  - **Gross Ad Impressions Across Platforms**: `68.4M`
  - **Platform Account Reach (Non-Additive)**: TikTok `14.2M` accounts | Snapchat `11.8M` accounts | Instagram `7.5M` accounts (`Estimated De-Duplicated Unique KSA Audience Reached: ~15.5M – 18.0M adults at ~3.8x–4.4x cross-platform frequency`).
  - **Verified Attention KPI**: `9.4M` 6-Second Focused Views (`Cost per 6s View: 0.04 SAR`).
  - **Verified Commercial KPI**: `312,000` Unique Engaged Storefront Sessions (`GA4`) -> `8,420` Net Delivered Orders.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added Explicit Footnote in Monthly Report Template**: Added a permanent footnote to the automated reporting prompt forbidding cross-platform `Reach` summation and citing GASTAT/DataReportal multi-account methodology.
2. **Shifted Awareness Bidding**: Moved top-of-funnel campaigns from `Maximum Reach (Impressions)` to `6-Second Focused View / ThruPlay`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Executive reporting template updated to prevent `>100%` population reach hallucinations and tie media spend to 6-second attention and verified site/checkout actions.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An automated Looker Studio / LLM commentary script sums the `Reach` column across 8 campaigns within the same ad account and tells the CEO `'We reached 22 million people in Dubai this week'` (where Dubai's population is ~3.8M).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: In Looker Studio, BigQuery, and AI reporting prompts, mark `Reach` as a **Non-Summable Metric (`MAX` only, never `SUM` across rows)**—summing `Reach` across campaigns or ad sets is mathematically invalid.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **TikTok, Snapchat & Meta Ad Manager Reach Estimation vs. DataReportal 2026 Census Notes** | `supported` | [Official Docs](https://thegrower.ai/gcc-marketing) (`2026-10-25`) | DataReportal explicitly notes that ad reach figures reflect user accounts rather than unique individuals, explaining why KSA/UAE/Qatar figures exceed 100% of population. | Never use `SUM(Reach)` across campaigns or platforms; use `MAX(Reach)` as a lower bound and track unique first-party engaged users. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Cost per 6-Second Focused View, Cost per Incremental Engaged Session, and zero `SUM(Reach)` errors in client/executive dashboards.
- **Baseline**: Prior monthly reporting audit.
- **Observation Window**: Monthly reporting cycle.
- **Interpretation Boundary**: De-duplicating reach metrics fixes reporting honesty and frequency planning, but does not replace true geo-holdout incrementality testing.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
