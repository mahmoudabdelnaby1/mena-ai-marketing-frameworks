# FW-039: Arabic Grammatical Gender-Targeting & Dual/Plural Morphology Prompt Template
## قالب ضبط المخاطب النحوي والتأنيث والتذكير في النصوص التسويقية العربية (تجاوز حيادية الضمير الإنجليزي `You`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-192`, `AMP-202`, `AMP-212`, `AMP-222`
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent English-sourced prompts from defaulting to masculine-only Arabic verbs (`اشترِ الآن / استمتع`) when addressing female shoppers (`اشترِي الآن / استمتعي / لكِ`) in beauty, modest fashion, jewelry, and maternal categories.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع البرومبتات المترجمة من الإنجليزية (`You`) من مخاطبة الجمهور النسائي بصيغة المذكر المفرد (`اشترِ / استمتع / لكَ`) وضبط تصريف الأفعال والضمائر والصفات للمؤنث (`اشترِي / استمتعي / لكِ`) أو الصيغة المحايدة.
- **Why `PROMPT_TEMPLATE` Fits This User Job (EN)**: Because English `'you'` is gender-neutral, LLMs translating or generating from English briefs default to the Arabic 2nd-person masculine singular (`أنتَ / اكتشف / احصل`), alienating female buyers in cosmetics, abayas, bridal, and mom-and-baby verticals; a grammatical-gender PROMPT_TEMPLATE locks verb and pronoun inflection.
- **لماذا يناسب شكل `PROMPT_TEMPLATE` هذه المهمة (AR)**: بسبب حيادية الضمير الإنجليزي (`You`)، تميل النماذج اللغوية افتراضياً إلى صيغة المفرد المذكر (`أنتَ / اكتشف / احصل`) حتى في إعلانات العبايات والتجميل والعناية بالأم؛ لذا يفرض هذا القالب تصريفاً نحوياً دقيقاً للمؤنث أو الصيغة الشاملة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever generating Arabic ad copy, push notifications, app UI, email lifecycle flows, or product descriptions where audience gender is predominantly female, predominantly male, or mixed.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند كتابة الإعلانات أو إشعارات التطبيقات أو رسائل البريد أو أوصاف المنتجات الموجهة لجمهور نسائي أو رجالي أو مختلط.
- **When NOT to Use It (EN)**: Do not use awkward slash notation (`عزيزي/عزيزتي المشترك/ـة`) in social media ads or push notifications—choose either the specific audience gender inflection or clean gender-inclusive noun phrasing (`نرحب بكم` / `خطوة واحدة تفصلك عن...`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تستخدم صيغ الشرطة المائلة الركيكة (`عزيزي/عزيزتي العميل/ـة`) في الإعلانات أو الإشعارات؛ اختر إما صيغة المؤنث الصريحة للعلامات النسائية أو الصياغة الشاملة الأنيقة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Audience Gender Profile (`100% Female`, `100% Male`, `Segmented by CRM Gender Field`, or `Mixed/Unknown`)
2. Dialect Track (`Saudi Khaleeji`, `Emirati`, `Egyptian Ammiya`, or `White MSA`)
3. Draft English or Uninflected Copy

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Copy-Ready Grammatical Gender Inflection Prompt & Reference Table

#### 1. Arabic 2nd-Person Inflection Matrix across Registers
| English Neutral Prompt | Masculine Default Trap (`MASCULINE_SINGULAR`) | Explicit Female Target (`FEMININE_SINGULAR — 2nd Person Yaa ي`) | Gender-Safe Inclusive (`UNSEGMENTED / MIXED AUDIENCE`) |
| :--- | :--- | :--- | :--- |
| **"Shop now & discover your glow"** | `تسوّق الآن واكتشف إشراقتك` *(Wrong for women's skincare!)* | **MSA**: `تسوّقي الآن واكتشفي إشراقتكِ`<br>**KSA**: `تسوّقي الحين واكتشفي إشراقتك`<br>**Egypt**: `اطلبي دلوقتي واكتشفي جمالك` | `اكتشفوا سر الإشراقة الطبيعية — للتسوق الآن` / `إشراقة متجددة تبدأ من هنا` |
| **"Are you ready to upgrade your style?"** | `هل أنت مستعد لتجديد إطلالتك؟` | **MSA**: `هل أنتِ مستعدة لتجديد إطلالتكِ؟`<br>**KSA**: `جاهزة تجددين إطلالتك؟`<br>**Egypt**: `جاهزة تجددي إطلالتك؟` | `وقت تجديد الإطلالة بدأ الآن` |
| **"Choose the shade that suits you"** | `اختر الدرجة التي تناسبك` | **MSA**: `اختاري الدرجة التي تناسبكِ`<br>**KSA**: `اختاري الدرجة اللي تناسبك`<br>**Egypt**: `اختاري الدرجة اللي تليق عليكي` | `مجموعة درجات مصممة لتناسب كل بشرة` |

#### 2. Copy-Ready Prompt Template
```xml
<system_role>
You are an Arabic Morphological & Copywriting Specialist.
CRITICAL GRAMMAR RULE: Never default to 2nd-person masculine singular (`أنتَ / افعل`) when translating or drafting from English "you".
</system_role>
<gender_mode>{{MODE: FEMININE_SINGULAR_ANTI | MASCULINE_SINGULAR_ANTA | GENDER_INCLUSIVE_NO_SLASHES | CRM_DYNAMIC_PAIR}}</gender_mode>
<dialect_track>{{DIALECT: SAUDI_KHALEEJI | EGYPTIAN_AMMIYA | WHITE_MSA}}</dialect_track>
<rules>
- If FEMININE_SINGULAR_ANTI: Inflect every 2nd-person imperative verb (`تسوّقي، اختاري، استمتعي، دلّلي، جربي`), active participle (`مستعدة، متألقة، جاهزة`), and pronoun (`أنتِ، لكِ`) strictly in the feminine singular:
  - Note on Dialect Verb Endings: In Saudi Khaleeji present tense use `-ين` (`تختارين، تحبين، تقدرين`); in Egyptian Ammiya and MSA imperative/present subjunctive drop the noon (`تختاري، تحبي، تقدري`).
- If GENDER_INCLUSIVE_NO_SLASHES: Use verbal nouns (المصادر: `التسوق الآن، اختيار المقاس، خطوات الطلب`) or 1st/3rd person hooks so the sentence reads naturally to both men and women with ZERO `/ـة` slashes.
- If CRM_DYNAMIC_PAIR: Output both `"copy_female"` and `"copy_male"` JSON keys for Klaviyo/Braze conditional blocks.
</rules>
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **LLM Arabic Morphological Inflection (Feminine Singular vs. Masculine Default)** | `supported` | [Official Reference](https://f1000research.com/articles/14-694) (`2026-10-25`) | Research on Arabic LLM generation confirms models default to masculine singular when translating English 'you' unless `<gender_mode>` is explicitly specified. | Always pass `<gender_mode>` in every Arabic copywriting prompt. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-192`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Mandatory target-persona grammatical gender field in all Arabic copywriting prompts.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-202`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Mandatory target-persona grammatical gender field in all Arabic copywriting prompts.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-212`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Mandatory target-persona grammatical gender field in all Arabic copywriting prompts.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-222`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Mandatory target-persona grammatical gender field in all Arabic copywriting prompts.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Brand**: Riyadh & Cairo Luxury Abaya & Modest Eveningwear Brand (`100% Female Customer Base`).
- **Broken Masculine AI Push Notification**: `"أهلاً بك! لا تفوت فرصة الحصول على عبايتك المفضلة بخصم 20%، اختر مقاسك الآن وادفع عبر تابي!"` *(Addresses a woman buying an abaya as a man: `لا تفوت / اختر مقاسك / ادفع`!)*
- **Human Review & Key Edits Applied**: 1. **Verified Saudi Present-Tense `-ين` vs Imperative `-ي`**: Checked that negative present (`لا تفوتين` in Khaleeji vs `لا تفوّتي` in MSA and `متفوتيش` in Egyptian) matches native spoken morphology.
2. **Updated App UI Strings**: Audited checkout and push templates (`اشترِي الآن`, `أضيفي للسلة`) across the women's store theme.
- **Final Usable Output**: - All push notifications, cart buttons, and email flows inflected in 100% natural feminine singular across KSA and Egypt.
- **What Can Go Wrong**: A unisex fragrance store sends a single push notification with `'اخترِ/اختاري عطرك/عطركِ المفضل الآن يا عزيزي/عزيزتي'` full of slashes, making the notification look like a government tax form and clipping the preview text.
- **Correction & Fallback**: For unsegmented unisex lists, always use the **`GENDER_INCLUSIVE_NO_SLASHES`** rule (e.g., `'اكتشفوا مجموعتنا الجديدة من العطور الفاخرة — تسوقوا الآن'` or noun-led `'عطر يناسب كل الأوقات — للطلب الآن'`).

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% grammatical gender match rate in pre-send QA and improved Push/Email CTR on female-targeted segments.
- **Baseline Definition**: Audit of existing automated lifecycle messages for masculine-default verb forms.
- **Observation Window**: 14 days post-update. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Grammatical gender accuracy eliminates jarring brand disconnect, while offer timing and segmentation drive conversion volume.
