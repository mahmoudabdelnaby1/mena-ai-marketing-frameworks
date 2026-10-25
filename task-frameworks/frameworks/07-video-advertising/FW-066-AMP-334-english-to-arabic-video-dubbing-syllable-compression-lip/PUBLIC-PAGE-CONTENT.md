# English-to-Arabic Video Dubbing Syllable Compression & Lip-Sync Alignment Workflow
## <span dir="rtl">مسار عمل ضغط المقاطع الصوتية ومزامنة حركة الشفاه (`Lip-Sync`) عند دبلجة الإعلانات الإنجليزية إلى العربية (معالجة تمدد النص بنسبة 25%+)</span>

> **Asset ID**: `FW-066` (`AMP-334`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Compress translated Arabic ad scripts by 25–30% in syllable count before running AI dubbing or lip-sync (`ElevenLabs Dubbing`, `HeyGen Video Translate`, `Sync Labs`) so the Arabic voiceover never speeds up into unnatural chipmunk cadence or overflows the video cut.
- **AR**: <span dir="rtl">ضغط عدد المقاطع الصوتية في النصوص العربية المترجمة بنسبة 25–30% قبل الدبلجة الآلية لمنع تسريع الصوت بشكل آلي مشوه أو تأخر الكلام عن حركة الشفاه ومشاهد الفيديو.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever localizing or dubbing global English TV/social video ads into Arabic (MSA, Saudi Khaleeji, or Egyptian Ammiya) using AI dubbing or human voiceover.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تعريب أو دبلجة إعلانات الفيديو الإنجليزية العالمية إلى العربية (سواء بأدوات الدبلجة بالذكاء الاصطناعي أو بالتعليق الصوتي البشري).</span>
- **When NOT to Use It (EN)**: Never click '1-Click Auto-Translate & Dub' in HeyGen/ElevenLabs on a fast-paced English commercial without manually editing the intermediate Arabic transcript down to `<= 2.3` Arabic words per second first!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تعتمد خيار «الترجمة والدبلجة التلقائية بضغطة واحدة» للإعلانات الإنجليزية السريعة دون تقليص النص العربي الوسيط يدوياً إلى معدل `2.2 – 2.5 كلمة عربية في الثانية` أولاً.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Source English Video with Timecoded Transcript (`[00:00.0 - 00:03.2]`, exact duration in seconds per phrase)
- Target Arabic Register (`White MSA`, `Saudi Khaleeji`, or `Egyptian Ammiya`)
- Phonetic Tashkeel rules (`AMP-332`)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 3-Step Timecode-Locked Arabic Dubbing Compression Workflow

#### Step 1: Calculate the Exact Arabic Word Ceiling per Timecode Slot
Natural commercial Arabic speech runs at **`2.2 to 2.5 words per second`** (compared to `3.2 to 3.8 words per second` in fast English ads!):
- **Formula**: `Max_Arabic_Words_In_Slot = floor(Slot_Duration_Seconds * 2.3)`
  - *Example*: A `3.0-second` English sentence containing `11` English words (`"Get instant relief from dry winter skin with our new formula"`) can hold **AT MOST `6 to 7` Arabic words** (`"ودّعي جفاف الشتاء فوراً بتركيبتنا الجديدة"` — `6` words), NEVER a 12-word literal translation (`"احصلي على راحة فورية من البشرة الجافة في فصل الشتاء مع تركيبتنا الجديدة"` — which overflows by 2.2 seconds!).

#### Step 2: Copy-Ready Dubbing Compression Prompt (With Labial Lip-Sync Matching)
```xml
<system_role>
You are an Arabic Dubbing & Lip-Sync Script Adapter for MENA Commercials.
CRITICAL TIMING RULE: Spoken Arabic takes 25–30% longer per word than English. For every timecode slot, your Arabic line MUST NOT EXCEED `floor(duration_seconds * 2.3)` words!
LIP-SYNC BONUS RULE: For on-camera speaking shots (`On-Camera Lip-Sync`), match bilabial closures (`ب / م / و` in Arabic corresponding to `B / M / P / W` in English) at the start and end of phrases so AI lip-sync looks effortless.
</system_role>

<timecoded_english_source>
{{PASTE_TIMECODED_ENGLISH_LINES_WITH_DURATION_AND_SHOT_TYPE}}
</timecoded_english_source>

<output_schema>
| Slot | Duration (s) | Shot Type (VO vs On-Camera) | English Source (Word Count) | Literal Translation (REJECTED - Too Long) | Compressed Dubbing Arabic (`<= 2.3 words/s` + Tashkeel `AMP-332`) | Arabic Word Count |
</output_schema>
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Source Video**: 10-second Global Skincare Commercial being dubbed into Arabic via `HeyGen / ElevenLabs Dubbing Studio`.
  - `Slot 1 (0.0s–2.5s | On-Camera)`: `"Tired of waking up with dull, dehydrated skin every single morning?"` (`11` English words in `2.5s`)
  - `Slot 2 (2.5s–6.0s | Product B-Roll VO)`: `"Our hyaluronic acid booster locks in moisture for seventy-two hours straight."` (`11` English words in `3.5s`)
  - `Slot 3 (6.0s–9.0s | On-Camera)`: `"Try it today and feel the glow."` (`7` English words in `3.0s`)

### Step B: Initial Output (`المخرج الأولي`)
| Slot | Duration | Shot Type | Max Arabic Words (`2.3w/s`) | Literal Translation (`FAIL — Overflows`) | Compressed Dubbing Arabic (`PASS — Exact Pacing`) | Words |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | `2.5s` | On-Camera | **5–6 words** | `هل تعبتِ من الاستيقاظ ببشرة باهتة وجافة في كل صباح؟` (`10w` — `1.45x` chipmunk speed!) | `تَعِبْتِي مِنْ بَشْرَةْ بَاهْتَة كُلْ صَبَاحْ؟` | **`6` words** |
| **2** | `3.5s` | B-Roll VO | **8 words** | `معزز حمض الهيالورونيك الخاص بنا يحبس الرطوبة لمدة اثنتين وسبعين ساعة متواصلة.` (`12w`) | `مُعَزِّزْ الهِيَالُورُونِيكْ يَحْفَظْ تَرْطِيبْ بَشْرِتِكْ لِـ ثَلَاثْ أَيَّامْ.` *(Replaced 4-word "72 hours" with 2-word "3 days"!)* | **`8` words** |
| **3** | `3.0s` | On-Camera | **6–7 words** | `جربيه اليوم واشعري بالإشراقة واللمعان الفوري.` (`6w`) | `جَرِّبِيهْ اليُومْ... وعِيشِي الإِشْرَاقَة بِنَفْسِكْ.` | **`5` words** |

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Ingenious Syllable Swap (`72 Hours` -> `3 Days`)**: Replacing `"اثنتين وسبعين ساعة متواصلة"` (11 syllables) with `"ثلاث أيام كاملة"` (6 syllables) kept the exact factual meaning while matching the 3.5-second B-roll cut at `1.0x` natural voice speed!
2. **Checked Lip Closure on Slot 1 & 3**: Matched `"صَبَاحْ"` and `"بِنَفْسِكْ"` to the actress's labial closures.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- 10-second Arabic dubbed commercial rendered at `1.00x` natural speaking speed with zero audio clipping and tight lip-sync alignment.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An editor leaves the literal Arabic translation in ElevenLabs Dubbing with 'Auto-adjust speed to fit timecode' enabled; the voiceover plays at `1.38x` speed, sounding like a fast-forwarded legal disclaimer and ruining the luxury brand mood.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Lock playback speed in your dubbing tool to **`0.95x – 1.05x` maximum**; whenever a translated segment requires `>1.05x` speed to fit the timecode, **cut Arabic words/syllables in the script** rather than speeding up the audio.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Dubbing Studio & HeyGen Video Translate Timecode Alignment** | `supported` | [Official Docs](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | Both platforms allow manual editing of the translated target-language transcript per timecode segment before rendering final audio/lip-sync. | Always open the manual timeline editor and enforce `<= 2.3 Arabic words/second` before rendering the final dub. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Dubbed Audio Speed Ratio (`Target: 0.95x – 1.05x` across all segments), Zero clipped end-words, and Video Completion Rate.
- **Baseline**: Prior auto-dubbed video completion rate and viewer negative comments on voice quality.
- **Observation Window**: Checked prior to exporting every dubbed video.
- **Interpretation Boundary**: Syllable compression fixes audio naturalness and lip-sync, while culturally adapted visuals (`AMP-336`) determine local resonance.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) — *ElevenLabs* (Published `2026-06-01`, Accessed `2026-10-25`): Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements.
- [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) — *Locstars* (Published `2026-10-22`, Accessed `2026-10-25`): Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms.
