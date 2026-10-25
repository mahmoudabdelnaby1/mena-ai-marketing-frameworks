# `FW-064` — Arabic TTS Full Vocalization (Tashkeel) & Homograph Disambiguation Prompt (ElevenLabs / HeyGen / Veo Audio — Extending `video-prompt-architect`)
## قالب التشكيل الصوتي الكامل وفك التباس المتشابهات الخطية لتوليد التعليق الصوتي العربي (`ElevenLabs / HeyGen / Veo` — امتداد `video-prompt-architect`)

- **One-Sentence Promise (EN)**: Add phonetic diacritics (`تشكيل كامل على أواخر وبواطن الكلمات`), Sukun markers (`ْ`) for spoken dialects, and Arabic phonetic respellings of foreign brand names so AI voiceovers never mispronounce Arabic homographs.
- **الوعد التطبيقي في جملة واحدة (AR)**: إضافة التشكيل الصوتي الدقيق وعلامات السكون اللهجية والكتابة الصوتية لأسماء العلامات الأجنبية لمنع أخطاء النطق الشائعة للمتشابهات الخطية في منصات `ElevenLabs` و`HeyGen` و`Veo 3.1`.
- **Selected Artifact Type**: `EXTEND_EXISTING` *(Chosen because: Extends `user:video-prompt-architect` (Phase 3 Item 2 Phonetic Notes) into a dedicated Arabic TTS Vocalization & Homograph Disambiguation PROMPT_TEMPLATE because unvocalized Arabic consonant skeletons (`علم`, `قدم`, `سعر`, `جرب`, `عد`) have 3–6 different vowel readings that TTS models guess wrong without explicit diacritics.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-342`, `AMP-352`, `AMP-362`, `AMP-372`, `AMP-382`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-532`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before pasting any Arabic voiceover script (MSA, Saudi Khaleeji, or Egyptian Ammiya) into ElevenLabs, HeyGen, Murf, PlayHT, or Veo 3.1 native audio.
- **داعي الاستخدام (AR)**: تُستخدم قبل إدخال أي سكريبت تعليق صوتي عربي (فصحى أو خليجي أو مصري) في منصات `ElevenLabs` أو `HeyGen` أو `Veo 3.1`.
- **Do NOT Use When**: Do not apply formal Classical Arabic case endings (`تنوين الضم والكسر في أواخر الكلمات:ٌ / ٍ`) to a colloquial Saudi or Egyptian script—use **Dialectal Phonetic Tashkeel** (internal vowel diacritics + final Sukun `ْ` on pause words!).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Approved Unvocalized Arabic Video Script
   - Target Voice Mode & Dialect (`Modern White MSA`, `Saudi Khaleeji`, or `Egyptian Ammiya`)
   - List of English/Foreign Brand Names, Acronyms, and Numbers (`SAR`, `mAh`, `Pro`, `Tabby`, `valU`) in the script
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `EXTEND_EXISTING` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `EXTEND_EXISTING` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
