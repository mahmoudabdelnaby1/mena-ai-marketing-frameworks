# Arabic Grammatical Gender-Targeting & Dual/Plural Morphology Prompt Template
## <span dir="rtl">قالب ضبط المخاطب النحوي والتأنيث والتذكير في النصوص التسويقية العربية (تجاوز حيادية الضمير الإنجليزي `You`)</span>

> **Asset ID**: `FW-039` (`AMP-182`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Content Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent English-sourced prompts from defaulting to masculine-only Arabic verbs (`اشترِ الآن / استمتع`) when addressing female shoppers (`اشترِي الآن / استمتعي / لكِ`) in beauty, modest fashion, jewelry, and maternal categories.
- **AR**: <span dir="rtl">منع البرومبتات المترجمة من الإنجليزية (`You`) من مخاطبة الجمهور النسائي بصيغة المذكر المفرد (`اشترِ / استمتع / لكَ`) وضبط تصريف الأفعال والضمائر والصفات للمؤنث (`اشترِي / استمتعي / لكِ`) أو الصيغة المحايدة.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever generating Arabic ad copy, push notifications, app UI, email lifecycle flows, or product descriptions where audience gender is predominantly female, predominantly male, or mixed.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند كتابة الإعلانات أو إشعارات التطبيقات أو رسائل البريد أو أوصاف المنتجات الموجهة لجمهور نسائي أو رجالي أو مختلط.</span>
- **When NOT to Use It (EN)**: Do not use awkward slash notation (`عزيزي/عزيزتي المشترك/ـة`) in social media ads or push notifications—choose either the specific audience gender inflection or clean gender-inclusive noun phrasing (`نرحب بكم` / `خطوة واحدة تفصلك عن...`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تستخدم صيغ الشرطة المائلة الركيكة (`عزيزي/عزيزتي العميل/ـة`) في الإعلانات أو الإشعارات؛ اختر إما صيغة المؤنث الصريحة للعلامات النسائية أو الصياغة الشاملة الأنيقة.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Audience Gender Profile (`100% Female`, `100% Male`, `Segmented by CRM Gender Field`, or `Mixed/Unknown`)
- Dialect Track (`Saudi Khaleeji`, `Emirati`, `Egyptian Ammiya`, or `White MSA`)
- Draft English or Uninflected Copy

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Brand**: Riyadh & Cairo Luxury Abaya & Modest Eveningwear Brand (`100% Female Customer Base`).
- **Broken Masculine AI Push Notification**: `"أهلاً بك! لا تفوت فرصة الحصول على عبايتك المفضلة بخصم 20%، اختر مقاسك الآن وادفع عبر تابي!"` *(Addresses a woman buying an abaya as a man: `لا تفوت / اختر مقاسك / ادفع`!)*

### Step B: Initial Output (`المخرج الأولي`)
- **Corrected `FEMININE_SINGULAR_ANTI` Outputs**:
  - **Saudi Khaleeji Version**: `"حياكِ الله! لا تفوتين فرصة اقتناء عبايتك المفضلة بخصم 20% ✨ اختاري مقاسك الحين وقسّميها على 4 دفعات مع تابي."`
  - **Egyptian Ammiya Version**: `"أهلاً بيكي! متفوتيش فرصة اختيار عبايتك المفضلة بخصم 20% ✨ اختاري مقاسك دلوقتي وقسطيها براحتك."`
  - **White MSA Version**: `"أهلاً بكِ! لا تفوّتي فرصة التألق بعبايتكِ المفضلة بخصم 20% — اختاري مقاسكِ الآن بالتقسيط المريح."`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified Saudi Present-Tense `-ين` vs Imperative `-ي`**: Checked that negative present (`لا تفوتين` in Khaleeji vs `لا تفوّتي` in MSA and `متفوتيش` in Egyptian) matches native spoken morphology.
2. **Updated App UI Strings**: Audited checkout and push templates (`اشترِي الآن`, `أضيفي للسلة`) across the women's store theme.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- All push notifications, cart buttons, and email flows inflected in 100% natural feminine singular across KSA and Egypt.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A unisex fragrance store sends a single push notification with `'اخترِ/اختاري عطرك/عطركِ المفضل الآن يا عزيزي/عزيزتي'` full of slashes, making the notification look like a government tax form and clipping the preview text.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: For unsegmented unisex lists, always use the **`GENDER_INCLUSIVE_NO_SLASHES`** rule (e.g., `'اكتشفوا مجموعتنا الجديدة من العطور الفاخرة — تسوقوا الآن'` or noun-led `'عطر يناسب كل الأوقات — للطلب الآن'`).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **LLM Arabic Morphological Inflection (Feminine Singular vs. Masculine Default)** | `supported` | [Official Docs](https://f1000research.com/articles/14-694) (`2026-10-25`) | Research on Arabic LLM generation confirms models default to masculine singular when translating English 'you' unless `<gender_mode>` is explicitly specified. | Always pass `<gender_mode>` in every Arabic copywriting prompt. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% grammatical gender match rate in pre-send QA and improved Push/Email CTR on female-targeted segments.
- **Baseline**: Audit of existing automated lifecycle messages for masculine-default verb forms.
- **Observation Window**: 14 days post-update.
- **Interpretation Boundary**: Grammatical gender accuracy eliminates jarring brand disconnect, while offer timing and segmentation drive conversion volume.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) — *F1000Research* (Published `2025-07-16`, Accessed `2026-10-25`): Demonstrates measurable accuracy drops and cultural/idiomatic errors when LLMs translate between English and regional Arabic dialects.
- [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) — *Locstars* (Published `2026-10-22`, Accessed `2026-10-25`): Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms.
