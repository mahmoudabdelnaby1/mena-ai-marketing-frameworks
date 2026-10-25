# End-to-End Worked Example & Failure Recovery — `FW-066` (`AMP-334`)

- **Framework**: English-to-Arabic Video Dubbing Syllable Compression & Lip-Sync Alignment Workflow
- **العنوان بالعربية**: مسار عمل ضغط المقاطع الصوتية ومزامنة حركة الشفاه (`Lip-Sync`) عند دبلجة الإعلانات الإنجليزية إلى العربية (معالجة تمدد النص بنسبة 25%+)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Source Video**: 10-second Global Skincare Commercial being dubbed into Arabic via `HeyGen / ElevenLabs Dubbing Studio`.
  - `Slot 1 (0.0s–2.5s | On-Camera)`: `"Tired of waking up with dull, dehydrated skin every single morning?"` (`11` English words in `2.5s`)
  - `Slot 2 (2.5s–6.0s | Product B-Roll VO)`: `"Our hyaluronic acid booster locks in moisture for seventy-two hours straight."` (`11` English words in `3.5s`)
  - `Slot 3 (6.0s–9.0s | On-Camera)`: `"Try it today and feel the glow."` (`7` English words in `3.0s`)

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

| Slot | Duration | Shot Type | Max Arabic Words (`2.3w/s`) | Literal Translation (`FAIL — Overflows`) | Compressed Dubbing Arabic (`PASS — Exact Pacing`) | Words |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | `2.5s` | On-Camera | **5–6 words** | `هل تعبتِ من الاستيقاظ ببشرة باهتة وجافة في كل صباح؟` (`10w` — `1.45x` chipmunk speed!) | `تَعِبْتِي مِنْ بَشْرَةْ بَاهْتَة كُلْ صَبَاحْ؟` | **`6` words** |
| **2** | `3.5s` | B-Roll VO | **8 words** | `معزز حمض الهيالورونيك الخاص بنا يحبس الرطوبة لمدة اثنتين وسبعين ساعة متواصلة.` (`12w`) | `مُعَزِّزْ الهِيَالُورُونِيكْ يَحْفَظْ تَرْطِيبْ بَشْرِتِكْ لِـ ثَلَاثْ أَيَّامْ.` *(Replaced 4-word "72 hours" with 2-word "3 days"!)* | **`8` words** |
| **3** | `3.0s` | On-Camera | **6–7 words** | `جربيه اليوم واشعري بالإشراقة واللمعان الفوري.` (`6w`) | `جَرِّبِيهْ اليُومْ... وعِيشِي الإِشْرَاقَة بِنَفْسِكْ.` | **`5` words** |

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Ingenious Syllable Swap (`72 Hours` -> `3 Days`)**: Replacing `"اثنتين وسبعين ساعة متواصلة"` (11 syllables) with `"ثلاث أيام كاملة"` (6 syllables) kept the exact factual meaning while matching the 3.5-second B-roll cut at `1.0x` natural voice speed!
2. **Checked Lip Closure on Slot 1 & 3**: Matched `"صَبَاحْ"` and `"بِنَفْسِكْ"` to the actress's labial closures.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- 10-second Arabic dubbed commercial rendered at `1.00x` natural speaking speed with zero audio clipping and tight lip-sync alignment.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An editor leaves the literal Arabic translation in ElevenLabs Dubbing with 'Auto-adjust speed to fit timecode' enabled; the voiceover plays at `1.38x` speed, sounding like a fast-forwarded legal disclaimer and ruining the luxury brand mood.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Lock playback speed in your dubbing tool to **`0.95x – 1.05x` maximum**; whenever a translated segment requires `>1.05x` speed to fit the timecode, **cut Arabic words/syllables in the script** rather than speeding up the audio.
