# End-to-End Worked Example & Failure Recovery — `FW-069` (`AMP-337`)

- **Framework**: ElevenLabs Arabic Voice Stability, `Style Exaggeration = 0` & Breath-Artifact Prevention Checklist
- **العنوان بالعربية**: قائمة فحص إعدادات `ElevenLabs` للصوت العربي (تصفير `Style Exaggeration` ومنع تذبذب السرعة وأصوات التنفس الزائدة)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Task**: Generate a 30-second Saudi National Day commercial voiceover in ElevenLabs.
- **Problem**: Producer set `Stability = 0.25` and `Style Exaggeration = 0.70` and pasted all 75 words in one block. The generated audio started slow, sped up to `1.4x` by sentence 3, and inserted two loud gasping breaths (`"هااااه"`) before the CTA.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Applied Parameter & Chunking Fix**:
  1. Reset `style: 0.0`, `stability: 0.68`, `similarity_boost: 0.80`.
  2. Split the 75-word vocalized script (`AMP-332`) into **2 chunks of 37 words each**, passing `previous_text` and `next_text` context to maintain seamless prosody across the stitch.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **De-Essing & Breath Gate in Post**: Applied a gentle `-4dB` de-esser at `6.5 kHz` on harsh Arabic sibilants (`س / ص / ش`) and a `-38dB` noise gate between sentences.
2. **Loudness Normalization**: Normalized final VO track to **`-16 LUFS`** (mobile social ad standard) with true peak at `-1.5 dBTP`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Clean, broadcast-grade 30-second Saudi Arabic voiceover rendered with zero breath gasps, steady pacing, and crisp articulation.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A user selects an English-native stock voice (e.g., `'Adam'` or `'Rachel'`) with `eleven_multilingual_v2` to read a Saudi Khaleeji script; even with Tashkeel, the voice pronounces `ح` (`Ḥā'`) as `هـ` (`Hā'`) and `ع` (`ʿAyn`) as a glottal stop `أ` with a heavy American accent.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  In the ElevenLabs Voice Library, filter strictly by **`Language: Arabic` + `Accent: Saudi / Gulf / Egyptian / Standard`** (or use a verified native speaker Professional Voice Clone `AMP-340`)—never use an English-native base voice for Arabic ads.
