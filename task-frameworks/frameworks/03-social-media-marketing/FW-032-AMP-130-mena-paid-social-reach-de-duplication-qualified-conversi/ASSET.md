# FW-032: MENA Paid Social Reach De-Duplication & Qualified Conversion Evaluation Aid (TikTok/Snap KSA & UAE)
## أداة تقييم الوصول الفعلي والتحويلات المؤهلة في إعلانات التواصل الاجتماعي (معالجة تضخم أرقام الوصول في تيك توك وسناب شات بالخليج)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-140`, `AMP-150`, `AMP-160`, `AMP-170`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Calibrate paid social media plans and executive reports in KSA and UAE where platform-reported ad reach exceeds 100% of the adult population due to multi-account and device duplication.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: معايرة خطط وتقارير الإعلانات الاجتماعية في السعودية والإمارات حيث يتجاوز «الوصول الإعلاني المعلن» 100% من عدد السكان البالغين بسبب تعدد الحسابات والأجهزة.
- **Why `DECISION_AID` Fits This User Job (EN)**: DataReportal Digital 2026 explicitly notes that reported social ad reach in KSA (e.g., TikTok's 38.6M reported reach vs. ~34.4M total population) and UAE (TikTok 118.8%) exceeds 100% of the population due to duplicate accounts, SIMs, and tourist/visitor churn; a DECISION_AID stops AI reporting agents from presenting vanity reach as unique humans.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: تشير تقارير DataReportal Digital 2026 صراحةً إلى أن أرقام الوصول الإعلاني في السعودية (مثل 38.6 مليون في تيك توك مقابل 34.4 مليون إجمالي السكان) والإمارات (118.8%) تتجاوز 100% من السكان بسبب تعدد الحسابات والشرائح؛ لذا تمنع أداة القرار هذه بناء الميزانيات على أرقام وصول مضخمة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when evaluating media agency proposals, forecasting reach/frequency in KSA/UAE/Qatar/Kuwait, or building executive AI marketing performance reports.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند مراجعة عروض الوكالات الإعلانية أو التنبؤ بالوصول والتكرار (`Reach & Frequency`) في السعودية والإمارات وقطر والكويت أو إعداد تقارير الأداء التنفيذية.
- **When NOT to Use It (EN)**: Do not sum 'Unique Reach' across TikTok + Snapchat + Instagram + YouTube in KSA or UAE and claim you reached '85 million people in Saudi Arabia' (`AMP-564`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً بجمع أرقام الوصول (`Reach`) عبر تيك توك وسناب شات وإنستغرام ويوتيوب في تقرير واحد والادعاء بالوصول إلى «80 مليون شخص في السعودية» (`AMP-564`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Platform-reported `Reach`, `Impressions`, `3-Second / 6-Second Focused Views`, and `Conversions` per channel
2. Official Population / Target Demographic Ceiling (GASTAT KSA / UAE FCSC / CAPMAS Egypt)
3. First-party verified downstream metrics (Unique Engaged Sessions in GA4, OTP-Verified Leads, or Net Delivered Orders)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **TikTok, Snapchat & Meta Ad Manager Reach Estimation vs. DataReportal 2026 Census Notes** | `supported` | [Official Reference](https://thegrower.ai/gcc-marketing) (`2026-10-25`) | DataReportal explicitly notes that ad reach figures reflect user accounts rather than unique individuals, explaining why KSA/UAE/Qatar figures exceed 100% of population. | Never use `SUM(Reach)` across campaigns or platforms; use `MAX(Reach)` as a lower bound and track unique first-party engaged users. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-140`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Evaluating TikTok and Snapchat strictly on verified downstream conversions and holdout lift.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-150`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Evaluating TikTok and Snapchat strictly on verified downstream conversions and holdout lift.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-160`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Evaluating TikTok and Snapchat strictly on verified downstream conversions and holdout lift.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-170`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Evaluating TikTok and Snapchat strictly on verified downstream conversions and holdout lift.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Scenario**: A Riyadh retail brand's monthly AI-generated agency deck claimed: `"حققنا هذا الشهر وصولاً لـ 46 مليون مستخدم فريد في المملكة العربية السعودية عبر تيك توك وسناب شات وإنستغرام!"` (claiming 46M unique Saudis when the entire population of KSA is ~34.4M).
- **Human Review & Key Edits Applied**: 1. **Added Explicit Footnote in Monthly Report Template**: Added a permanent footnote to the automated reporting prompt forbidding cross-platform `Reach` summation and citing GASTAT/DataReportal multi-account methodology.
2. **Shifted Awareness Bidding**: Moved top-of-funnel campaigns from `Maximum Reach (Impressions)` to `6-Second Focused View / ThruPlay`.
- **Final Usable Output**: - Executive reporting template updated to prevent `>100%` population reach hallucinations and tie media spend to 6-second attention and verified site/checkout actions.
- **What Can Go Wrong**: An automated Looker Studio / LLM commentary script sums the `Reach` column across 8 campaigns within the same ad account and tells the CEO `'We reached 22 million people in Dubai this week'` (where Dubai's population is ~3.8M).
- **Correction & Fallback**: In Looker Studio, BigQuery, and AI reporting prompts, mark `Reach` as a **Non-Summable Metric (`MAX` only, never `SUM` across rows)**—summing `Reach` across campaigns or ad sets is mathematically invalid.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Cost per 6-Second Focused View, Cost per Incremental Engaged Session, and zero `SUM(Reach)` errors in client/executive dashboards.
- **Baseline Definition**: Prior monthly reporting audit.
- **Observation Window**: Monthly reporting cycle. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: De-duplicating reach metrics fixes reporting honesty and frequency planning, but does not replace true geo-holdout incrementality testing.
