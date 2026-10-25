# ElevenLabs Arabic Voice Stability, `Style Exaggeration = 0` & Breath-Artifact Prevention Checklist
## <span dir="rtl">قائمة فحص إعدادات `ElevenLabs` للصوت العربي (تصفير `Style Exaggeration` ومنع تذبذب السرعة وأصوات التنفس الزائدة)</span>

> **Asset ID**: `FW-069` (`AMP-337`) | **Artifact Type**: `CHECKLIST` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Configure ElevenLabs voice parameters (`Style Exaggeration = 0.00`, `Stability = 0.60–0.75`, `Similarity = 0.75–0.85`) and chunk lengths so Arabic voiceovers never suffer erratic speed-ups, metallic slurring, or gasping breath noises.
- **AR**: <span dir="rtl">ضبط معاملات الصوت في منصة `ElevenLabs` (`تصفير Style Exaggeration`، وضبط `Stability` بين `0.60–0.75`) لمنع تذبذب سرعة الكلام أو الحشرجة أو أصوات الشهيق المزعجة في التعليق الصوتي العربي.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever generating Arabic voiceovers in ElevenLabs (Web Studio or API) for ads, reels, explainers, or IVR/WhatsApp audio notes.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند توليد أي تعليق صوتي عربي عبر منصة `ElevenLabs` أو واجهتها البرمجية (`API`).</span>
- **When NOT to Use It (EN)**: Never crank `Style Exaggeration` above `0.05` on Arabic scripts hoping to make the voice sound 'more excited'—it destabilizes Arabic consonant timing and injects gasping noises.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم برفع مؤشر `Style Exaggeration` فوق `0.05` في النصوص العربية بهدف زيادة الحماس؛ لأن ذلك يخل بتوقيت الحروف العربية ويولد شهيقاً مزعجاً بين الجمل.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Vocalized Arabic Script (`AMP-332`, broken into `<= 45-word` paragraphs)
- Selected ElevenLabs Native Arabic Voice Profile (verified native Saudi/Gulf, Egyptian, or MSA training source)
- ElevenLabs Voice Settings JSON / Sliders

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Task**: Generate a 30-second Saudi National Day commercial voiceover in ElevenLabs.
- **Problem**: Producer set `Stability = 0.25` and `Style Exaggeration = 0.70` and pasted all 75 words in one block. The generated audio started slow, sped up to `1.4x` by sentence 3, and inserted two loud gasping breaths (`"هااااه"`) before the CTA.

### Step B: Initial Output (`المخرج الأولي`)
- **Applied Parameter & Chunking Fix**:
  1. Reset `style: 0.0`, `stability: 0.68`, `similarity_boost: 0.80`.
  2. Split the 75-word vocalized script (`AMP-332`) into **2 chunks of 37 words each**, passing `previous_text` and `next_text` context to maintain seamless prosody across the stitch.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **De-Essing & Breath Gate in Post**: Applied a gentle `-4dB` de-esser at `6.5 kHz` on harsh Arabic sibilants (`س / ص / ش`) and a `-38dB` noise gate between sentences.
2. **Loudness Normalization**: Normalized final VO track to **`-16 LUFS`** (mobile social ad standard) with true peak at `-1.5 dBTP`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Clean, broadcast-grade 30-second Saudi Arabic voiceover rendered with zero breath gasps, steady pacing, and crisp articulation.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A user selects an English-native stock voice (e.g., `'Adam'` or `'Rachel'`) with `eleven_multilingual_v2` to read a Saudi Khaleeji script; even with Tashkeel, the voice pronounces `ح` (`Ḥā'`) as `هـ` (`Hā'`) and `ع` (`ʿAyn`) as a glottal stop `أ` with a heavy American accent.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: In the ElevenLabs Voice Library, filter strictly by **`Language: Arabic` + `Accent: Saudi / Gulf / Egyptian / Standard`** (or use a verified native speaker Professional Voice Clone `AMP-340`)—never use an English-native base voice for Arabic ads.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Troubleshooting Guide — Style Exaggeration & Voice Stability** | `supported` | [Official Docs](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | ElevenLabs' official troubleshooting documentation states that setting Style Exaggeration to 0 and keeping Stability around 50–75% with shorter text segments resolves speed instability and breath artifacts. | If a specific word still inflects oddly at `style: 0.0`, regenerate just that sentence using Request Stitching (`previous_request_ids`). |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero audible breath/speed-drift artifacts in final audio QA and `<2` regeneration attempts per script.
- **Baseline**: Average credit spend and retry count per voiceover before parameter lock.
- **Observation Window**: Monitored across all TTS jobs.
- **Interpretation Boundary**: Slider hygiene ensures clean acoustic synthesis, while phonetic Tashkeel (`AMP-332`) and native voice selection govern pronunciation authenticity.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) — *ElevenLabs* (Published `2026-06-01`, Accessed `2026-10-25`): Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements.
