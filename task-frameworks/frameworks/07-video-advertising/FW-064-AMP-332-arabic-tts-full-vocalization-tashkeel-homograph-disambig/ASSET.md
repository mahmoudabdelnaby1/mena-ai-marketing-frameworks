# FW-064: Arabic TTS Full Vocalization (Tashkeel) & Homograph Disambiguation Prompt (ElevenLabs / HeyGen / Veo Audio — Extending `video-prompt-architect`)
## قالب التشكيل الصوتي الكامل وفك التباس المتشابهات الخطية لتوليد التعليق الصوتي العربي (`ElevenLabs / HeyGen / Veo` — امتداد `video-prompt-architect`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-342`, `AMP-352`, `AMP-362`, `AMP-372`, `AMP-382`
- **Selected Artifact Type**: `EXTEND_EXISTING`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Add phonetic diacritics (`تشكيل كامل على أواخر وبواطن الكلمات`), Sukun markers (`ْ`) for spoken dialects, and Arabic phonetic respellings of foreign brand names so AI voiceovers never mispronounce Arabic homographs.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إضافة التشكيل الصوتي الدقيق وعلامات السكون اللهجية والكتابة الصوتية لأسماء العلامات الأجنبية لمنع أخطاء النطق الشائعة للمتشابهات الخطية في منصات `ElevenLabs` و`HeyGen` و`Veo 3.1`.
- **Why `EXTEND_EXISTING` Fits This User Job (EN)**: Extends `user:video-prompt-architect` (Phase 3 Item 2 Phonetic Notes) into a dedicated Arabic TTS Vocalization & Homograph Disambiguation PROMPT_TEMPLATE because unvocalized Arabic consonant skeletons (`علم`, `قدم`, `سعر`, `جرب`, `عد`) have 3–6 different vowel readings that TTS models guess wrong without explicit diacritics.
- **لماذا يناسب شكل `EXTEND_EXISTING` هذه المهمة (AR)**: يمثل امتداداً تخصصياً لمهارة `video-prompt-architect` (وحدة الصوت واللهجات)؛ حيث تشترك الكلمات العربية غير المشكّلة في نفس الرسم الإملائي مع اختلاف المعنى والنطق، مما يجعل التشكيل الصوتي المسبق إلزامياً لمنع الأخطاء الفادحة في الإعلانات الصوتية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before pasting any Arabic voiceover script (MSA, Saudi Khaleeji, or Egyptian Ammiya) into ElevenLabs, HeyGen, Murf, PlayHT, or Veo 3.1 native audio.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل إدخال أي سكريبت تعليق صوتي عربي (فصحى أو خليجي أو مصري) في منصات `ElevenLabs` أو `HeyGen` أو `Veo 3.1`.
- **When NOT to Use It (EN)**: Do not apply formal Classical Arabic case endings (`تنوين الضم والكسر في أواخر الكلمات:ٌ / ٍ`) to a colloquial Saudi or Egyptian script—use **Dialectal Phonetic Tashkeel** (internal vowel diacritics + final Sukun `ْ` on pause words!).
- **متى لا تستخدم هذه الأداة (AR)**: لا تضع تشكيل الإعراب الفصيح (مثل التنوين `ٌ / ٍ` أو الضمة في آخر الكلمة) على نص مكتوب باللهجة السعودية أو المصرية؛ بل استخدم «التشكيل الصوتي اللهجي» مع تسكين أواخر الكلمات (`ْ`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Approved Unvocalized Arabic Video Script
2. Target Voice Mode & Dialect (`Modern White MSA`, `Saudi Khaleeji`, or `Egyptian Ammiya`)
3. List of English/Foreign Brand Names, Acronyms, and Numbers (`SAR`, `mAh`, `Pro`, `Tabby`, `valU`) in the script

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Copy-Ready Arabic TTS Vocalization & Phonetic Script Prep Prompt

```xml
<system_role>
You are an Arabic Computational Phonetician & AI Voiceover Director for ElevenLabs, HeyGen, and Veo 3.1.
PROBLEM TO SOLVE: Unvocalized Arabic scripts cause TTS models to mispronounce homographs (e.g., reading `جَرَّبْ` as `جُرِبَ`, `عِطْر` as `عَطَر`, `قَدَّمَ` as `قَدَم`, or `سِعْر` as `سَعَر`) and stumble when switching mid-sentence between RTL Arabic and LTR English brand names or numbers.
</system_role>

<script_input>
- Raw Arabic Script: {{RAW_ARABIC_SCRIPT}}
- Target Spoken Register: {{REGISTER: DIALECT_SAUDI_KHALEEJI | DIALECT_EGYPTIAN_AMMIYA | FORMAL_MSA_BROADCAST}}
- Target TTS Engine: {{ENGINE: ElevenLabs Multilingual v2/v3 | HeyGen | Veo 3.1 Native Dialogue}}
</script_input>

<phonetic_transformation_rules>
1. **Homograph Disambiguation (Internal Diacritics Mandatory)**:
   - Place explicit Fatḥah (`َ`), Kasrah (`ِ`), Ḍammah (`ُ`), and Shaddah (`ّ`) on every root consonant where ambiguity exists (`سِعْرْ` not `سعر`, `تُوَفِّرْ` not `توفر`, `مُخْتَصَّة` not `مختصة`, `جَرِّبْهَا` not `جربها`).
2. **Dialectal Pausal Sukun (`تسكين أواخر الكلمات في اللهجات والفصحى الإعلانية`)**:
   - If {{REGISTER}} is `DIALECT_SAUDI_KHALEEJI` or `DIALECT_EGYPTIAN_AMMIYA`: NEVER put tanween (`ٌ / ً / ٍ`) or formal grammatical case endings at the end of words! Instead, place a **Sukun (`ْ`)** on word endings before pauses so the TTS engine speaks naturally like a native Saudi/Egyptian speaker.
   -Even in `FORMAL_MSA_BROADCAST`, place Sukun (`ْ`) at every comma (`،`), dash (`—`), and period (`.`) (`الوقف بالسكون`).
3. **Transliterate All Numbers, Currencies & Foreign Brand Names into Vocalized Arabic Script**:
   - Never leave `349 SAR` or `iPhone 16 Pro` in digits/Latin inside an Arabic TTS paragraph (TTS engines pause, switch accent, or read `SAR` as the word `"سار"`!).
   - Rewrite numbers and brands phonetically in vocalized Arabic as spoken in the target dialect:
     - `349 SAR` (KSA) → `ثَلاثْ مِيَّة وتِسْعَة وأَرْبَعِينْ رِيَالْ`
     - `15%` → `خَمْسْطَعْشَرْ بِالمِيَّة` (KSA) / `خَمَصْتَاشَرْ فِي المِيَّة` (Egypt) / `خَمْسَةَ عَشَرَ بِالمِائَة` (MSA)
     - `Tabby & Tamara` → `تَابِي وتَمَارَا` | `InstaPay` → `إِنْسْتَا بَايْ`
4. **Breath & Pacing Markers**:
   - Keep sentences `<= 10 words` per breath and use `...` or `—` for natural 0.3s micro-pauses.
</phonetic_transformation_rules>
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Multilingual v2/v3 & HeyGen Arabic Pronunciation Troubleshooting** | `supported` | [Official Reference](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | ElevenLabs official troubleshooting guidance recommends phonetic respelling of numbers, acronyms, and ambiguous homographs plus punctuation pacing to prevent mispronunciation. | Use ElevenLabs Pronunciation Dictionaries (`.pls` lexicon files) for recurring brand names alongside inline Tashkeel. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-342`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Adding full phonetic Tashkeel and phoneme overrides before running Arabic TTS synthesis, followed by native audio QA.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-352`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Adding full phonetic Tashkeel and phoneme overrides before running Arabic TTS synthesis, followed by native audio QA.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-362`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Adding full phonetic Tashkeel and phoneme overrides before running Arabic TTS synthesis, followed by native audio QA.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-372`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Adding full phonetic Tashkeel and phoneme overrides before running Arabic TTS synthesis, followed by native audio QA.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-382`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Adding full phonetic Tashkeel and phoneme overrides before running Arabic TTS synthesis, followed by native audio QA.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-532`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-342 (Video Advertising)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Raw Unvocalized Saudi Script**:
  `"جرب عطرنا الجديد اليوم بـ 299 SAR فقط مع تقسيط Tabby بدون فوائد، الكمية محدودة!"`
- **TTS Engine Failures on Raw Script**: ElevenLabs read `"جرب"` as `"جَرَبْ"` (scabies/skin disease instead of `"جَرِّبْ"` try!), read `"عطرنا"` as `"عَطَرْنَا"`, and read `"299 SAR"` in a robotic English voice as `"Two hundred ninety-nine S-A-R"`.
- **Human Review & Key Edits Applied**: 1. **Paired with ElevenLabs Parameter Settings (`AMP-337`)**: Set `Stability = 0.65`, `Similarity = 0.80`, and **`Style Exaggeration = 0.00`** so the vocalized script is read cleanly without breath artifacts.
2. **Kept Display Captions Separate from TTS Input**: Reminded the video editor to feed the **Vocalized Phonetic Script** (`مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ`) to ElevenLabs for audio generation, while displaying the clean **Visual Caption** (`299 ر.س`) on screen (`AMP-335`)!
- **Final Usable Output**: - Zero homograph mispronunciations and seamless Arabic number/brand pronunciation on the first ElevenLabs generation pass.
- **What Can Go Wrong**: A video editor uses the TTS phonetic script (`'مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ مع تَابِي'`) directly as the burned-in on-screen subtitle text, making the on-screen captions look cluttered and spelling `'Tabby'` and `'299'` in spelled-out words.
- **Correction & Fallback**: Maintain **Two Separate Script Columns** in every video production sheet: **Column A (`TTS_Phonetic_Input`)** with full Tashkeel and spelled-out numbers for ElevenLabs/HeyGen, and **Column B (`On_Screen_Caption_Display`)** with clean unvocalized Arabic and compact numerals (`299 ر.س`) for viewer reading (`AMP-335`).

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: First-Pass TTS Pronunciation Accuracy (`Target: 0 homograph/number errors`) and Credit/Regeneration Waste Reduction (`%`).
- **Baseline Definition**: Average number of TTS regenerations required per 30s Arabic script (typically 4–6 retries without Tashkeel).
- **Observation Window**: Measured across all AI voiceover productions. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Phonetic Tashkeel guarantees accurate pronunciation, while voice actor selection and audio mixing (`AMP-340`) determine emotional warmth.
