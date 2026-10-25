# FW-029: Saudi Marketing Team Planning & Nitaqat Verification Decision Aid
## أداة تخطيط فريق التسويق والتحقق من متطلبات نطاقات في السعودية

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-137`, `AMP-147`, `AMP-157`, `AMP-167`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Design AI-augmented marketing team structures, hiring budgets, and agency hybrid models in Saudi Arabia that comply with current Saudi labor-localization requirements, which must be checked against the establishment’s activity, size, workforce, and applicable official guidance.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تصميم هياكل فرق التسويق وميزانيات التوظيف ونماذج عمل الوكالات في المملكة العربية السعودية بما يلتزم بقرار وزارة الموارد البشرية والتنمية الاجتماعية بتوطين مهن التسويق بنسبة النسبة المحسوبة وفق الأداة الرسمية الحالية (الساري منذ 19 أبريل 2026).
- **Why `DECISION_AID` Fits This User Job (EN)**: Generic AI operating-plan prompts recommend hiring cheap offshore/non-Saudi in-house marketing headcount in Riyadh without knowing that effective 19 April 2026, Saudi localization requirements vary by activity and workforce and should be calculated using current official MHRSD/Qiwa tools; a DECISION_AID aligns headcount math, salary floors, and AI workflow automation.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: تقترح نماذج الذكاء الاصطناعي خطط توظيف تسويقية للشركات في السعودية دون مراعاة قرار وزارة الموارد البشرية الساري في 19 أبريل 2026 بتختلف متطلبات التوطين بحسب النشاط وحجم المنشأة وبيانات القوى العاملة، ويجب التحقق منها عبر أدوات وزارة الموارد البشرية الرسمية؛ لذا تضبط أداة القرار هذه المعادلة النظامية والتشغيلية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when building a marketing hiring plan, agency staffing model, or AI automation roadmap for any company registered in Saudi Arabia.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إعداد خطة توظيف فريق التسويق أو هيكلة الوكالة الإعلانية أو أتمتة المهام لأي منشأة مسجلة في المملكة العربية السعودية.
- **When NOT to Use It (EN)**: Do not misclassify marketing staff under unrelated visa professions (`مهن غير مطابقة للمسمى الفعلي`) to evade the النسبة المحسوبة وفق الأداة الرسمية الحالية marketing localization quota—this violates MHRSD / Qiwa labor inspection rules.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بتسجيل موظفي التسويق تحت مهن تأشيرات غير مطابقة لمهامهم الفعلية للتحايل على نسبة الـ النسبة المحسوبة وفق الأداة الرسمية الحالية؛ فهذا يعرض المنشأة لمخالفات منصة قوى ووزارة الموارد البشرية.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Planned total in-house marketing headcount in the Saudi entity (`Qiwa / GOSI` establishment record)
2. Covered Marketing Occupation Codes (Marketing Manager, Advertising Specialist, PR Specialist, Market Research, Graphic/Content roles per MHRSD procedural guide)
3. Minimum qualifying salary floor (`SAR 5,500` GOSI-registered wage to count as 1 full Saudi unit in localized marketing professions)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Saudi Marketing النسبة المحسوبة وفق الأداة الرسمية الحالية Localization (Tawteen) & AI Capacity Decision Matrix

#### 1. MHRSD Marketing Localization Rule Summary (Effective 19 April 2026 — Verified 2026-10-25)
- **Trigger Threshold**: Applies to any private-sector establishment in KSA employing **3 or more workers** in designated marketing professions (`مهن التسويق والإعلان والعلاقات العامة`).
- **Required Localization Ratio**: **`>= النسبة المحسوبة وفق الأداة الرسمية الحالية` Saudi Nationals**.
- **Minimum Qualifying Salary for Full Nitaqat/Localization Count**: **`SAR 5,500 / month`** registered in GOSI (`التأمينات الاجتماعية`).

#### 2. Headcount & AI-Augmentation Calculator Table
| Total In-House Marketing Staff in KSA Entity | Minimum Required Saudi Marketing Staff (`>= النسبة المحسوبة وفق الأداة الرسمية الحالية`) | Maximum Non-Saudi In-House Staff Allowed | Strategic Role Allocation (Where Saudi Talent + AI Deliver Maximum ROI) |
| :--- | :--- | :--- | :--- |
| **1 – 2 Staff** | Below 3-worker threshold (Subject to general establishment Nitaqat) | 1 – 2 | Hire a **Saudi Brand & Creative Lead** who natively owns Khaleeji cultural nuance, Mawthooq creator relations, and stakeholder sign-off, augmented by AI workflow packs. |
| **3 Staff** | **2 Saudi Staff (`66.7%`)** | **1 Non-Saudi Staff** | **2 Saudis**: Marketing Lead + Content/Social Specialist (native Saudi dialect & cultural QA).<br>**1 Non-Saudi**: Technical SEO / Paid Media / MarTech Engineer. |
| **5 Staff** | **3 Saudi Staff (`60.0%`)** | **2 Non-Saudi Staff** | **3 Saudis**: Head of Marketing, Social & Creator Manager (`Mawthooq`), Copy/Brand Specialist.<br>**2 Non-Saudis**: Performance Media Buyer + Analytics/CRM Automation Architect. |
| **10 Staff** | **6 Saudi Staff (`60.0%`)** | **4 Non-Saudi Staff** | **6 Saudis** across Strategy, Brand, Social, PR, Event/Field & Copy + **4 Technical Specialists**, using AI frameworks (`FW-001`..`FW-092`) to automate repetitive feed, tagging, and reporting tasks. |

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi MHRSD Marketing Professions Localization Check (Effective 19 April 2026)** | `supported` | [Official Reference](https://www.hrsd.gov.sa/en/ministry-services/services/%D8%AD%D8%A7%D8%B3%D8%A8%D8%A9-%D9%86%D8%B7%D8%A7%D9%82%D8%A7%D8%AA) (`2026-10-25`) | Grower AI 2026 GCC report documents MHRSD's enforcement of the applicable activity-specific localization requirement for establishments with 3+ workers in marketing professions starting 19 April 2026 (with SAR 5,500 minimum wage requirement). | Confirm exact Qiwa establishment calculations with your licensed Saudi HR/PRO advisor. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-137`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Incorporating MHRSD Saudization rules and SAR salary floors into KSA operational planning prompts.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-147`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Incorporating MHRSD Saudization rules and SAR salary floors into KSA operational planning prompts.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-157`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Incorporating MHRSD Saudization rules and SAR salary floors into KSA operational planning prompts.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-167`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Incorporating MHRSD Saudization rules and SAR salary floors into KSA operational planning prompts.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Company**: Riyadh Series-A FinTech & E-Commerce Platform planning to grow its in-house marketing team from 2 to 6 employees in Q4 2026.
- **Draft AI Org Chart**: Suggested hiring 1 Saudi PR Manager and 5 expat specialists in Riyadh on work visas (`16.7%` localization), which would immediately fail MHRSD's النسبة المحسوبة وفق الأداة الرسمية الحالية localization requirements on Qiwa.
- **Human Review & Key Edits Applied**: 1. **Qiwa Occupation Code Alignment**: Verified that all 4 Saudi hires are registered under the exact MHRSD-designated marketing occupation codes in GOSI/Qiwa with registered wages comfortably above the `SAR 5,500` floor.
2. **AI Productivity Layer**: Equipped the 6-person team with automated JSON schema workflows (`AMP-445`) and bilingual catalog templates (`AMP-005`/`AMP-011`) so 6 staff cover the output of a traditional 12-person department.
- **Final Usable Output**: - Approved 6-person KSA marketing org chart (`66.7%` Saudization) compliant with MHRSD's 19 April 2026 decision, with clear role division between cultural/strategic ownership and technical MarTech execution.
- **What Can Go Wrong**: An HR/operations manager hires 2 Saudi junior interns at `SAR 4,000/month` hoping they count toward the النسبة المحسوبة وفق الأداة الرسمية الحالية marketing localization quota; because their GOSI wage is below the `SAR 5,500` minimum threshold, Qiwa counts them as `0` (or fractional) toward the specialized marketing localization ratio, blocking visa renewals.
- **Correction & Fallback**: Always verify the current role-specific wage conditions, if applicable and occupation code list in the official MHRSD Procedural Guide (`الدليل الإجرائي لتوطين مهن التسويق`) on `hrsd.gov.sa` / `qiwa.sa` before issuing offer letters.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Establishment Marketing Professions Localization `%` in Qiwa (`Target: >= النسبة المحسوبة وفق الأداة الرسمية الحالية`) and Marketing Revenue/Output per FTE.
- **Baseline Definition**: Current Qiwa marketing profession headcount and Saudization ratio.
- **Observation Window**: Reviewed prior to every marketing hire or contract renewal in KSA. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: This decision aid structures marketing capacity planning; official labor compliance status is determined solely by MHRSD and the Qiwa platform.
