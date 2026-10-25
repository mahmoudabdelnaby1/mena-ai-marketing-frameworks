# FW-021: Google Ads Search Campaign Channel Allocation & Lead Quality Review
## مراجعة توزيع القنوات وجودة العملاء المحتملين في حملات البحث على Google Ads

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-079`, `AMP-089`, `AMP-099`, `AMP-109`, `AMP-119`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Review Search campaign channel settings, allocation controls, and lead-quality signals as Google rolls out channel-prioritization changes.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: مراجعة توزيع القنوات وجودة العملاء المحتملين باستخدام إعدادات الحساب الحالية وبيانات العملاء المؤهلين، مع إعادة التحقق من التغييرات التي تطرحها Google تدريجياً.
- **Why `DECISION_AID` Fits This User Job (EN)**: Google is rolling out channel-prioritization and allocation changes. Their availability and behavior can vary by account and campaign, so a decision aid should help teams inspect current settings, campaign goals, and qualified outcomes before choosing a configuration.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: يؤدي تحديث جوجل (أكتوبر 2026 والانتقال إلى نموذج أولوية القنوات وتخصيص الميزانية في فبراير 2027) إلى السماح للخوارزمية بتحويل ميزانية حملات البحث إلى الشبكة الإعلانية (`Display`) الرخيصة إذا كان الحساب يتتبع النقرات أو النماذج الأولية غير المؤهلة؛ لذا تحسم أداة القرار هذه إعدادات الشبكة والتتبع.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when auditing or launching Google Search campaigns in KSA, UAE, or Egypt—especially for lead generation (real estate, clinics, B2B, education, automotive).
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند تدقيق أو إطلاق حملات بحث جوجل (`Google Search`) في السعودية أو الإمارات أو مصر، خاصة في قطاعات توليد العملاء المحتملين (العقارات، العيادات، الشركات B2B، التعليم).
- **When NOT to Use It (EN)**: Review network and channel settings against the campaign objective, current account controls, and qualified outcome data; avoid universal setting rules.
- **متى لا تستخدم هذه الأداة (AR)**: راجع إعدادات الشبكة والقنوات وفق هدف الحملة والخيارات المتاحة وبيانات النتائج المؤهلة، وتجنب القواعد العامة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Google Ads Campaign Settings -> `Networks` (`الشبكات`) status across all active Search campaigns
2. Search Campaign Spend Breakdown by Network (`Search` vs. `Search Partners` vs. `Display Expansion`)
3. Primary Conversion Action configuration (`Page View / Raw Form Submit` vs. `Qualified Lead / CRM SQL`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Search-to-Display Spend Protection Decision Aid

#### 1. Network Isolation Decision Tree
1. **Check `Campaign Settings -> Networks -> Display Network`**:
   - **IF `Include Google Display Network` is checked**:
     - Review current channel priorities, budget allocation controls, conversion definitions, and lead-quality evidence. Choose settings based on the campaign goal and observed outcomes; do not apply a universal setting.
2. **Check `Campaign Settings -> Networks -> Google Search Partners`**:
   - Segment your campaign report by **`Network (with search partners)`** over the last 30 days:
   - **IF Search Partners CPA on *CRM-Qualified Leads* is `> 1.3x` Google Search CPA** (or if you only track raw front-end form submits without CRM feedback):
     - Review whether Search Partners fit the campaign objective and qualified-lead evidence; change the setting only after account-level review.
3. **Upgrade the Primary Conversion Signal (So Automated Bidding Cannot Game Display/Partner Clicks)**:
   - Replace raw front-end `Thank You Page View` or unverified `WhatsApp Button Click` (`AMP-126`) as the Primary Conversion Action with **OTP-Verified Lead** or **Offline CRM Qualified Lead (`MQL/SQL`)** via Enhanced Conversions for Leads (`AMP-446`).

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Google Ads channel settings and staged channel-prioritization changes** | `supported` | [Official Reference](https://support.google.com/google-ads/faq/10286469?hl=en) (`2026-10-25`) | Google Ads documents the channel-prioritization rollout and the February 2027 Display Expansion migration. Check the current account interface and set channel priorities and any best-effort budget allocations according to campaign objectives; these controls do not guarantee a fixed allocation. | Review current network and channel settings in the account. Choose priorities and allocation based on campaign goals and observed qualified outcomes; confirm changes with the account owner. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-079`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Strictly separating Search and Display into distinct campaigns before February 2027.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-089`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Strictly separating Search and Display into distinct campaigns before February 2027.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-099`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Strictly separating Search and Display into distinct campaigns before February 2027.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-109`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Strictly separating Search and Display into distinct campaigns before February 2027.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-119`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Strictly separating Search and Display into distinct campaigns before February 2027.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-509`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-089 (Pay-Per-Click (PPC) Advertising)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Advertiser**: Dubai & Riyadh Luxury Off-Plan Real Estate Brokerage (`$15,000/month` Google Search budget).
- **Problem**: Campaign had `Include Google Display Network` enabled under `Maximize Conversions`. After adding a simple 2-field lead form, Display Expansion consumed `44%` of the Search budget (`$6,600`), generating `310` spam/accidental mobile-game leads (`0` actual property buyers).
- **Human Review & Key Edits Applied**: 1. **Added Negative Placement Exclusion**: Added mobile app category exclusions at the Account level (`Content Suitability -> Excluded placements -> All Mobile Apps`) as a second firewall for PMax campaigns.
2. **Phone Input Validation**: Added Saudi/UAE mobile OTP verification (`+966 5...` / `+971 5...` normalized per `AMP-388`) before firing the primary lead event.
- **Final Usable Output**: - Document the selected channel settings and compare subsequent qualified outcomes with the prior baseline; this illustrative example does not establish a guaranteed allocation or result.
- **What Can Go Wrong**: A practitioner accepts Google Ads' inline 'Recommendations (`التوصيات`)' auto-apply suggestion `'Add Display Expansion to get more conversions at a similar CPA'`, which silently re-enables Display Network on Search campaigns.
- **Correction & Fallback**: Open `Recommendations -> Auto-apply` in Google Ads and **uncheck all automatic network/expansion recommendations** so Display Expansion can never be turned back on automatically.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Share of Search campaign spend on `Google Search` (`Target: 100%`) and Cost per CRM-Qualified Lead (`Cost / SQL`).
- **Baseline Definition**: Prior 30-day spend split (`Google Search` vs. `Display Expansion` / `Search Partners`) and lead-to-SQL qualification rate.
- **Observation Window**: 14–28 days post-change. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Eliminating Display Expansion stops low-intent spend leakage; total raw lead count may drop while qualified sales pipeline rate increases.
