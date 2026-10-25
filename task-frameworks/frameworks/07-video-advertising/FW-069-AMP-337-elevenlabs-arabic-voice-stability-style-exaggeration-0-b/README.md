# `FW-069` — ElevenLabs Arabic Voice Stability, `Style Exaggeration = 0` & Breath-Artifact Prevention Checklist
## قائمة فحص إعدادات `ElevenLabs` للصوت العربي (تصفير `Style Exaggeration` ومنع تذبذب السرعة وأصوات التنفس الزائدة)

- **One-Sentence Promise (EN)**: Configure ElevenLabs voice parameters (`Style Exaggeration = 0.00`, `Stability = 0.60–0.75`, `Similarity = 0.75–0.85`) and chunk lengths so Arabic voiceovers never suffer erratic speed-ups, metallic slurring, or gasping breath noises.
- **الوعد التطبيقي في جملة واحدة (AR)**: ضبط معاملات الصوت في منصة `ElevenLabs` (`تصفير Style Exaggeration`، وضبط `Stability` بين `0.60–0.75`) لمنع تذبذب سرعة الكلام أو الحشرجة أو أصوات الشهيق المزعجة في التعليق الصوتي العربي.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: ElevenLabs' official troubleshooting documentation explicitly warns that raising the `Style Exaggeration` slider causes voice instability, erratic speed shifts, and unintended extra breath/noise artifacts—an effect that is severely amplified on Arabic scripts; a parameter-tuning CHECKLIST saves hours of wasted credits.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-347`, `AMP-357`, `AMP-367`, `AMP-377`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever generating Arabic voiceovers in ElevenLabs (Web Studio or API) for ads, reels, explainers, or IVR/WhatsApp audio notes.
- **داعي الاستخدام (AR)**: تُستخدم عند توليد أي تعليق صوتي عربي عبر منصة `ElevenLabs` أو واجهتها البرمجية (`API`).
- **Do NOT Use When**: Never crank `Style Exaggeration` above `0.05` on Arabic scripts hoping to make the voice sound 'more excited'—it destabilizes Arabic consonant timing and injects gasping noises.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Vocalized Arabic Script (`AMP-332`, broken into `<= 45-word` paragraphs)
   - Selected ElevenLabs Native Arabic Voice Profile (verified native Saudi/Gulf, Egyptian, or MSA training source)
   - ElevenLabs Voice Settings JSON / Sliders
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `CHECKLIST` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `CHECKLIST` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
