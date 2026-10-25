# `FW-066` — English-to-Arabic Video Dubbing Syllable Compression & Lip-Sync Alignment Workflow
## مسار عمل ضغط المقاطع الصوتية ومزامنة حركة الشفاه (`Lip-Sync`) عند دبلجة الإعلانات الإنجليزية إلى العربية (معالجة تمدد النص بنسبة 25%+)

- **One-Sentence Promise (EN)**: Compress translated Arabic ad scripts by 25–30% in syllable count before running AI dubbing or lip-sync (`ElevenLabs Dubbing`, `HeyGen Video Translate`, `Sync Labs`) so the Arabic voiceover never speeds up into unnatural chipmunk cadence or overflows the video cut.
- **الوعد التطبيقي في جملة واحدة (AR)**: ضغط عدد المقاطع الصوتية في النصوص العربية المترجمة بنسبة 25–30% قبل الدبلجة الآلية لمنع تسريع الصوت بشكل آلي مشوه أو تأخر الكلام عن حركة الشفاه ومشاهد الفيديو.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Spoken Arabic translations of compact English ad copy (`'Shop now and save big'`) naturally take 20–35% more syllables and speaking duration (`'تسوّقوا الآن واحصلوا على توفير كبير'`); automated AI dubbing tools force-fit the longer Arabic audio into the original English timestamp window by speeding up the voice (`1.3x` robotic speed) or drifting out of lip-sync; a syllable-compression OPERATING_FRAMEWORK fixes the script before synthesis.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-344`, `AMP-354`, `AMP-364`, `AMP-374`, `AMP-384`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-534`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever localizing or dubbing global English TV/social video ads into Arabic (MSA, Saudi Khaleeji, or Egyptian Ammiya) using AI dubbing or human voiceover.
- **داعي الاستخدام (AR)**: تُستخدم عند تعريب أو دبلجة إعلانات الفيديو الإنجليزية العالمية إلى العربية (سواء بأدوات الدبلجة بالذكاء الاصطناعي أو بالتعليق الصوتي البشري).
- **Do NOT Use When**: Never click '1-Click Auto-Translate & Dub' in HeyGen/ElevenLabs on a fast-paced English commercial without manually editing the intermediate Arabic transcript down to `<= 2.3` Arabic words per second first!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Source English Video with Timecoded Transcript (`[00:00.0 - 00:03.2]`, exact duration in seconds per phrase)
   - Target Arabic Register (`White MSA`, `Saudi Khaleeji`, or `Egyptian Ammiya`)
   - Phonetic Tashkeel rules (`AMP-332`)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `OPERATING_FRAMEWORK` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `OPERATING_FRAMEWORK` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
