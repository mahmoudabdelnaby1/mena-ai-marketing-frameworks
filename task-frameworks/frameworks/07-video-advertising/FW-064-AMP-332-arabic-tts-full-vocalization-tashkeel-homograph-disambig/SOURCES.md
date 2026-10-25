# Evidence Register & Source Boundaries — `FW-064` (`AMP-332`)

- **Framework Title (EN)**: Arabic TTS Full Vocalization (Tashkeel) & Homograph Disambiguation Prompt (ElevenLabs / HeyGen / Veo Audio — Extending `video-prompt-architect`)
- **عنوان الأصل (AR)**: قالب التشكيل الصوتي الكامل وفك التباس المتشابهات الخطية لتوليد التعليق الصوتي العربي (`ElevenLabs / HeyGen / Veo` — امتداد `video-prompt-architect`)
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-072` | [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) | F1000Research | `2025-07-16` | `2026-10-25` | `PEER_REVIEWED_RESEARCH` (`RESEARCH_FINDING`) | Demonstrates measurable accuracy drops and cultural/idiomatic errors when LLMs translate between English and regional Arabic dialects. | Peer-reviewed evaluation of ChatGPT and DeepSeek on Arabic dialects. |
| `SRC-073` | [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) | Locstars | `2026-10-22` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms. | Arabic localization QA. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements. | Voice synthesis requires clean mono reference audio and explicit phonetic/diacritic control. |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | ElevenLabs official troubleshooting guidance recommends phonetic respelling of numbers, acronyms, and ambiguous homographs plus punctuation pacing to prevent mispronunciation. | Fallback: Use ElevenLabs Pronunciation Dictionaries (`.pls` lexicon files) for recurring brand names alongside inline Tashkeel. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not apply formal Classical Arabic case endings (`تنوين الضم والكسر في أواخر الكلمات:ٌ / ٍ`) to a colloquial Saudi or Egyptian script—use **Dialectal Phonetic Tashkeel** (internal vowel diacritics + final Sukun `ْ` on pause words!). / لا تضع تشكيل الإعراب الفصيح (مثل التنوين `ٌ / ٍ` أو الضمة في آخر الكلمة) على نص مكتوب باللهجة السعودية أو المصرية؛ بل استخدم «التشكيل الصوتي اللهجي» مع تسكين أواخر الكلمات (`ْ`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
