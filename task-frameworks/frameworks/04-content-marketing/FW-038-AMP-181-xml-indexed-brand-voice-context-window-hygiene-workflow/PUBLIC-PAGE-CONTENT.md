# XML-Indexed Brand Voice & Context-Window Hygiene Workflow for Long Arabic Drafts
## <span dir="rtl">مسار عمل فهرسة أدلة الهوية اللغوية بهيكلة `XML` لمنع انحراف التعليمات (`Instruction Drift`) في النصوص العربية الطويلة</span>

> **Asset ID**: `FW-038` (`AMP-181`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Content Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Replace raw 50-page brand PDF dumps in the LLM context window with a compact `<brand_constitution>` XML card so long Arabic drafts never suffer mid-document dialect or instruction drift.
- **AR**: <span dir="rtl">استبدال حشو نافذة السياق بملفات الهوية الطويلة غير المفهرسة ببطاقة دستور لغوي مهيكلة بوسوم `XML` لضمان عدم انحراف اللهجة أو النبرة في المقالات والتقارير العربية الطويلة.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when generating long-form Arabic content (`>800` words), multi-email lifecycle sequences, or 30-post monthly calendars that must strictly obey brand voice, dialect, and regulatory rules.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند توليد محتوى عربي طويل (أكثر من 800 كلمة) أو سلاسل رسائل بريدية أو خطط محتوى شهرية تتطلب التزاماً صارماً بالهوية اللغوية.</span>
- **When NOT to Use It (EN)**: Do not paste contradictory historical examples (e.g., old MSA press releases + old Egyptian Ammiya posts) into the same prompt when asking for a new Saudi Khaleeji campaign.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بلصق أمثلة سابقة متناقضة اللهجة (مثل بيانات صحفية بالفصحى مع منشورات مصرية قديمة) داخل نفس البرومبت عند طلب حملة جديدة باللهجة الخليجية.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Raw Brand Guidelines / Tone of Voice PDF
- 3 Golden Approved Brand Examples in the EXACT target register
- Target document outline (broken into `<= 600-word` sections for sectioned generation)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 3-Step Context Hygiene & XML Brand Constitution Workflow

#### Step 1: Distill the 50-Page Brand PDF into a `<= 500-Token` `<brand_constitution>` XML Block
Never attach a raw 50-page brand book containing visual logo spacing rules, typography history, and mixed-language samples to a copywriting prompt. Extract only the active linguistic rules into this XML structure:
```xml
<brand_constitution version="1.2">
  <identity>
    <brand_name_ar>{{BRAND_AR}}</brand_name_ar>
    <brand_name_en>{{BRAND_EN}}</brand_name_en>
    <target_market_and_register>{{E.G., Saudi Executive White Arabic / Cairene Smart Casual}}</target_market_and_register>
    <grammatical_address>{{E.G., Feminine Singular أنتِ / Masculine Singular أنتَ / Plural أنتم}}</grammatical_address>
  </identity>
  <mandatory_terminology>
    <term source="Installments" use_ar="تقسيط على 4 دفعات عبر تابي وتمارا" never_use="دفعات مؤجلة الائتمان" />
    <term source="Customer Support" use_ar="فريق العناية بالعملاء" never_use="قسم الشكاوى" />
  </mandatory_terminology>
  <strictly_banned_phrases>
    <ban>في عالم يتسارع فيه</ban>
    <ban>هل تبحث عن</ban>
    <ban>لا شك أن</ban>
    <ban>تُعدّ بمثابة</ban>
  </strictly_banned_phrases>
  <golden_style_samples>
    <sample id="1">{{100_WORD_PERFECT_BRAND_SAMPLE_IN_EXACT_TARGET_DIALECT}}</sample>
  </golden_style_samples>
</brand_constitution>
```

#### Step 2: Section-by-Section Generation with Rule Pinning (For Drafts `> 800` Words)
- Place `<brand_constitution>` at the top of the system prompt AND repeat a 3-line `<section_style_reminder>` at the end of the user prompt right before generation.
- Generate long Arabic guides in **300–500 word modular sections** rather than asking for a single 3,000-word output in one pass (which triggers output token truncation `AMP-185` and mid-draft style drift).

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Task**: Write a 2,000-word Saudi B2B FinTech Guide on Corporate Expense Management (`إدارة مصروفات الشركات والبطاقات المؤسسية في السعودية`).
- **Previous Failure**: Team uploaded a 42-page PDF brand book + 15 old English blog posts into the prompt. By Section 4, the model drifted from Saudi executive terminology (`الفوترة الإلكترونية ZATCA المرحلة الثانية - ربط`) into generic translated US tax terms (`خصومات مصلحة الضرائب الفيدرالية IRS`).

### Step B: Initial Output (`المخرج الأولي`)
- **Distilled `<brand_constitution>` (`380` tokens)**:
  - Locked Saudi financial lexicon: `هيئة الزكاة والضريبة والجمارك (ZATCA)`, `الفوترة الإلكترونية (فاتورة - مرحلة الربط والتكامل)`, `نظام مدى`, `سريع (SARIE)`, `ضريبة القيمة المضافة 15%`.
  - Explicitly banned US/EU regulatory terms (`IRS`, `401k`, `VAT 20%`, `HMRC`).
- **Modular 4-Part Generation**: Generated Sections 1–4 with 100% lexical consistency from opening paragraph to final conclusion.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified ZATCA Phase 2 Terminology**: Confirmed accurate reference to ZATCA Phase 2 integration (`المرحلة الثانية: مرحلة الربط والتكامل`) and XML/UUID invoice requirements.
2. **Checked Zero Cliché Drift**: Confirmed zero occurrences of `"في عالمنا الرقمي المتسارع"` across all 4 sections.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- 2,000-word Saudi B2B FinTech whitepaper completed with zero foreign regulatory drift and 82% reduction in input prompt token cost.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A writer pastes 10 old blog posts into the prompt as 'style examples', unaware that 4 of them were written by a previous freelancer in Levantine/Egyptian idioms; the LLM imitates the noisy examples and ignores the system prompt.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Audit every few-shot `<sample>` before adding it to `<brand_constitution>`: **1 clean 100-word golden paragraph beats 10 noisy historical posts**.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic Claude Context Windows & XML Structuring Best Practices** | `supported` | [Official Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) (`2026-10-25`) | Anthropic documentation notes that as context length grows with unindexed or conflicting material, instruction adherence can degrade; XML tags (`<brand_constitution>`) and clean few-shot examples preserve precision. | Keep the active style prompt under 1,000 tokens and generate long Arabic documents in modular sections. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Section-to-section terminology consistency rate (0 foreign/off-brand terms in Sections 3–5) and reduced human rewrite time per long-form asset.
- **Baseline**: Edit count in second half of long-form AI drafts prior to XML indexing.
- **Observation Window**: Measured across 5 consecutive long-form pieces.
- **Interpretation Boundary**: Context hygiene ensures stylistic and lexical consistency, while primary source pack quality (`AMP-179`) governs factual depth.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) — *Anthropic* (Published `2026-08-15`, Accessed `2026-10-25`): Recommends XML tag structuring, explicit role/audience context, few-shot examples, and verification criteria to avoid generic outputs.
- [Context windows - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) — *Anthropic* (Published `2026-08-15`, Accessed `2026-10-25`): Larger context windows do not guarantee uniform recall; dumping unindexed guidelines and noisy history degrades instruction adherence.
