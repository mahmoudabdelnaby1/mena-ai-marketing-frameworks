# English-to-Arabic Idiom, Metaphor & Polysemy Transcreation Checklist
## <span dir="rtl">قائمة فحص التعريب الإبداعي (`Transcreation`) ومنع الترجمة الحرفية للتعبيرات الاصطلاحية والمشتركات اللفظية</span>

> **Asset ID**: `FW-035` (`AMP-178`) | **Artifact Type**: `CHECKLIST` | **Channel**: Content Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Replace awkward literal English idiom calques (`'بدون كسر البنك'`, `'لعبة مغير'`) and misresolved polysemous words with resonant native Arabic commercial hooks.
- **AR**: <span dir="rtl">استبدال الترجمات الحرفية الركيكة للتعبيرات الإنجليزية («بدون كسر البنك»، «مغير قواعد اللعبة») والأخطاء الدلالية للمشتركات اللفظية بصياغات عربية أصيلة ومقنعة تجارياً.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when localizing global brand campaigns, product packaging, app UI strings, or English landing pages into Arabic for MENA.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تعريب حملات العلامات التجارية العالمية أو واجهات التطبيقات أو صفحات الهبوط من الإنجليزية إلى العربية.</span>
- **When NOT to Use It (EN)**: Do not translate English idioms word-for-word even if individual words are grammatically correct in MSA.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تترجم الاستعارات والتعبيرات الاصطلاحية الإنجليزية كلمة بكلمة حتى لو بدت الجملة صحيحة نحوياً في الفصحى.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Source English Marketing Copy / UI Strings
- Target Market (`KSA/GCC` vs `Egypt` vs `Pan-Arab MSA`)
- Brand Voice Guide

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Source English Hero Copy (Global SaaS + D2C Launch)**:
  `"Upgrade your workflow without breaking the bank. Our new platform is a game-changer that tackles your biggest pain points with no strings attached. Free trial—book a demo today!"`

### Step B: Initial Output (`المخرج الأولي`)
- **Literal AI Draft (`REJECTED`)**:
  `"قم بترقية سير عملك بدون كسر البنك. منصتنا الجديدة هي مغير اللعبة الذي يعالج أكبر نقاط الألم لديك بدون خيوط مرفقة. تجربة حرة — كتاب عرض اليوم!"`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Replaced All 5 Calques & Polysemy Errors**: Converted `"بدون كسر البنك"`, `"مغير اللعبة"`, `"نقاط الألم"`, `"بدون خيوط مرفقة"`, and `"كتاب عرض"` into natural executive Arabic.
2. **Created Both GCC White MSA and Egyptian Business Versions**.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **Approved Pan-Arab / GCC Executive Copy**:
  `"طوّر كفاءة أعمالك بتكلفة تناسب ميزانيتك. منصتنا الجديدة تمنح فريقك نقلة نوعية لحل أصعب التحديات التشغيلية دون أي التزامات مسبقة. جرّبها مجاناً واحجز عرضك التوضيحي اليوم!"`

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An app localization pipeline sends a JSON file of raw button labels (`{"cta_1": "Book", "tag_2": "Light", "status_3": "Clear"}`) to an LLM without screen context; the Arabic app ships with `'كتاب'` on the hotel booking button and `'ضوء'` on the low-calorie menu filter.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always pass `{key, english_text, screen_location, part_of_speech_and_meaning}` in UI localization payloads.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **LLM Contextual Transcreation vs. String-by-String MT** | `supported` | [Official Docs](https://locstars.com/ai-translation-errors-arabic/) (`2026-10-25`) | Locstars and 23HubLab localization audits document polysemy and idiom calques as the top cause of unnatural Arabic marketing copy when context is omitted. | Enforce the Idiom & Polysemy Replacement Table prior to publication. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero literal idiom calques or polysemy mistranslations in pre-launch QA and improved landing page scroll-depth / conversion rate.
- **Baseline**: Count of calque/polysemy defects per 1,000 localized words.
- **Observation Window**: Checked per localization batch.
- **Interpretation Boundary**: Transcreation removes linguistic friction and builds native trust, while product-market fit drives retention.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Why Direct Translation Fails in MENA SEO](https://23hublab.com/why-direct-translation-fails-in-mena-seo/) — *23HubLab* (Published `2026-04-01`, Accessed `2026-10-25`): AI/machine translations of English keyword lists fail in MENA because native searchers use distinct Arabic lexical roots and phrasing, leading to high bounce rates and poor dwell time.
- [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) — *Locstars* (Published `2026-10-22`, Accessed `2026-10-25`): Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms.
