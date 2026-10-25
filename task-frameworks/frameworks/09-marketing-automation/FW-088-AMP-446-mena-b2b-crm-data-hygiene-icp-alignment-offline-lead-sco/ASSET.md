# FW-088: MENA B2B CRM Data Hygiene, ICP Alignment & Offline Lead-Scoring Feedback Framework
## الإطار التشغيلي لتنظيف بيانات `CRM` ومواءمة معايير العميل المثالي (`ICP`) بين التسويق والمبيعات في قطاع الأعمال (`B2B`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-456`, `AMP-466`, `AMP-476`, `AMP-486`, `AMP-496`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Clean duplicate/malformed Arabic-English CRM records, lock a shared Sales-Marketing Ideal Customer Profile (`ICP`), and feed back SQL status to Google/Meta/LinkedIn so AI lead-generation automation scales revenue instead of amplifying dirty data.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تنظيف سجلات `CRM` المكررة والمشوهة (بين العربية والإنجليزية)، وتوحيد تعريف «العميل المؤهل `MQL/SQL`» بين التسويق والمبيعات، وتغذية المنصات الإعلانية بالصفقات الحقيقية لمنع أتمتة الفوضى.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Founderz's 2026 B2B AI study and 23HubLab's Egypt/MENA lead-generation benchmarks demonstrate that deploying AI lead-scoring and outreach automation on top of a dirty CRM (where the same company is entered 4 times as `'شركة المراعي'`, `'Almarai'`, `'المراعي'`, and personal `@gmail.com` leads from job-seekers mix with C-suite buyers) amplifies errors at scale and floods sales reps in Riyadh, Dubai, and Cairo with junk leads; a 4-stage OPERATING_FRAMEWORK fixes data hygiene and ICP alignment first.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تثبت دراسات أتمتة مبيعات الشركات (`B2B` لعام 2026) أن تشغيل الذكاء الاصطناعي فوق قاعدة بيانات `CRM` غير منظمة (تتكرر فيها نفس الشركة بالعربية والإنجليزية وتختلط فيها طلبات الباحثين عن عمل بالعملاء الفعليين) يضاعف الفوضى ويغرق مندوبي المبيعات في الرياض ودبي والقاهرة بفرص وهمية؛ لذا يفرض هذا الإطار التشغيلي تنظيف البيانات وتوحيد المعايير قبل الأتمتة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before deploying AI lead scoring, automated SDR sequences, or value-based lead bidding (`AMP-069`) for B2B, SaaS, real estate, industrial, or healthcare enterprises in MENA.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل تشغيل أنظمة تقييم العملاء المحتملين بالذكاء الاصطناعي (`AI Lead Scoring`) أو أتمتة المبيعات في قطاعات الشركات (`B2B`) والعقارات والحلول التقنية.
- **When NOT to Use It (EN)**: Never automate outbound B2B emails/WhatsApp messages from CRM triggers until duplicate company records, Arabic-Indic phone numbers (`AMP-388`), and non-ICP disqualifiers (`Job Seeker / Student / Vendor`) are scrubbed.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بتفعيل الإرسال الآلي من الـ CRM قبل دمج السجلات المكررة، وتطبيع أرقام الهواتف، وعزل طلبات التوظيف والطلاب والموردين.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. CRM Contact & Company Export (`HubSpot`, `Salesforce`, `Zoho`, `Pipedrive`, `Dynamics 365`)
2. Joint Sales + Marketing Signed ICP Charter (`Minimum Company Size, Commercial Registration / CR presence, Target Geography, Budget Floor`)
3. Google Ads `GCLID` / Meta `Lead_ID` Offline Conversion Import integration

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 4-Stage MENA B2B CRM Hygiene & Closed-Loop Scoring Framework

#### Stage 1: Bilingual Entity Normalization & De-Duplication Gate (Run Before Any AI Scoring)
In MENA CRMs, the same account or contact is routinely duplicated across Arabic and English forms:
- **Phone Key Normalization (`Primary Contact Dedupe Key`)**: Convert Arabic-Indic digits (`٠-٩`) to ASCII (`AMP-388`) and format 100% of mobile numbers to strict **`E.164`** (`+9665...`, `+9715...`, `+201...`). Merge duplicate Contacts sharing the same `phone_e164` or `email_lowercase`.
- **Bilingual Company Name & Legal Prefix Normalization**: Strip legal suffixes/prefixes (`شركة، مؤسسة، مجموعة، ذات مسؤولية محدودة، ذ.م.م، ش.م.م، القابضة، LLC, WLL, Co., Ltd, Al-, الـ`) and normalize Arabic orthography (`AMP-002`) onto a shadow key `company_normalized_key` + corporate domain (`@domain.sa`) so `'شركة الفطيم ذ.م.م'` and `'Al-Futtaim LLC'` link to one parent Account!

#### Stage 2: The Progressive Form Gate (Filter Out Job Seekers & B2C Noise Before Entering Sales Queue)
In Egypt and GCC, 30–50% of raw form submissions on B2B ads come from job seekers (`AMP-066`), students, or tiny micro-vendors. Enforce this 3-field progressive gate:
1. **`الغرض من التواصل (Inquiry Purpose)`**:
   - `[شراء الخدمة لشركتي / طلب عرض سعر]` → Route to **Sales Pipeline**.
   - `[التقديم على وظيفة / تدريب]` → **BLOCK from CRM Sales Pipeline** (Redirect immediately to `/careers` page & fire `0` ad conversion value!).
   - `[تقديم عرض كمورد]` → Route to Procurement inbox (`0` ad conversion value!).
2. **`حجم المنشأة / عدد الموظفين` (`1–4` vs. `5–49` vs. `50–250` vs. `250+`)**.
3. **`رقم الجوال بصيغة صحيحة + البريد المؤسسي (أو رقم السجل التجاري / النشاط)`**.

#### Stage 3: Joint Sales-Marketing 100-Point ICP Scoring Rubric
| Dimension | High-Fit Tier (`+30 to +40 pts`) | Mid-Fit Tier (`+15 pts`) | Disqualified (`-100 pts -> MQL Blocked`) |
| :--- | :--- | :--- | :--- |
| **1. Geography & Entity** | Registered business in target market (`KSA`, `UAE`, `Egypt`) with verified company name/domain. | GCC/Egypt SME using Gmail/Hotmail but verified phone + commercial store link. | Outside service geography or student/job-seeker inquiry. |
| **2. Company Scale / Volume** | Matches ICP threshold (e.g., `>= 10` employees or `>= 2` retail branches). | Growing startup (`3–9` staff) with immediate budget. | No active business (`"فكرة مشروع مستقبلي بدون سجل"`). |
| **3. High-Intent Behavioral Signal** | Requested live demo, pricing calculator completion, or attended executive webinar. | Downloaded 1 whitepaper (`AMP-236` nurtures first; do NOT push straight to AE call!). | Unverified 1-click lead form with invalid phone. |

#### Stage 4: Closed-Loop Offline Conversion Sync (`CRM SQL -> Google Ads & Meta CAPI`)
- Fire the primary high-value conversion event back to Google Ads (`Enhanced Conversions for Leads` using `GCLID`/hashed email+phone) and Meta CAPI **ONLY when `ICP_Score >= 60` (`MQL/SQL`)**, starving spam/job-seeker clicks of algorithmic bidding credit (`AMP-069`)!

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **HubSpot / Salesforce Offline Conversion Sync to Google Ads (`GCLID`) & Meta CAPI for Leads** | `supported` | [Official Reference](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) (`2026-10-25`) | Passing CRM-qualified lead stages (`MQL/SQL`) back to Google Ads and Meta prevents automated bidding from optimizing toward cheap unqualified form-fills. | If real-time CRM API sync is unavailable, upload a weekly CSV of `GCLID` + SHA-256 hashed `email`/`phone` for qualified SQLs. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-456`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Pre-automation CRM hygiene gate (phone/domain normalization, duplicate merging, ICP role verification) plus closed-loop offline lead scoring.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-466`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Pre-automation CRM hygiene gate (phone/domain normalization, duplicate merging, ICP role verification) plus closed-loop offline lead scoring.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-476`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Pre-automation CRM hygiene gate (phone/domain normalization, duplicate merging, ICP role verification) plus closed-loop offline lead scoring.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-486`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Pre-automation CRM hygiene gate (phone/domain normalization, duplicate merging, ICP role verification) plus closed-loop offline lead scoring.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-496`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Pre-automation CRM hygiene gate (phone/domain normalization, duplicate merging, ICP role verification) plus closed-loop offline lead scoring.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Company**: Riyadh, Dubai & Cairo B2B Logistics & Warehouse Management SaaS (`Average Annual Contract: $14,000`).
- **Problem**: Marketing celebrated generating `1,200` 'AI-scored leads' in Q3, but Sales closed only `6` deals (`0.5%` close rate) and complained that `78%` of leads were truck drivers looking for jobs (`"وظائف سائق"`), university students, or duplicate entries of existing clients.
- **Human Review & Key Edits Applied**: 1. **Pragmatic MENA SME Email Rule**: Note that in Egypt and KSA, many legitimate traditional wholesale/retail business owners (`أصحاب مؤسسات تجارية حقيقية`) still use a personal `@gmail.com` or `@hotmail.com` address while conducting business on WhatsApp—so instead of hard-blocking `@gmail.com`, required **`اسم المؤسسة/المتجر + عدد الفروع + رقم جوال موثق`** to qualify them!
2. **Enforced 10-Minute Speed-to-Lead SLA on `Score >= 60` SQLs**: Routed verified `SQL` leads directly to the regional AE's WhatsApp/Phone queue within 60 seconds.
- **Final Usable Output**: - Raw junk lead volume dropped by `64%`, Sales rep time wasted on job seekers fell to `0%`, and MQL-to-SQL conversion rate rose from `9%` to **`38%`**.
- **What Can Go Wrong**: A Western B2B lead-scoring template automatically disqualifies (`-100 pts`) any lead submitting a `@gmail.com` or `@yahoo.com` email address; in Egypt and Saudi Arabia, this blocks 40%+ of profitable traditional family trading companies, clinics, and retail store owners who do not use corporate email daily.
- **Correction & Fallback**: In MENA B2B scoring, **do not auto-reject `@gmail.com` if the user provides a valid local mobile number (`+9665...` / `+201...`), a real store/establishment name (`اسم المنشأة أو المتجر`), and qualifying branch/employee count**!

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: MQL-to-SQL Acceptance Rate by Sales (`Target: >= 35%`), CRM Duplicate Contact Rate (`Target: < 1%`), and Cost per Closed-Won Deal.
- **Baseline Definition**: Prior quarter raw Lead-to-SQL conversion rate and duplicate record audit.
- **Observation Window**: 28–60 days (1–2 B2B sales cycles). *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: CRM hygiene and ICP alignment ensure reps work real deals, while AE product discovery and pricing close the contract.
