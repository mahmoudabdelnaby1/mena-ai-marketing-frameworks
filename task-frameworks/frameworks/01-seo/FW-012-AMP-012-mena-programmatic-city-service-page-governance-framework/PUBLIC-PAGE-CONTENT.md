# MENA Programmatic City/Service Page Governance Framework (Anti-Scaled Content Abuse)
## <span dir="rtl">الإطار التشغيلي لحوكمة صفحات المدن والخدمات المولدة برمجياً (تجنب عقوبة `Scaled Content Abuse` في جوجل)</span>

> **Asset ID**: `FW-012` (`AMP-012`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Search Engine Optimization (SEO) | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Decide which regional city/service landing pages deserve standalone URLs and enforce unique local proof requirements so AI page generation never triggers Google's Scaled Content Abuse penalty.
- **AR**: <span dir="rtl">تحديد صفحات المدن والخدمات التي تستحق روابط مستقلة وإلزامها ببيانات محلية حقيقية (الرياض، جدة، الدمام، القاهرة، دبي) لمنع الوقوع تحت طائلة سياسة المحتوى المضخم (`Scaled Content Abuse`) في جوجل.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before launching multi-city or multi-category SEO landing pages across KSA (Riyadh, Jeddah, Dammam/Khobar), UAE (Dubai, Abu Dhabi, Sharjah), or Egypt (Cairo, New Cairo, Sheikh Zayed, Alexandria).
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم قبل إطلاق صفحات هبوط متعددة المدن أو الفئات في السعودية (الرياض، جدة، الدمام/الخبر) أو الإمارات (دبي، أبوظبي، الشارقة) أو مصر (القاهرة، التجمع، الشيخ زايد، الإسكندرية).</span>
- **When NOT to Use It (EN)**: Do not generate a standalone city URL if your business has zero distinct operational data (no specific delivery SLA, shipping cost, physical branch, local portfolio, or regulatory license) for that city.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بإنشاء صفحة مستقلة لمدينة ليس لديك فيها أي بيانات تشغيلية حقيقية مميزة (مثل مدة التوصيل، تكلفة الشحن، فرع فعلي، أو مشاريع منفذة في تلك المدينة).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- First-Party Operational Matrix per City (actual branch address, delivery SLA, shipping fee, local municipal/regulatory permit, local project examples)
- City-Specific Demand & Persona Matrix (e.g., Riyadh enterprise/government focus vs. Jeddah retail/tourism vs. Dammam industrial/B2B)
- Google Search Console query data confirming distinct city-modifier search demand

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Business**: B2B Commercial HVAC Maintenance & Smart Cooling Provider in Saudi Arabia.
- **Proposed AI Plan**: An agency proposed generating 60 city pages (`شركة صيانة تكييف في [المدينة]`) using a single ChatGPT template with only the city name swapped.

### Step B: Initial Output (`المخرج الأولي`)
- **Gate 1 Audit of the 60 Proposed Cities**:
  - **Approved for Standalone Pages (`3` Hubs)**: Riyadh (`/ar/hvac-maintenance-riyadh`), Jeddah (`/ar/hvac-maintenance-jeddah`), Dammam/Khobar (`/ar/hvac-maintenance-dammam`) — where the company has field engineers, distinct SLA tables (4-hour emergency response), and real client projects.
  - **Blocked / Consolidated (`57` Minor Towns)**: Consolidated into a single interactive coverage & dispatch SLA table on the main service page (`0` thin doorway pages created).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Persona Differentiation**: Rewrote the Riyadh page around commercial towers and server-room precision cooling (`تبريد غرف السيرفرات والأبراج الإدارية بالرياض`), Jeddah around high-humidity coastal corrosion protection (`حماية وحدات التكييف من الرطوبة والأملاح في جدة`), and Dammam around industrial warehouse chillers (`صيانة الشيلرات المركزية للمصانع والمستودعات بالدمام والجبيل`).
2. **Shingle Check**: Verified 5-gram overlap between Riyadh, Jeddah, and Dammam pages dropped from `94%` (agency draft) to **`14%`**.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Published 3 deeply differentiated regional hub pages with verified local SLAs, engineering specs, and `LocalBusiness` JSON-LD instead of 60 thin doorway pages.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A site publishes 200 AI-spun neighborhood pages (`سباك في حي الملز`, `سباك في حي النرجس`...) with identical text; Google classifies the directory under Scaled Content Abuse and deindexes the entire `/services/` subfolder.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Immediately return `410 Gone` (or `301` redirect to the 1–3 genuine city hubs) for all thin swapped-keyword pages, consolidate neighborhood coverage into a structured table on the parent city page, and submit a reconsideration/recrawl request.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Google Search Spam Policies — Scaled Content Abuse (March 2024 / 2026 Guidance)** | `supported` | [Official Docs](https://developers.google.com/search/docs/fundamentals/using-gen-ai-content) (`2026-10-25`) | Google's official policy is method-agnostic: it does not penalize AI assistance per se (`AMP-556`), but strictly penalizes generating many pages without original value or distinct user utility. | Never create a standalone URL unless at least 3 first-party city-specific data points exist. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Indexation rate (`Indexed / Submitted`) of published city hubs in GSC and organic qualified lead conversions per city page.
- **Baseline**: Ratio of `Crawled - currently not indexed` pages in GSC.
- **Observation Window**: 28–45 days post-publication.
- **Interpretation Boundary**: Consolidating doorway pages protects site-wide crawl equity and compliance, though ranking in competitive local packs also requires verified Google Business Profiles.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Google Search's Guidance on Generative AI Content on Your Website](https://developers.google.com/search/docs/fundamentals/using-gen-ai-content) — *Google Search Central* (Published `2026-10-01`, Accessed `2026-10-25`): Google evaluates content quality/helpfulness regardless of AI vs human authorship; using AI to generate many pages without added value violates Scaled Content Abuse.
- [Spam Policies for Google Web Search | Documentation](https://developers.google.com/search/docs/essentials/spam-policies) — *Google Search Central* (Published `2026-08-28`, Accessed `2026-10-25`): Defines Scaled Content Abuse as generating many pages primarily to manipulate rankings or generative AI responses rather than helping users.
- [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) — *DigiStreet Media* (Published `2026-09-29`, Accessed `2026-10-25`): Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous.
