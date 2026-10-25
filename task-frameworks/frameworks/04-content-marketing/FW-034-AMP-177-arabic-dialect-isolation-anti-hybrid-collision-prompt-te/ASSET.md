# FW-034: Arabic Dialect Isolation & Anti-Hybrid-Collision Prompt Template (Egyptian Ammiya vs. Saudi/Gulf Khaleeji vs. White MSA)
## قالب عزل اللهجات العربية ومنع الخلط اللهجي الهجين (العامية المصرية مقابل الخليجية السعودية مقابل الفصحى البيضاء)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-187`, `AMP-197`, `AMP-207`, `AMP-217`, `AMP-227`
- **Selected Artifact Type**: `PROMPT_TEMPLATE`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Lock LLM copy generation to one pure Arabic dialect register—preventing jarring mid-sentence collisions of Egyptian (`كده/عايز`), Levantine (`هلق/كتير`), and Saudi Khaleeji (`الحين/ودك`) in the same script.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تقييد النموذج اللغوي بسجل لهجي واحد نقي ومنع الخلط الهجين المحرج بين العامية المصرية (`كده/عايز`) والشامية (`هلق/كتير`) والخليجية (`الحين/ودك`) داخل النص الواحد.
- **Why `PROMPT_TEMPLATE` Fits This User Job (EN)**: Peer-reviewed Arabic LLM research (F1000Research 2025/2026) and localization audits confirm that when prompted simply for 'colloquial Arabic' (`بالعامية`), models blend Egyptian, Levantine, and Gulf tokens within the same paragraph; a PROMPT_TEMPLATE with a Negative Dialect Exclusion Table eliminates hybrid collisions.
- **لماذا يناسب شكل `PROMPT_TEMPLATE` هذه المهمة (AR)**: تثبت الأبحاث المحكمة وتدقيقات التعريب أن مطالبة النماذج بالكتابة «باللهجة العامية» تنتج خليطاً هجيناً يجمع مفردات مصرية وشامية وخليجية في جملة واحدة؛ لذا يعزل هذا القالب اللهجة المستهدفة بقائمة حظر صريحة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever writing social captions, video scripts, ad copy, WhatsApp templates, or landing page hooks in spoken regional Arabic.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند كتابة نصوص الإعلانات أو سكريبتات الفيديو أو منشورات التواصل الاجتماعي أو رسائل واتساب باللهجة المحلية.
- **When NOT to Use It (EN)**: Do not use heavy street slang for formal enterprise B2B contracts, legal terms, or medical leaflets—use Modern White Arabic (`الفصحى البيضاء المعاصرة`) for those.
- **متى لا تستخدم هذه الأداة (AR)**: لا تستخدم العامية الدارجة في العقود الرسمية أو التقارير المالية أو النشرات الطبية؛ بل استخدم «العربية الفصحى البيضاء المعاصرة».

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Target Market Track (`Track A: Saudi White Khaleeji`, `Track B: Emirati Gulf`, `Track C: Egyptian Cairene Ammiya`, or `Track D: Modern White MSA`)
2. Target Grammatical Gender (`Masculine Singular`, `Feminine Singular`, or `Plural/Neutral` — `AMP-182`)
3. Core Offer & Brand Persona

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Frontier LLMs (Claude 3.7/4 Sonnet, GPT-4o, Gemini 2.5 Pro) Dialect Control** | `supported` | [Official Reference](https://f1000research.com/articles/14-694) (`2026-10-25`) | F1000Research and Locstars evaluations confirm LLMs default to hybrid dialect blending unless explicit positive and negative lexical lists are enforced in the prompt. | Always run a post-generation regex check against the banned cross-dialect token list. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-187`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Dialect-locked system prompts with explicit forbidden-word tables and native reviewer sign-off.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-197`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Dialect-locked system prompts with explicit forbidden-word tables and native reviewer sign-off.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-207`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Dialect-locked system prompts with explicit forbidden-word tables and native reviewer sign-off.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-217`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Dialect-locked system prompts with explicit forbidden-word tables and native reviewer sign-off.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-227`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Dialect-locked system prompts with explicit forbidden-word tables and native reviewer sign-off.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-517`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-177 (Content Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Track**: `SAUDI_WHITE_KHALEEJI` (`Riyadh & Jeddah Coffee Subscription App`).
- **Broken Hybrid AI Draft (Before Prompt)**: `"لو عايز تشرب قهوة مختصة كل يوم الصبح، تطبيقنا بيوفرلك باقات كتير منيحة توصلك لحد باب البيت الحين وبسعر خيالي!"` *(Collides Egyptian `لو عايز / بيوفرلك / لحد`, Levantine `كتير منيحة`, and Gulf `الحين` in 20 words!)*
- **Human Review & Key Edits Applied**: 1. **Orthography Check (`ذا` vs `ده`)**: Confirmed Saudi copy uses `"كذا"` / `"هذا"` (with Thal `ذ`) while Egyptian copy uses `"كده"` / `"ده"` (with Dal `د`).
2. **Ran Automated Regex Linter**: Confirmed `0` banned cross-dialect tokens in either version.
- **Final Usable Output**: - Two 100% dialect-pure scripts delivered (`SAUDI_WHITE_KHALEEJI` for Riyadh/Jeddah and `EGYPTIAN_CAIRENE_AMMIYA` for Cairo) with zero hybrid collisions.
- **What Can Go Wrong**: A prompt specifies `'Write in Gulf Arabic'`, and the LLM mixes Kuwaiti `'شدعوة / صج'`, Emirati `'وايد / عسب'`, and Hijazi `'دحين'` in a single paragraph aimed at a Riyadh audience.
- **Correction & Fallback**: Specify the exact **Country & Sub-Register** (`Saudi White Khaleeji` vs. `Emirati Khaleeji` vs. `Kuwaiti Khaleeji`) rather than the umbrella term `'Gulf Arabic'`.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero cross-dialect token collisions per 1,000 words of published copy and improved native speaker authenticity score in pre-launch review.
- **Baseline Definition**: Rate of dialect-collision edits required on unguided AI drafts.
- **Observation Window**: Checked on every script/caption batch. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Dialect purity prevents immediate audience alienation, while the core value proposition and hook structure drive conversion.
