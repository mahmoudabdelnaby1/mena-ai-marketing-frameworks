# FW-069: ElevenLabs Arabic Voice Stability, `Style Exaggeration = 0` & Breath-Artifact Prevention Checklist
## قائمة فحص إعدادات `ElevenLabs` للصوت العربي (تصفير `Style Exaggeration` ومنع تذبذب السرعة وأصوات التنفس الزائدة)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-347`, `AMP-357`, `AMP-367`, `AMP-377`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Configure ElevenLabs voice parameters (`Style Exaggeration = 0.00`, `Stability = 0.60–0.75`, `Similarity = 0.75–0.85`) and chunk lengths so Arabic voiceovers never suffer erratic speed-ups, metallic slurring, or gasping breath noises.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: ضبط معاملات الصوت في منصة `ElevenLabs` (`تصفير Style Exaggeration`، وضبط `Stability` بين `0.60–0.75`) لمنع تذبذب سرعة الكلام أو الحشرجة أو أصوات الشهيق المزعجة في التعليق الصوتي العربي.
- **Why `CHECKLIST` Fits This User Job (EN)**: ElevenLabs' official troubleshooting documentation explicitly warns that raising the `Style Exaggeration` slider causes voice instability, erratic speed shifts, and unintended extra breath/noise artifacts—an effect that is severely amplified on Arabic scripts; a parameter-tuning CHECKLIST saves hours of wasted credits.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تحذر وثائق استكشاف الأخطاء الرسمية في `ElevenLabs` من أن رفع مؤشر `Style Exaggeration` يسبب عدم استقرار الصوت وتذبذب السرعة وظهور أصوات تنفس غير طبيعية، وهو ما يتفاقم بشدة مع النصوص العربية؛ وتوفر قائمة الفحص هذه الإعدادات القياسية المثبتة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever generating Arabic voiceovers in ElevenLabs (Web Studio or API) for ads, reels, explainers, or IVR/WhatsApp audio notes.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند توليد أي تعليق صوتي عربي عبر منصة `ElevenLabs` أو واجهتها البرمجية (`API`).
- **When NOT to Use It (EN)**: Never crank `Style Exaggeration` above `0.05` on Arabic scripts hoping to make the voice sound 'more excited'—it destabilizes Arabic consonant timing and injects gasping noises.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم برفع مؤشر `Style Exaggeration` فوق `0.05` في النصوص العربية بهدف زيادة الحماس؛ لأن ذلك يخل بتوقيت الحروف العربية ويولد شهيقاً مزعجاً بين الجمل.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Vocalized Arabic Script (`AMP-332`, broken into `<= 45-word` paragraphs)
2. Selected ElevenLabs Native Arabic Voice Profile (verified native Saudi/Gulf, Egyptian, or MSA training source)
3. ElevenLabs Voice Settings JSON / Sliders

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### ElevenLabs Arabic Production Parameter Matrix & QA Checklist

#### 1. Verified ElevenLabs Parameter Settings for Arabic Commercial Voiceover (`2026-10-25`)
| Parameter | Common Broken User Setting | Mandatory Arabic Production Setting (`PASS`) | Why (Official ElevenLabs Troubleshooting Guidance) |
| :--- | :--- | :--- | :--- |
| **`style` (`Style Exaggeration`)** | `0.40 – 0.85` (Cranked up for 'hype') | **`0.00` (Strictly `0%` to `5%` max)** | Official ElevenLabs docs recommend keeping `Style Exaggeration` at **`0`** for stability; raising it on Arabic causes sudden speed-ups, slurred Tashkeel, and loud artificial breath gasps. |
| **`stability`** | `< 0.30` (Too erratic) or `1.00` (Flat robot) | **`0.60 – 0.75`** (`60%–75%`) | Balances natural Arabic melodic cadence (`النبر والتنغيم`) without hallucinating foreign accents mid-sentence. |
| **`similarity_boost`** | `1.00` (Copies background room hiss from clone sample) | **`0.75 – 0.85`** (`75%–85%`) | Preserves authentic speaker timbre without amplifying microphone artifacts from the reference audio. |
| **`use_speaker_boost`** | Always `ON` without checking | **`ON` for clean studio voices / `OFF` if sibilance (`س/ص/ش`) is harsh** | Test on a 1-sentence sample containing `س / ش / ص` first. |
| **Paragraph Chunk Length** | Pasting a 250-word script in one block | **`<= 35–50` Arabic words per generation block (`~15–20 seconds`)** | Long Arabic generations drift in speed and pitch after ~20 seconds; generate paragraph-by-paragraph using `previous_text` / `next_text` stitching! |

#### 2. Copy-Ready API Payload for Stable Arabic TTS Generation
```json
{
  "model_id": "eleven_multilingual_v2",
  "text": "جَرِّبْ عِطْرَنَا الجَدِيدْ اليُومْ... بِـ مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ بَسْ — مَعْ تَقْسِيطْ تَابِي بِدُونْ فَوَائِدْ.",
  "voice_settings": {
    "stability": 0.68,
    "similarity_boost": 0.80,
    "style": 0.0,
    "use_speaker_boost": true
  }
}
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Troubleshooting Guide — Style Exaggeration & Voice Stability** | `supported` | [Official Reference](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | ElevenLabs' official troubleshooting documentation states that setting Style Exaggeration to 0 and keeping Stability around 50–75% with shorter text segments resolves speed instability and breath artifacts. | If a specific word still inflects oddly at `style: 0.0`, regenerate just that sentence using Request Stitching (`previous_request_ids`). |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-347`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Locking Style Exaggeration at 0 and controlling energy via clean reference audio and punctuation pacing.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-357`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Locking Style Exaggeration at 0 and controlling energy via clean reference audio and punctuation pacing.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-367`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Locking Style Exaggeration at 0 and controlling energy via clean reference audio and punctuation pacing.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-377`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Locking Style Exaggeration at 0 and controlling energy via clean reference audio and punctuation pacing.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Task**: Generate a 30-second Saudi National Day commercial voiceover in ElevenLabs.
- **Problem**: Producer set `Stability = 0.25` and `Style Exaggeration = 0.70` and pasted all 75 words in one block. The generated audio started slow, sped up to `1.4x` by sentence 3, and inserted two loud gasping breaths (`"هااااه"`) before the CTA.
- **Human Review & Key Edits Applied**: 1. **De-Essing & Breath Gate in Post**: Applied a gentle `-4dB` de-esser at `6.5 kHz` on harsh Arabic sibilants (`س / ص / ش`) and a `-38dB` noise gate between sentences.
2. **Loudness Normalization**: Normalized final VO track to **`-16 LUFS`** (mobile social ad standard) with true peak at `-1.5 dBTP`.
- **Final Usable Output**: - Clean, broadcast-grade 30-second Saudi Arabic voiceover rendered with zero breath gasps, steady pacing, and crisp articulation.
- **What Can Go Wrong**: A user selects an English-native stock voice (e.g., `'Adam'` or `'Rachel'`) with `eleven_multilingual_v2` to read a Saudi Khaleeji script; even with Tashkeel, the voice pronounces `ح` (`Ḥā'`) as `هـ` (`Hā'`) and `ع` (`ʿAyn`) as a glottal stop `أ` with a heavy American accent.
- **Correction & Fallback**: In the ElevenLabs Voice Library, filter strictly by **`Language: Arabic` + `Accent: Saudi / Gulf / Egyptian / Standard`** (or use a verified native speaker Professional Voice Clone `AMP-340`)—never use an English-native base voice for Arabic ads.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero audible breath/speed-drift artifacts in final audio QA and `<2` regeneration attempts per script.
- **Baseline Definition**: Average credit spend and retry count per voiceover before parameter lock.
- **Observation Window**: Monitored across all TTS jobs. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Slider hygiene ensures clean acoustic synthesis, while phonetic Tashkeel (`AMP-332`) and native voice selection govern pronunciation authenticity.
