# `FW-038` — XML-Indexed Brand Voice & Context-Window Hygiene Workflow for Long Arabic Drafts
## مسار عمل فهرسة أدلة الهوية اللغوية بهيكلة `XML` لمنع انحراف التعليمات (`Instruction Drift`) في النصوص العربية الطويلة

- **One-Sentence Promise (EN)**: Replace raw 50-page brand PDF dumps in the LLM context window with a compact `<brand_constitution>` XML card so long Arabic drafts never suffer mid-document dialect or instruction drift.
- **الوعد التطبيقي في جملة واحدة (AR)**: استبدال حشو نافذة السياق بملفات الهوية الطويلة غير المفهرسة ببطاقة دستور لغوي مهيكلة بوسوم `XML` لضمان عدم انحراف اللهجة أو النبرة في المقالات والتقارير العربية الطويلة.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Anthropic's official context-window documentation confirms that dumping large unindexed files into a prompt degrades instruction adherence ('context rot' / attention dilution), causing Arabic drafts to start in Saudi Khaleeji or crisp MSA and drift into translated English syntax by page 3; an XML-indexed OPERATING_FRAMEWORK prevents attention dilution.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-191`, `AMP-201`, `AMP-211`, `AMP-221`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-521`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when generating long-form Arabic content (`>800` words), multi-email lifecycle sequences, or 30-post monthly calendars that must strictly obey brand voice, dialect, and regulatory rules.
- **داعي الاستخدام (AR)**: تُستخدم عند توليد محتوى عربي طويل (أكثر من 800 كلمة) أو سلاسل رسائل بريدية أو خطط محتوى شهرية تتطلب التزاماً صارماً بالهوية اللغوية.
- **Do NOT Use When**: Do not paste contradictory historical examples (e.g., old MSA press releases + old Egyptian Ammiya posts) into the same prompt when asking for a new Saudi Khaleeji campaign.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Raw Brand Guidelines / Tone of Voice PDF
   - 3 Golden Approved Brand Examples in the EXACT target register
   - Target document outline (broken into `<= 600-word` sections for sectioned generation)
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
