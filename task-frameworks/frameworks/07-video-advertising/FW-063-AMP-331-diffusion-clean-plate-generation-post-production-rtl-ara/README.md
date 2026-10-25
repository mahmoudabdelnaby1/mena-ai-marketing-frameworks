# `FW-063` — Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Workflow (Extending `video-prompt-architect`)
## مسار عمل توليد المشاهد النظيفة (`Clean-Plate`) وإضافة النصوص العربية المتجهية في المونتاج (امتداد لمهارة `video-prompt-architect`)

- **One-Sentence Promise (EN)**: Eliminate reversed, disconnected Left-to-Right Arabic gibberish inside Sora, Veo, Kling, Midjourney, and DALL·E outputs by enforcing a `text-free clean plate` prompt + post-production RTL vector overlay pipeline.
- **الوعد التطبيقي في جملة واحدة (AR)**: القضاء نهائياً على الحروف العربية المقطعة والمعكوسة من اليسار لليمين داخل نماذج توليد الفيديو والصور (`Sora, Veo, Kling, Midjourney, DALL·E`) عبر فصل توليد المشهد البصري النظيف عن طبقة الخط العربي المتجهي في المونتاج.
- **Selected Artifact Type**: `EXTEND_EXISTING` *(Chosen because: Extends `user:video-prompt-architect` (Phase 4 Item 5 On-screen Text) into a deterministic 2-Stage Clean-Plate + Vector Overlay workflow because image and video diffusion models do not natively shape connected right-to-left Arabic glyphs reliably.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-341`, `AMP-351`, `AMP-361`, `AMP-371`, `AMP-381`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-531`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever generating AI video ads, product hero visuals, or social thumbnails that require Arabic headlines, prices (`SAR/AED/EGP`), or brand packaging text.
- **داعي الاستخدام (AR)**: تُستخدم عند إنتاج إعلانات الفيديو أو الصور بالذكاء الاصطناعي التي تتطلب ظهور عناوين عربية أو أسعار أو شعارات على الشاشة.
- **Do NOT Use When**: Never ask DALL·E, Midjourney, Sora, Veo, or Kling to 'write the Arabic sentence `خصم 50% بمناسبة اليوم الوطني` on a neon sign or storefront board' inside the diffusion prompt.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Scene Visual Concept (from `video-prompt-architect` Master Prompt)
   - Negative Prompt Token Pack (`no text, no Arabic calligraphy, no signage, no watermarks, clean blank packaging surface`)
   - Vector Brand Logo (`.svg` / transparent `.png`) + Arabic Typography file (`Tajawal` / `Cairo` / `IBM Plex Sans Arabic`) for CapCut/Premiere/After Effects overlay
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
