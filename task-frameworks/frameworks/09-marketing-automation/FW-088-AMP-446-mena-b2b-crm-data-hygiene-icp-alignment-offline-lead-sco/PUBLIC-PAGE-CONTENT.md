# MENA B2B CRM Data Hygiene, ICP Alignment & Offline Lead-Scoring Feedback Framework
## <span dir="rtl">الإطار التشغيلي لتنظيف بيانات `CRM` ومواءمة معايير العميل المثالي (`ICP`) بين التسويق والمبيعات في قطاع الأعمال (`B2B`)</span>

> **Asset ID**: `FW-088` (`AMP-446`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Marketing Automation | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Clean duplicate/malformed Arabic-English CRM records, lock a shared Sales-Marketing Ideal Customer Profile (`ICP`), and feed back SQL status to Google/Meta/LinkedIn so AI lead-generation automation scales revenue instead of amplifying dirty data.
- **AR**: <span dir="rtl">تنظيف سجلات `CRM` المكررة والمشوهة (بين العربية والإنجليزية)، وتوحيد تعريف «العميل المؤهل `MQL/SQL`» بين التسويق والمبيعات، وتغذية المنصات الإعلانية بالصفقات الحقيقية لمنع أتمتة الفوضى.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before deploying AI lead scoring, automated SDR sequences, or value-based lead bidding (`AMP-069`) for B2B, SaaS, real estate, industrial, or healthcare enterprises in MENA.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل تشغيل أنظمة تقييم العملاء المحتملين بالذكاء الاصطناعي (`AI Lead Scoring`) أو أتمتة المبيعات في قطاعات الشركات (`B2B`) والعقارات والحلول التقنية.</span>
- **When NOT to Use It (EN)**: Never automate outbound B2B emails/WhatsApp messages from CRM triggers until duplicate company records, Arabic-Indic phone numbers (`AMP-388`), and non-ICP disqualifiers (`Job Seeker / Student / Vendor`) are scrubbed.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بتفعيل الإرسال الآلي من الـ CRM قبل دمج السجلات المكررة، وتطبيع أرقام الهواتف، وعزل طلبات التوظيف والطلاب والموردين.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- CRM Contact & Company Export (`HubSpot`, `Salesforce`, `Zoho`, `Pipedrive`, `Dynamics 365`)
- Joint Sales + Marketing Signed ICP Charter (`Minimum Company Size, Commercial Registration / CR presence, Target Geography, Budget Floor`)
- Google Ads `GCLID` / Meta `Lead_ID` Offline Conversion Import integration

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Company**: Riyadh, Dubai & Cairo B2B Logistics & Warehouse Management SaaS (`Average Annual Contract: $14,000`).
- **Problem**: Marketing celebrated generating `1,200` 'AI-scored leads' in Q3, but Sales closed only `6` deals (`0.5%` close rate) and complained that `78%` of leads were truck drivers looking for jobs (`"وظائف سائق"`), university students, or duplicate entries of existing clients.

### Step B: Initial Output (`المخرج الأولي`)
- **Executed 4-Stage Overhaul**:
  1. De-duplicated `14,800` CRM contacts via E.164 phone normalization (`AMP-388`) and bilingual company matching (merged `2,310` duplicate Arabic/English records).
  2. Added the `Inquiry Purpose` (`شراء النظام لشركتي` vs. `التقديم على وظيفة`) routing gate + Arabic morphological negative keywords (`AMP-066`).
  3. Connected HubSpot `Lifecycle Stage == SQL` webhook to Google Ads and Meta CAPI.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Pragmatic MENA SME Email Rule**: Note that in Egypt and KSA, many legitimate traditional wholesale/retail business owners (`أصحاب مؤسسات تجارية حقيقية`) still use a personal `@gmail.com` or `@hotmail.com` address while conducting business on WhatsApp—so instead of hard-blocking `@gmail.com`, required **`اسم المؤسسة/المتجر + عدد الفروع + رقم جوال موثق`** to qualify them!
2. **Enforced 10-Minute Speed-to-Lead SLA on `Score >= 60` SQLs**: Routed verified `SQL` leads directly to the regional AE's WhatsApp/Phone queue within 60 seconds.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Raw junk lead volume dropped by `64%`, Sales rep time wasted on job seekers fell to `0%`, and MQL-to-SQL conversion rate rose from `9%` to **`38%`**.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A Western B2B lead-scoring template automatically disqualifies (`-100 pts`) any lead submitting a `@gmail.com` or `@yahoo.com` email address; in Egypt and Saudi Arabia, this blocks 40%+ of profitable traditional family trading companies, clinics, and retail store owners who do not use corporate email daily.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: In MENA B2B scoring, **do not auto-reject `@gmail.com` if the user provides a valid local mobile number (`+9665...` / `+201...`), a real store/establishment name (`اسم المنشأة أو المتجر`), and qualifying branch/employee count**!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **HubSpot / Salesforce Offline Conversion Sync to Google Ads (`GCLID`) & Meta CAPI for Leads** | `supported` | [Official Docs](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) (`2026-10-25`) | Passing CRM-qualified lead stages (`MQL/SQL`) back to Google Ads and Meta prevents automated bidding from optimizing toward cheap unqualified form-fills. | If real-time CRM API sync is unavailable, upload a weekly CSV of `GCLID` + SHA-256 hashed `email`/`phone` for qualified SQLs. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: MQL-to-SQL Acceptance Rate by Sales (`Target: >= 35%`), CRM Duplicate Contact Rate (`Target: < 1%`), and Cost per Closed-Won Deal.
- **Baseline**: Prior quarter raw Lead-to-SQL conversion rate and duplicate record audit.
- **Observation Window**: 28–60 days (1–2 B2B sales cycles).
- **Interpretation Boundary**: CRM hygiene and ICP alignment ensure reps work real deals, while AE product discovery and pricing close the contract.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Google Ads Channel Priority, Lead Scoring and a February 2027 Display Change: A Checklist for Arab Advertisers](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) — *VOCTOS* (Published `2026-10-16`, Accessed `2026-10-25`): Documents Google Ads Oct 2026 channel priority changes, offline lead-scoring requirements, and the Feb 2027 removal of current Display spend allocation controls on Search campaigns.
- [Lead Generation Benchmarks in Egypt](https://23hublab.com/lead-generation-benchmarks-in-egypt/) — *23HubLab* (Published `2026-05-12`, Accessed `2026-10-25`): LinkedIn B2B leads in Egypt convert to meetings at 25-40% vs 8-18% for Meta lead forms; structured lead nurturing lifts 12-month conversion by 20-40%.
- [Common Mistakes When Using AI in B2B Sales and Marketing](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) — *Founderz* (Published `2026-08-15`, Accessed `2026-10-25`): Automating B2B outreach and lead generation on top of uncleaned CRM data or without sales-marketing ICP alignment amplifies errors and lengthens the sales cycle.
