# FW-022: MENA Healthcare & Pharmaceutical Paid Search Eligibility & Regulatory Routing Aid
## أداة القرار الإعلاني للقطاع الصحي والدوائي في الأسواق العربية (قيود `Google AI Mode` وتصاريح `SFDA / MOH / EDA`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-080`, `AMP-090`, `AMP-100`, `AMP-110`, `AMP-120`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Route healthcare, clinic, pharmacy, and supplement paid search budgets into eligible placements with mandatory SFDA, UAE MOHAP, and Egyptian EDA ad permit verification instead of blocked Google AI Mode drug placements.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: توجيه ميزانيات الإعلانات الصحية والدوائية والعيادات نحو المواضع الإعلانية المسموحة مع استيفاء تراخيص `SFDA` و`MOHAP` و`EDA` بدلاً من محاولة التشغيل في مواضع `Google AI Mode` المقيدة جغرافياً.
- **Why `DECISION_AID` Fits This User Job (EN)**: Healthcare and pharmaceutical advertisers in MENA face two intersecting walls: (1) Google's Healthcare and Medicines policy restricts prescription/OTC drug ad formats by approved country list (excluding Arab jurisdictions from AI Mode pharmaceutical placements), and (2) Saudi SFDA/MOH, UAE MOHAP, and Egypt EDA mandate prior advertising permits; a DECISION_AID prevents account suspension and regulatory fines.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: يواجه معلنو القطاع الصحي والدوائي في المنطقة قيدين مزدوجين: (1) سياسات جوجل للأدوية والرعاية الصحية التي تقصر بعض المواضع المتقدمة مثل `AI Mode` على دول محددة ليس منها الدول العربية، و(2) اشتراط التراخيص المسبقة من `SFDA/MOH` و`MOHAP` و`EDA`؛ وتوجه أداة القرار هذه الحملات للمسار القانوني والتقني الصحيح.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before planning paid search or AI search ad campaigns for hospitals, aesthetic/dental clinics, online pharmacies, medical devices, or health supplements in KSA, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل تخطيط حملات البحث المدفوعة للمستشفيات أو عيادات التجميل والأسنان أو الصيدليات الإلكترونية أو المكملات والأجهزة الطبية في السعودية أو الإمارات أو مصر.
- **When NOT to Use It (EN)**: Do not launch any medical, pharmaceutical, or clinical procedure ad in KSA, UAE, or Egypt without an active, non-expired Ministry of Health / SFDA / EDA advertising license number displayed in the ad or landing page.
- **متى لا تستخدم هذه الأداة (AR)**: لا تطلق أي إعلان طبي أو دوائي أو تجميلي في السعودية أو الإمارات أو مصر دون رقم ترخيص إعلان صحي ساري المفعول ومكتوب بوضوح في الإعلان وصفحة الهبوط.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Product / Service Category (`Hospital/Clinic Service`, `OTC Supplement/Cosmetic`, `Medical Device`, or `Prescription Drug`)
2. Target Jurisdiction (`Saudi Arabia`, `UAE`, `Egypt`)
3. Active Regulatory License Number (`ترخيص إعلان صحي من وزارة الصحة / هيئة الغذاء والدواء SFDA / MOHAP / EDA`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Healthcare & Pharma Paid Search Routing Matrix (MENA)

| Sub-Vertical | Allowed Paid Search & Social Placements | Prohibited / Blocked Placements in MENA | Mandatory Statutory & Policy Gates |
| :--- | :--- | :--- | :--- |
| **1. Prescription Pharmaceuticals (`أدوية بوصفة طبية`)** | **NONE (Direct-to-Consumer Paid Ads Prohibited)** | Blocked across Google Ads (Search/Display/AI Mode), Meta, TikTok, and Snapchat in KSA, UAE & Egypt. | Restricted strictly to licensed HCP-only medical channels under SFDA / MOHAP / EDA rules. |
| **2. OTC Medicines, Medical Devices & Registered Supplements (`الأدوية اللاوصفية والمكملات المسجلة`)** | Standard Google Search SERP (where LegitScript/Google Pharmacy certification applies), Pharmacy Marketplace Sponsored Ads (`Nahdi`, `Al Dawaa`, `Chefaa`, `Amazon.sa`), Meta/Snap (with age & claim restrictions). | **Google AI Mode pharma placements** (no Arab jurisdiction is on the approved AI Mode drug-ad list) & any ad promising guaranteed cure (`AMP-176`). | 1. **KSA**: Valid **SFDA Registration & Ad Clearance** (penalties that depend on the applicable law and specific violation; confirm current scope with qualified local review for violations).<br>2. **UAE**: **MOHAP Health Advertisement License**.<br>3. **Egypt**: **EDA (`هيئة الدواء المصرية`)** registration & approval. |
| **3. Hospitals, Dental, Dermatology & Aesthetic Clinics (`المستشفيات والعيادات الطبية والتجميلية`)** | Standard Google Search (`Exact/Phrase` Local Intent + Google Maps Local Ads), Meta/Snapchat/TikTok (excluding before/after body-shaming or prohibited procedures like Botox/prescription injectables on restricted platforms). | Unlicensed treatment claims, guaranteed surgical results, or prescription injectable drug brand names in ad text. | 1. **KSA**: Ministry of Health (`ترخيص إعلان صحي - وزارة الصحة`) number displayed in ad/LP.<br>2. **UAE**: **MOHAP / DHA / DOH** facility & ad permit number (`#MOHAP-...` / `#DHA-...`) displayed visibly.<br>3. **Egypt**: Ministry of Health & Medical Syndicate rules. |

#### Pre-Flight Compliance Checklist for Clinic & Wellness Paid Search
- [ ] **Check 1 — Strip Prohibited Drug Brand Names from Ad Copy**: Even when advertising a licensed dermatology clinic in Riyadh or Dubai, including prescription toxin/filler brand names in Google Ad headlines triggers automated `Healthcare and medicines: Prescription drug terms` disapproval. Advertise the **licensed clinical consultation (`استشارة جلدية وتجميلية بترخيص وزارة الصحة رقم ...`)** instead.
- [ ] **Check 2 — Display License Badge in Hero Section**: Place the official `MOH / SFDA / MOHAP / DHA / EDA` permit number in plain HTML text at the top of the landing page so both human reviewers and automated policy crawlers verify it immediately.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Google Ads Healthcare and Medicines Policy & Regional Jurisdiction List** | `plan/region dependent` | [Official Reference](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) (`2026-10-25`) | Google restricts pharmaceutical advertising formats by country list and enforces strict automated checks on prescription drug terms globally. | Focus clinic campaigns on consultation and general dermatology/dental service terms with visible MOH/DHA/EDA permits. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-080`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Compliant organic GEO/AEO educational pages paired with licensed standard Search campaigns.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-090`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Compliant organic GEO/AEO educational pages paired with licensed standard Search campaigns.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-100`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Compliant organic GEO/AEO educational pages paired with licensed standard Search campaigns.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-110`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Compliant organic GEO/AEO educational pages paired with licensed standard Search campaigns.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-120`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Compliant organic GEO/AEO educational pages paired with licensed standard Search campaigns.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-510`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-100 (Pay-Per-Click (PPC) Advertising)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Advertiser**: Multi-branch Dermatology & Aesthetic Clinic in Riyadh and Dubai.
- **Problem**: Agency tried to run Google Search ads with headlines containing prescription injectable brand names and pitched 'Google AI Mode Pharma Ads' for a new hair-loss treatment; 18 of 20 ads were disapproved for `Restricted drug terms` and missing DHA/MOH permit disclosures.
- **Human Review & Key Edits Applied**: 1. **Landing Page Audit (`AMP-176`)**: Replaced `"علاج نهائي ومضمون 100% لتساقط الشعر"` on the landing page with `"جلسات عناية متخصصة بفروة الرأس تحت إشراف أطباء جلدية مرخصين"`.
2. **Expectation Alignment**: Clarified in the media plan that Google AI Mode pharma ad inventory is not enabled for Arab jurisdictions, shifting budget to standard High-Intent Arabic/English Search + Google Maps Local Pack.
- **Final Usable Output**: - `100%` of clinic Search ads approved in Riyadh and Dubai with visible `MOH` and `DHA` permit numbers and zero restricted-drug policy violations.
- **What Can Go Wrong**: A copywriter uses leetspeak or spacing tricks (`بـ.ـوتـ.ـوكس` or `B.o.t.o.x`) to bypass Google Ads' automated prescription drug filter; Google's policy system flags the account for `Circumventing Systems`, suspending the entire ad account permanently.
- **Correction & Fallback**: Never use obfuscation or character insertion to bypass medical ad filters (`Circumventing Systems` is a fatal account ban); remove restricted drug terms completely and apply for official Google Healthcare certification where eligible.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Ad Approval Rate (`100%` approved without `Restricted drug terms` flags) and Cost per Booked Clinic Appointment.
- **Baseline Definition**: Pre-fix ad disapproval rate.
- **Observation Window**: Checked at campaign launch and after every ad copy update. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: This decision aid routes ads to compliant formats; formal medical advertising approval always requires an active permit from KSA MOH/SFDA, UAE MOHAP/DHA/DOH, or Egypt MOH/EDA.
