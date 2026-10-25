# Arabic TTS Full Vocalization (Tashkeel) & Homograph Disambiguation Prompt (ElevenLabs / HeyGen / Veo Audio — Extending `video-prompt-architect`)
## <span dir="rtl">قالب التشكيل الصوتي الكامل وفك التباس المتشابهات الخطية لتوليد التعليق الصوتي العربي (`ElevenLabs / HeyGen / Veo` — امتداد `video-prompt-architect`)</span>

> **Asset ID**: `FW-064` (`AMP-332`) | **Artifact Type**: `EXTEND_EXISTING` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Add phonetic diacritics (`تشكيل كامل على أواخر وبواطن الكلمات`), Sukun markers (`ْ`) for spoken dialects, and Arabic phonetic respellings of foreign brand names so AI voiceovers never mispronounce Arabic homographs.
- **AR**: <span dir="rtl">إضافة التشكيل الصوتي الدقيق وعلامات السكون اللهجية والكتابة الصوتية لأسماء العلامات الأجنبية لمنع أخطاء النطق الشائعة للمتشابهات الخطية في منصات `ElevenLabs` و`HeyGen` و`Veo 3.1`.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before pasting any Arabic voiceover script (MSA, Saudi Khaleeji, or Egyptian Ammiya) into ElevenLabs, HeyGen, Murf, PlayHT, or Veo 3.1 native audio.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل إدخال أي سكريبت تعليق صوتي عربي (فصحى أو خليجي أو مصري) في منصات `ElevenLabs` أو `HeyGen` أو `Veo 3.1`.</span>
- **When NOT to Use It (EN)**: Do not apply formal Classical Arabic case endings (`تنوين الضم والكسر في أواخر الكلمات:ٌ / ٍ`) to a colloquial Saudi or Egyptian script—use **Dialectal Phonetic Tashkeel** (internal vowel diacritics + final Sukun `ْ` on pause words!).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تضع تشكيل الإعراب الفصيح (مثل التنوين `ٌ / ٍ` أو الضمة في آخر الكلمة) على نص مكتوب باللهجة السعودية أو المصرية؛ بل استخدم «التشكيل الصوتي اللهجي» مع تسكين أواخر الكلمات (`ْ`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Approved Unvocalized Arabic Video Script
- Target Voice Mode & Dialect (`Modern White MSA`, `Saudi Khaleeji`, or `Egyptian Ammiya`)
- List of English/Foreign Brand Names, Acronyms, and Numbers (`SAR`, `mAh`, `Pro`, `Tabby`, `valU`) in the script

## 2. The Working `EXTEND_EXISTING` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Raw Unvocalized Saudi Script**:
  `"جرب عطرنا الجديد اليوم بـ 299 SAR فقط مع تقسيط Tabby بدون فوائد، الكمية محدودة!"`
- **TTS Engine Failures on Raw Script**: ElevenLabs read `"جرب"` as `"جَرَبْ"` (scabies/skin disease instead of `"جَرِّبْ"` try!), read `"عطرنا"` as `"عَطَرْنَا"`, and read `"299 SAR"` in a robotic English voice as `"Two hundred ninety-nine S-A-R"`.

### Step B: Initial Output (`المخرج الأولي`)
- **TTS-Ready Vocalized Saudi Script (Copy-Paste into ElevenLabs / HeyGen)**:
  `"جَرِّبْ عِطْرَنَا الجَدِيدْ اليُومْ... بِـ مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ بَسْ — مَعْ تَقْسِيطْ تَابِي بِدُونْ فَوَائِدْ... الكَمِّيَّة مَحْدُودَة!"`
- **Phonetic Audit Table**:
  - `جَرِّبْ` (Shaddah + Kasrah on Raa + Sukun on Baa -> prevents `"جَرَب"` misreading).
  - `عِطْرَنَا` (Kasrah on Ayn + Sukun on Taa -> prevents `"عَطَر"` misreading).
  - `299 SAR` → `مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ` (100% seamless Saudi spoken flow).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Paired with ElevenLabs Parameter Settings (`AMP-337`)**: Set `Stability = 0.65`, `Similarity = 0.80`, and **`Style Exaggeration = 0.00`** so the vocalized script is read cleanly without breath artifacts.
2. **Kept Display Captions Separate from TTS Input**: Reminded the video editor to feed the **Vocalized Phonetic Script** (`مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ`) to ElevenLabs for audio generation, while displaying the clean **Visual Caption** (`299 ر.س`) on screen (`AMP-335`)!

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Zero homograph mispronunciations and seamless Arabic number/brand pronunciation on the first ElevenLabs generation pass.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A video editor uses the TTS phonetic script (`'مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ مع تَابِي'`) directly as the burned-in on-screen subtitle text, making the on-screen captions look cluttered and spelling `'Tabby'` and `'299'` in spelled-out words.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Maintain **Two Separate Script Columns** in every video production sheet: **Column A (`TTS_Phonetic_Input`)** with full Tashkeel and spelled-out numbers for ElevenLabs/HeyGen, and **Column B (`On_Screen_Caption_Display`)** with clean unvocalized Arabic and compact numerals (`299 ر.س`) for viewer reading (`AMP-335`).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Multilingual v2/v3 & HeyGen Arabic Pronunciation Troubleshooting** | `supported` | [Official Docs](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | ElevenLabs official troubleshooting guidance recommends phonetic respelling of numbers, acronyms, and ambiguous homographs plus punctuation pacing to prevent mispronunciation. | Use ElevenLabs Pronunciation Dictionaries (`.pls` lexicon files) for recurring brand names alongside inline Tashkeel. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: First-Pass TTS Pronunciation Accuracy (`Target: 0 homograph/number errors`) and Credit/Regeneration Waste Reduction (`%`).
- **Baseline**: Average number of TTS regenerations required per 30s Arabic script (typically 4–6 retries without Tashkeel).
- **Observation Window**: Measured across all AI voiceover productions.
- **Interpretation Boundary**: Phonetic Tashkeel guarantees accurate pronunciation, while voice actor selection and audio mixing (`AMP-340`) determine emotional warmth.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) — *ElevenLabs* (Published `2026-06-01`, Accessed `2026-10-25`): Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements.
- [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) — *F1000Research* (Published `2025-07-16`, Accessed `2026-10-25`): Demonstrates measurable accuracy drops and cultural/idiomatic errors when LLMs translate between English and regional Arabic dialects.
- [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) — *Locstars* (Published `2026-10-22`, Accessed `2026-10-25`): Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms.
