# FW-012: MENA Programmatic City/Service Page Governance Framework (Anti-Scaled Content Abuse)
## الإطار التشغيلي لحوكمة صفحات المدن والخدمات المولدة برمجياً (تجنب عقوبة `Scaled Content Abuse` في جوجل)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-024`, `AMP-036`, `AMP-048`, `AMP-060`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Decide which regional city/service landing pages deserve standalone URLs and enforce unique local proof requirements so AI page generation never triggers Google's Scaled Content Abuse penalty.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تحديد صفحات المدن والخدمات التي تستحق روابط مستقلة وإلزامها ببيانات محلية حقيقية (الرياض، جدة، الدمام، القاهرة، دبي) لمنع الوقوع تحت طائلة سياسة المحتوى المضخم (`Scaled Content Abuse`) في جوجل.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Spinning up hundreds of near-identical city/service pages by swapping `'الرياض'` with `'جدة'` or `'القاهرة'` is an operational governance failure that violates Google's Scaled Content Abuse policy; an OPERATING_FRAMEWORK with hard uniqueness gates prevents site-wide manual or algorithmic demotion.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: توليد مئات الصفحات المتطابقة عبر استبدال اسم المدينة فقط («شركة تنظيف بالرياض» / «بجدة» / «بالدمام») يعرّض الموقع لعقوبة `Scaled Content Abuse` من جوجل؛ لذا يفرض هذا الإطار التشغيلي بوابات تحقق صارمة قبل النشر.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before launching multi-city or multi-category SEO landing pages across KSA (Riyadh, Jeddah, Dammam/Khobar), UAE (Dubai, Abu Dhabi, Sharjah), or Egypt (Cairo, New Cairo, Sheikh Zayed, Alexandria).
- **متى تستخدم هذه الأداة (AR)**: يُستخدم قبل إطلاق صفحات هبوط متعددة المدن أو الفئات في السعودية (الرياض، جدة، الدمام/الخبر) أو الإمارات (دبي، أبوظبي، الشارقة) أو مصر (القاهرة، التجمع، الشيخ زايد، الإسكندرية).
- **When NOT to Use It (EN)**: Do not generate a standalone city URL if your business has zero distinct operational data (no specific delivery SLA, shipping cost, physical branch, local portfolio, or regulatory license) for that city.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بإنشاء صفحة مستقلة لمدينة ليس لديك فيها أي بيانات تشغيلية حقيقية مميزة (مثل مدة التوصيل، تكلفة الشحن، فرع فعلي، أو مشاريع منفذة في تلك المدينة).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. First-Party Operational Matrix per City (actual branch address, delivery SLA, shipping fee, local municipal/regulatory permit, local project examples)
2. City-Specific Demand & Persona Matrix (e.g., Riyadh enterprise/government focus vs. Jeddah retail/tourism vs. Dammam industrial/B2B)
3. Google Search Console query data confirming distinct city-modifier search demand

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Programmatic Geo-Page Governance & Anti-Spam Gate Framework

#### Gate 1: The "3 First-Party Differentiators" Eligibility Test (Kill or Build)
Before generating any `/city-service` page, score the target city against these 5 first-party data points. **If fewer than 3 are present, DO NOT create a standalone URL (consolidate into a regional table on the main service page instead)**:
1. **Verified Physical Presence or Dedicated Service Zone**: Exact district coverage (e.g., Riyadh: Al Olaya, Al Malqa, Al Narjis; Cairo: New Cairo, Maadi, 6th of October) + real Google Business Profile or warehouse hub.
2. **City-Specific Pricing / Delivery SLA Table**: Real shipping cost (`SAR`/`AED`/`EGP`), same-day vs. 48-hour courier SLA, and payment availability (e.g., COD availability by governorate).
3. **City-Specific Sector & Persona Framing**:
   - *Riyadh*: Government entities, Vision 2030 mega-projects, corporate headquarters, formal B2B procurement.
   - *Jeddah*: Commercial retail, hospitality, Red Sea logistics, family lifestyle.
   - *Dammam / Eastern Province*: Energy, industrial logistics, B2B supply chain, Bahrain cross-border proximity.
   - *Cairo vs. Alexandria*: Governorate-specific courier zones and local landmarks.
4. **Authentic Local Proof**: At least 1 real case study, project count, or verified customer deliveries completed in that city (never fabricated AI testimonials — `AMP-392`).
5. **Local Regulatory / Municipal Context**: Relevant local license or compliance standard (e.g., Balady/Momrah rules in KSA, Dubai Municipality in UAE, New Urban Communities Authority in Egypt).

#### Gate 2: Structural Similarity & Shingle Cap
- Run a 5-gram shingle overlap check across all city pages in the batch:
  - **Hard Ceiling**: Any two city pages sharing **`> 35%` identical sentence/5-gram overlap** are **BLOCKED** from publication.

#### Gate 3: Human Editorial Sign-Off & Batch Throttling
- Publish in human-reviewed waves of `<= 10` pages at a time, monitoring GSC `Crawled - currently not indexed` before expanding.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Google Search Spam Policies — Scaled Content Abuse (March 2024 / 2026 Guidance)** | `supported` | [Official Reference](https://developers.google.com/search/docs/fundamentals/using-gen-ai-content) (`2026-10-25`) | Google's official policy is method-agnostic: it does not penalize AI assistance per se (`AMP-556`), but strictly penalizes generating many pages without original value or distinct user utility. | Never create a standalone URL unless at least 3 first-party city-specific data points exist. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-024`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Programmatic pages backed by genuinely distinct city-level inventory, pricing, branch data, and regulatory specifics.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-036`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Programmatic pages backed by genuinely distinct city-level inventory, pricing, branch data, and regulatory specifics.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-048`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Programmatic pages backed by genuinely distinct city-level inventory, pricing, branch data, and regulatory specifics.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-060`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Programmatic pages backed by genuinely distinct city-level inventory, pricing, branch data, and regulatory specifics.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-502`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-012 (Search Engine Optimization (SEO))`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Business**: B2B Commercial HVAC Maintenance & Smart Cooling Provider in Saudi Arabia.
- **Proposed AI Plan**: An agency proposed generating 60 city pages (`شركة صيانة تكييف في [المدينة]`) using a single ChatGPT template with only the city name swapped.
- **Human Review & Key Edits Applied**: 1. **Persona Differentiation**: Rewrote the Riyadh page around commercial towers and server-room precision cooling (`تبريد غرف السيرفرات والأبراج الإدارية بالرياض`), Jeddah around high-humidity coastal corrosion protection (`حماية وحدات التكييف من الرطوبة والأملاح في جدة`), and Dammam around industrial warehouse chillers (`صيانة الشيلرات المركزية للمصانع والمستودعات بالدمام والجبيل`).
2. **Shingle Check**: Verified 5-gram overlap between Riyadh, Jeddah, and Dammam pages dropped from `94%` (agency draft) to **`14%`**.
- **Final Usable Output**: - Published 3 deeply differentiated regional hub pages with verified local SLAs, engineering specs, and `LocalBusiness` JSON-LD instead of 60 thin doorway pages.
- **What Can Go Wrong**: A site publishes 200 AI-spun neighborhood pages (`سباك في حي الملز`, `سباك في حي النرجس`...) with identical text; Google classifies the directory under Scaled Content Abuse and deindexes the entire `/services/` subfolder.
- **Correction & Fallback**: Immediately return `410 Gone` (or `301` redirect to the 1–3 genuine city hubs) for all thin swapped-keyword pages, consolidate neighborhood coverage into a structured table on the parent city page, and submit a reconsideration/recrawl request.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Indexation rate (`Indexed / Submitted`) of published city hubs in GSC and organic qualified lead conversions per city page.
- **Baseline Definition**: Ratio of `Crawled - currently not indexed` pages in GSC.
- **Observation Window**: 28–45 days post-publication. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Consolidating doorway pages protects site-wide crawl equity and compliance, though ranking in competitive local packs also requires verified Google Business Profiles.
