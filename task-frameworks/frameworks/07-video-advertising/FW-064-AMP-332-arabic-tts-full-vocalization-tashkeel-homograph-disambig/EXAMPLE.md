# End-to-End Worked Example & Failure Recovery — `FW-064` (`AMP-332`)

- **Framework**: Arabic TTS Full Vocalization (Tashkeel) & Homograph Disambiguation Prompt (ElevenLabs / HeyGen / Veo Audio — Extending `video-prompt-architect`)
- **العنوان بالعربية**: قالب التشكيل الصوتي الكامل وفك التباس المتشابهات الخطية لتوليد التعليق الصوتي العربي (`ElevenLabs / HeyGen / Veo` — امتداد `video-prompt-architect`)
- **Selected Artifact Type**: `EXTEND_EXISTING`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Raw Unvocalized Saudi Script**:
  `"جرب عطرنا الجديد اليوم بـ 299 SAR فقط مع تقسيط Tabby بدون فوائد، الكمية محدودة!"`
- **TTS Engine Failures on Raw Script**: ElevenLabs read `"جرب"` as `"جَرَبْ"` (scabies/skin disease instead of `"جَرِّبْ"` try!), read `"عطرنا"` as `"عَطَرْنَا"`, and read `"299 SAR"` in a robotic English voice as `"Two hundred ninety-nine S-A-R"`.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **TTS-Ready Vocalized Saudi Script (Copy-Paste into ElevenLabs / HeyGen)**:
  `"جَرِّبْ عِطْرَنَا الجَدِيدْ اليُومْ... بِـ مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ بَسْ — مَعْ تَقْسِيطْ تَابِي بِدُونْ فَوَائِدْ... الكَمِّيَّة مَحْدُودَة!"`
- **Phonetic Audit Table**:
  - `جَرِّبْ` (Shaddah + Kasrah on Raa + Sukun on Baa -> prevents `"جَرَب"` misreading).
  - `عِطْرَنَا` (Kasrah on Ayn + Sukun on Taa -> prevents `"عَطَر"` misreading).
  - `299 SAR` → `مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ` (100% seamless Saudi spoken flow).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Paired with ElevenLabs Parameter Settings (`AMP-337`)**: Set `Stability = 0.65`, `Similarity = 0.80`, and **`Style Exaggeration = 0.00`** so the vocalized script is read cleanly without breath artifacts.
2. **Kept Display Captions Separate from TTS Input**: Reminded the video editor to feed the **Vocalized Phonetic Script** (`مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ`) to ElevenLabs for audio generation, while displaying the clean **Visual Caption** (`299 ر.س`) on screen (`AMP-335`)!

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Zero homograph mispronunciations and seamless Arabic number/brand pronunciation on the first ElevenLabs generation pass.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A video editor uses the TTS phonetic script (`'مِيتِينْ وتِسْعَة وتِسْعِينْ رِيَالْ مع تَابِي'`) directly as the burned-in on-screen subtitle text, making the on-screen captions look cluttered and spelling `'Tabby'` and `'299'` in spelled-out words.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Maintain **Two Separate Script Columns** in every video production sheet: **Column A (`TTS_Phonetic_Input`)** with full Tashkeel and spelled-out numbers for ElevenLabs/HeyGen, and **Column B (`On_Screen_Caption_Display`)** with clean unvocalized Arabic and compact numerals (`299 ر.س`) for viewer reading (`AMP-335`).
