# `FW-068` — MENA Cultural Visual Guardrail & Authentic Gulf/Egyptian Wardrobe, Architecture & Etiquette Prompt Pack (Extending `video-prompt-architect`)
## حزمة الضوابط البصرية والثقافية لمشاهد الفيديو بالذكاء الاصطناعي (ضبط الزي السعودي والخليجي، العمارة، وآداب الضيافة — امتداد `video-prompt-architect`)

- **One-Sentence Promise (EN)**: Prevent Sora, Veo, Kling, and Midjourney from hallucinating South Asian/Moroccan hybrid clothing, wrong Saudi/Emirati ghutra/shimagh/iqal folds, or left-hand coffee pouring in MENA commercial scenes.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع نماذج الفيديو والصور (`Sora, Veo, Kling, Midjourney`) من هلوسة أزياء هجينة غير دقيقة للثوب والشماغ والعقال والعباءة أو أخطاء آداب تقديم القهوة السعودية باليد اليسرى.
- **Selected Artifact Type**: `EXTEND_EXISTING` *(Chosen because: Extends `user:video-prompt-architect` (Phase 3 Item 5 Cultural Alignment & Phase 4 Visual Anchor) with explicit English visual-anatomy descriptors and negative prompts because global video models trained on generic 'Middle East' tags conflate Saudi Najdi, Emirati, Moroccan, and South Asian attire and violate local hospitality etiquette (like pouring Dallat coffee with the wrong hand).)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-346`, `AMP-356`, `AMP-366`, `AMP-376`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever generating AI images or videos featuring people, hospitality scenes, homes, offices, or streets in Saudi Arabia, UAE, Qatar, Kuwait, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند توليد صور أو فيديوهات بالذكاء الاصطناعي تتضمن أشخاصاً أو مجالس ضيافة أو مكاتب أو معالم معمارية في السعودية والإمارات وقطر والكويت ومصر.
- **Do NOT Use When**: Never use vague prompt tokens like `'Middle Eastern man in traditional clothes'` or `'Arabian palace'`—they trigger Orientalist/Aladdin tropes, turbans, or South Asian kurtas.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Target Country & Setting (`Riyadh Modern Najdi/Salmani`, `Jeddah Hijazi`, `Dubai Emirati`, or `Cairo Contemporary`)
   - Reference Photo (`Ingredient` / `Start Frame` / `Character Reference` in `video-prompt-architect`)
   - Cultural Etiquette Checklist (Right-hand giving/drinking, Dallah in left hand + Finjan in right hand)
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
