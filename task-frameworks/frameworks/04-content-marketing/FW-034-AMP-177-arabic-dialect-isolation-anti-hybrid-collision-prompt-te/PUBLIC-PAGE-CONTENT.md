# Arabic Dialect Isolation & Anti-Hybrid-Collision Prompt Template (Egyptian Ammiya vs. Saudi/Gulf Khaleeji vs. White MSA)
## <span dir="rtl">قالب عزل اللهجات العربية ومنع الخلط اللهجي الهجين (العامية المصرية مقابل الخليجية السعودية مقابل الفصحى البيضاء)</span>

> **Asset ID**: `FW-034` (`AMP-177`) | **Artifact Type**: `PROMPT_TEMPLATE` | **Channel**: Content Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Lock LLM copy generation to one pure Arabic dialect register—preventing jarring mid-sentence collisions of Egyptian (`كده/عايز`), Levantine (`هلق/كتير`), and Saudi Khaleeji (`الحين/ودك`) in the same script.
- **AR**: <span dir="rtl">تقييد النموذج اللغوي بسجل لهجي واحد نقي ومنع الخلط الهجين المحرج بين العامية المصرية (`كده/عايز`) والشامية (`هلق/كتير`) والخليجية (`الحين/ودك`) داخل النص الواحد.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever writing social captions, video scripts, ad copy, WhatsApp templates, or landing page hooks in spoken regional Arabic.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند كتابة نصوص الإعلانات أو سكريبتات الفيديو أو منشورات التواصل الاجتماعي أو رسائل واتساب باللهجة المحلية.</span>
- **When NOT to Use It (EN)**: Do not use heavy street slang for formal enterprise B2B contracts, legal terms, or medical leaflets—use Modern White Arabic (`الفصحى البيضاء المعاصرة`) for those.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تستخدم العامية الدارجة في العقود الرسمية أو التقارير المالية أو النشرات الطبية؛ بل استخدم «العربية الفصحى البيضاء المعاصرة».</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Target Market Track (`Track A: Saudi White Khaleeji`, `Track B: Emirati Gulf`, `Track C: Egyptian Cairene Ammiya`, or `Track D: Modern White MSA`)
- Target Grammatical Gender (`Masculine Singular`, `Feminine Singular`, or `Plural/Neutral` — `AMP-182`)
- Core Offer & Brand Persona

## 2. The Working `PROMPT_TEMPLATE` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Copy-Ready Dialect-Lock Prompt Template (With Cross-Dialect Exclusion Matrix)

```xml
<system_role>
You are a Native Arabic Copywriter & Socio-Linguistic Editor.
CRITICAL FAILURE TO AVOID: Never mix Arabic dialects in the same text. If the selected track is SAUDI_KHALEEJI, a single Egyptian token ("كده", "عايز", "برضو", "دلوقتي", "إزاي") or Levantine token ("هلق", "كتير", "كرمال", "منيح", "شو") is an automatic FAIL. Conversely, if the track is EGYPTIAN_AMMIYA, a single Gulf token ("الحين", "وش", "ودك", "واجد", "زين") or Levantine token is an automatic FAIL.
</system_role>

<selected_track>{{TRACK: SAUDI_WHITE_KHALEEJI | EMIRATI_KHALEEJI | EGYPTIAN_CAIRENE_AMMIYA | MODERN_WHITE_MSA}}</selected_track>
<grammatical_gender>{{GENDER: MASCULINE_SINGULAR | FEMININE_SINGULAR | PLURAL_INCLUSIVE}}</grammatical_gender>

<dialect_isolation_rules>
1. IF SAUDI_WHITE_KHALEEJI:
   - Allowed Natural Markers: الحين، وش، ودك، مره، عشان، كذا، توه، يمديك، أبشر، حياك، لا يفوتك.
   - BANNED (Zero Tolerance): كده، عايز، دلوقتي، إزاي، بتاع، خالص (Egyptian); هلق، كتير، كرمال، منيح، هيك، شو (Levantine).
2. IF EMIRATI_KHALEEJI:
   - Allowed Natural Markers: الحين، وايد، شقايل، عسب، جيه، يبالك، فالك طيب، مرحبا الساع.
   - BANNED (Zero Tolerance): كده، دلوقتي، عايز (Egyptian); هلق، كتير، هيك (Levantine).
3. IF EGYPTIAN_CAIRENE_AMMIYA:
   - Allowed Natural Markers: دلوقتي، كده، عايز/عايزة، إزاي، علشان، أوي، بجد، متفوتش، يلا.
   - BANNED (Zero Tolerance): الحين، وش، ودك، كذا، وايد، يمديك (Gulf); هلق، كرمال، منيح، هيك (Levantine).
4. IF MODERN_WHITE_MSA:
   - Crisp, contemporary pan-Arab standard Arabic free of archaic dictionary words and free of regional slang.
</dialect_isolation_rules>

<self_verification_step>
After generating the draft, scan every word against the BANNED list for {{TRACK}}. Output a JSON block `{"dialect_purity_check": "PASS", "banned_tokens_found": []}` alongside the final copy.
</self_verification_step>
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Track**: `SAUDI_WHITE_KHALEEJI` (`Riyadh & Jeddah Coffee Subscription App`).
- **Broken Hybrid AI Draft (Before Prompt)**: `"لو عايز تشرب قهوة مختصة كل يوم الصبح، تطبيقنا بيوفرلك باقات كتير منيحة توصلك لحد باب البيت الحين وبسعر خيالي!"` *(Collides Egyptian `لو عايز / بيوفرلك / لحد`, Levantine `كتير منيحة`, and Gulf `الحين` in 20 words!)*

### Step B: Initial Output (`المخرج الأولي`)
- **Dialect Collision Audit of Broken Draft**:
  - Detected Egyptian tokens: `عايز`, `بيوفرلك`, `لحد`
  - Detected Levantine tokens: `كتير`, `منيحة`
- **Rewritten `SAUDI_WHITE_KHALEEJI` Output**:
  `"ودك بقهوة مختصة تضبط يومك كل صباح؟ تطبيقنا يوصلك باقاتك المفضلة لباب بيتك أو مكتبك بالرياض الحين، وبسعر يفرق معك!"`
- **Bonus `EGYPTIAN_CAIRENE_AMMIYA` Output (For Cairo Launch)**:
  `"لو عايز تبدأ يومك بقهوة مختصة مظبوطة كل صبح، تطبيقنا هيوصلك باقتك لحد باب البيت أو المكتب في دقائق وبسعر يوفر معاك بجد!"`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Orthography Check (`ذا` vs `ده`)**: Confirmed Saudi copy uses `"كذا"` / `"هذا"` (with Thal `ذ`) while Egyptian copy uses `"كده"` / `"ده"` (with Dal `د`).
2. **Ran Automated Regex Linter**: Confirmed `0` banned cross-dialect tokens in either version.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Two 100% dialect-pure scripts delivered (`SAUDI_WHITE_KHALEEJI` for Riyadh/Jeddah and `EGYPTIAN_CAIRENE_AMMIYA` for Cairo) with zero hybrid collisions.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A prompt specifies `'Write in Gulf Arabic'`, and the LLM mixes Kuwaiti `'شدعوة / صج'`, Emirati `'وايد / عسب'`, and Hijazi `'دحين'` in a single paragraph aimed at a Riyadh audience.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Specify the exact **Country & Sub-Register** (`Saudi White Khaleeji` vs. `Emirati Khaleeji` vs. `Kuwaiti Khaleeji`) rather than the umbrella term `'Gulf Arabic'`.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Frontier LLMs (Claude 3.7/4 Sonnet, GPT-4o, Gemini 2.5 Pro) Dialect Control** | `supported` | [Official Docs](https://f1000research.com/articles/14-694) (`2026-10-25`) | F1000Research and Locstars evaluations confirm LLMs default to hybrid dialect blending unless explicit positive and negative lexical lists are enforced in the prompt. | Always run a post-generation regex check against the banned cross-dialect token list. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero cross-dialect token collisions per 1,000 words of published copy and improved native speaker authenticity score in pre-launch review.
- **Baseline**: Rate of dialect-collision edits required on unguided AI drafts.
- **Observation Window**: Checked on every script/caption batch.
- **Interpretation Boundary**: Dialect purity prevents immediate audience alienation, while the core value proposition and hook structure drive conversion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) — *F1000Research* (Published `2025-07-16`, Accessed `2026-10-25`): Demonstrates measurable accuracy drops and cultural/idiomatic errors when LLMs translate between English and regional Arabic dialects.
- [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) — *Locstars* (Published `2026-10-22`, Accessed `2026-10-25`): Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms.
- [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) — *AISyncSo* (Published `2026-09-24`, Accessed `2026-10-25`): Shows why customer-facing AI agents trained on MSA fail to parse everyday Khaleeji phrasing, politeness formulas, and intent in Riyadh, Dubai, and Doha.
