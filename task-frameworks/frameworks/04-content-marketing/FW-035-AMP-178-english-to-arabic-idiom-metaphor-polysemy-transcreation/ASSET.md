# FW-035: English-to-Arabic Idiom, Metaphor & Polysemy Transcreation Checklist
## قائمة فحص التعريب الإبداعي (`Transcreation`) ومنع الترجمة الحرفية للتعبيرات الاصطلاحية والمشتركات اللفظية

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-188`, `AMP-198`, `AMP-208`, `AMP-218`, `AMP-228`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Replace awkward literal English idiom calques (`'بدون كسر البنك'`, `'لعبة مغير'`) and misresolved polysemous words with resonant native Arabic commercial hooks.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: استبدال الترجمات الحرفية الركيكة للتعبيرات الإنجليزية («بدون كسر البنك»، «مغير قواعد اللعبة») والأخطاء الدلالية للمشتركات اللفظية بصياغات عربية أصيلة ومقنعة تجارياً.
- **Why `CHECKLIST` Fits This User Job (EN)**: Direct AI translation of English marketing copy produces jarring idiom calques (`'لا تكسر البنك'` for `'Don't break the bank'`) and wrong polysemy choices (`'سفينة مجانية'` for `'Free shipping'`); a replacement CHECKLIST & glossary catches these errors instantly.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تؤدي الترجمة الآلية المباشرة لنصوص التسويق الإنجليزية إلى تراكيب حرفية هجينة («لا تكسر البنك» لترجمة `Don't break the bank`) أو أخطاء في المشترك اللفظي؛ وتكشف قائمة الفحص هذه تلك الأخطاء وتستبدلها فوراً.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when localizing global brand campaigns, product packaging, app UI strings, or English landing pages into Arabic for MENA.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند تعريب حملات العلامات التجارية العالمية أو واجهات التطبيقات أو صفحات الهبوط من الإنجليزية إلى العربية.
- **When NOT to Use It (EN)**: Do not translate English idioms word-for-word even if individual words are grammatically correct in MSA.
- **متى لا تستخدم هذه الأداة (AR)**: لا تترجم الاستعارات والتعبيرات الاصطلاحية الإنجليزية كلمة بكلمة حتى لو بدت الجملة صحيحة نحوياً في الفصحى.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Source English Marketing Copy / UI Strings
2. Target Market (`KSA/GCC` vs `Egypt` vs `Pan-Arab MSA`)
3. Brand Voice Guide

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Forbidden Literal Calques vs. Native Arabic Commercial Transcreation Table

| Source English Marketing Phrase / Polysemous Term | Broken Literal AI Translation (`CALQUE — REJECT`) | Native Saudi / Gulf Transcreation (`APPROVED`) | Native Egyptian Transcreation (`APPROVED`) | Modern White MSA (`APPROVED`) |
| :--- | :--- | :--- | :--- | :--- |
| **"Without breaking the bank"** | `بدون كسر البنك` / `دون تحطيم المصرف` | `بسعر يبيض الوجه وعلى قد الميزانية` | `بسعر على قد الإيد ومن غير ما تضغط ميزانيتك` | `بتكلفة مدروسة تناسب ميزانيتك` |
| **"A total game-changer"** | `مغيّر اللعبة بالكامل` | `نقلة نوعية تفرق معك من أول تجربة` | `هيغير تجربتك 180 درجة من أول يوم` | `معيار جديد يرتقي بتجربتك` |
| **"Steal the spotlight / Steal the show"** | `اسرقي الأضواء / اسرق العرض` | `تفرّدي بحضور يخطف الأنظار` | `اخطف الأنظار في كل مكان` | `حضور لافت يخطف الأنظار` |
| **"No strings attached"** | `بدون أي خيوط مرفقة` | `بدون شروط خفية أو التزامات` | `من غير أي شروط معقدة أو التزام` | `دون التزامات أو شروط مسبقة` |
| **"Free Shipping / Book now / Light texture"** *(Polysemy Traps)* | `سفينة مجانية` / `كتاب الآن` / `ملمس ضوئي` | `شحن مجاني` / `احجز الحين` / `قوام خفيف على البشرة` | `شحن مجاني` / `احجز دلوقتي` / `ملمس خفيف وسريع الامتصاص` | `شحن مجاني` / `احجز الآن` / `قوام خفيف ولطيف` |
| **"Pain points"** | `نقاط الألم الجسدي` (in B2B software copy!) | `التحديات اللي تعطل شغلك` | `المشاكل اللي بتعطل شغلك` | `التحديات التشغيلية التي تواجه فريقك` |

#### Pre-Publish Transcreation QA Checklist
- [ ] **Check 1 — Metaphor Replacement**: Scan the English source for idioms (`break the bank`, `game changer`, `elephant in the room`, `cut corners`, `one-stop shop`, `under the hood`, `bottleneck`) and replace each with the functional Arabic intent before translating.
- [ ] **Check 2 — Short UI String Context Injection**: Never send isolated 1–2 word UI strings (`"Book"`, `"Order"`, `"Free"`, `"Light"`, `"Charge"`, `"Spring"`) to an LLM without passing `"ui_context": "e-commerce checkout button / skincare texture / seasonal collection"`.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **LLM Contextual Transcreation vs. String-by-String MT** | `supported` | [Official Reference](https://locstars.com/ai-translation-errors-arabic/) (`2026-10-25`) | Locstars and 23HubLab localization audits document polysemy and idiom calques as the top cause of unnatural Arabic marketing copy when context is omitted. | Enforce the Idiom & Polysemy Replacement Table prior to publication. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-188`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Transcreation briefs that specify the emotional hook, target dialect, and cultural equivalent rather than source English phrasing.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-198`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Transcreation briefs that specify the emotional hook, target dialect, and cultural equivalent rather than source English phrasing.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-208`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Transcreation briefs that specify the emotional hook, target dialect, and cultural equivalent rather than source English phrasing.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-218`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Transcreation briefs that specify the emotional hook, target dialect, and cultural equivalent rather than source English phrasing.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-228`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Transcreation briefs that specify the emotional hook, target dialect, and cultural equivalent rather than source English phrasing.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-518`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-188 (Content Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Source English Hero Copy (Global SaaS + D2C Launch)**:
  `"Upgrade your workflow without breaking the bank. Our new platform is a game-changer that tackles your biggest pain points with no strings attached. Free trial—book a demo today!"`
- **Human Review & Key Edits Applied**: 1. **Replaced All 5 Calques & Polysemy Errors**: Converted `"بدون كسر البنك"`, `"مغير اللعبة"`, `"نقاط الألم"`, `"بدون خيوط مرفقة"`, and `"كتاب عرض"` into natural executive Arabic.
2. **Created Both GCC White MSA and Egyptian Business Versions**.
- **Final Usable Output**: - **Approved Pan-Arab / GCC Executive Copy**:
  `"طوّر كفاءة أعمالك بتكلفة تناسب ميزانيتك. منصتنا الجديدة تمنح فريقك نقلة نوعية لحل أصعب التحديات التشغيلية دون أي التزامات مسبقة. جرّبها مجاناً واحجز عرضك التوضيحي اليوم!"`
- **What Can Go Wrong**: An app localization pipeline sends a JSON file of raw button labels (`{"cta_1": "Book", "tag_2": "Light", "status_3": "Clear"}`) to an LLM without screen context; the Arabic app ships with `'كتاب'` on the hotel booking button and `'ضوء'` on the low-calorie menu filter.
- **Correction & Fallback**: Always pass `{key, english_text, screen_location, part_of_speech_and_meaning}` in UI localization payloads.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero literal idiom calques or polysemy mistranslations in pre-launch QA and improved landing page scroll-depth / conversion rate.
- **Baseline Definition**: Count of calque/polysemy defects per 1,000 localized words.
- **Observation Window**: Checked per localization batch. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Transcreation removes linguistic friction and builds native trust, while product-market fit drives retention.
