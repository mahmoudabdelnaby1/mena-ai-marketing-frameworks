# `FW-080` — MENA Mobile 4G Page-Speed & Uncompressed AI Hero Visual Optimization Checklist (`LCP < 2.5s`)
## قائمة فحص سرعة تحميل صفحات الجوال على شبكات `4G` وضغط الصور والفيديوهات المولدة بالذكاء الاصطناعي (`LCP < 2.5s`)

- **One-Sentence Promise (EN)**: Compress raw 4MB–15MB AI-generated hero images and background videos (`Midjourney / DALL·E / Veo / Sora`) into `<120KB` WebP/AVIF assets with responsive `srcset` and font subsetting so mobile landing pages load in `<2.5 seconds` across Egyptian and regional 4G networks.
- **الوعد التطبيقي في جملة واحدة (AR)**: ضغط صور وفيديوهات الواجهة الثقيلة المولدة بالذكاء الاصطناعي (من 4–15 ميجابايت إلى أقل من 120 كيلوبايت بصيغة `WebP/AVIF`) لضمان تحميل صفحات الهبوط على الجوال في أقل من 2.5 ثانية على شبكات `4G` في مصر والمنطقة.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Marketers export raw 2048x2048 `.png` images (`4.5 MB` each) from Midjourney/DALL·E or 25MB `.mp4` loops from Veo/Kling and upload them directly to the hero section of Salla, Zid, Shopify, or WordPress landing pages; on mobile 4G networks in Egypt and non-metro regions, Largest Contentful Paint (`LCP`) balloons past `6.5–11.0 seconds`, causing 40%+ of paid ad clicks to bounce before the page even renders!)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-403`, `AMP-413`, `AMP-423`, `AMP-433`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before publishing any AI-generated image, banner, or video onto a landing page or storefront in Egypt, KSA, or UAE.
- **داعي الاستخدام (AR)**: تُستخدم قبل رفع أي صورة أو بنر أو فيديو مولد بالذكاء الاصطناعي إلى صفحات الهبوط أو المتجر الإلكتروني.
- **Do NOT Use When**: Never upload a raw `.png` from Midjourney/DALL·E or an autoplay unmuted/high-bitrate `.mp4` into an above-the-fold mobile hero banner.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Raw AI Image (`.png`) or Video (`.mp4`) assets
   - PageSpeed Insights / Lighthouse Mobile 4G test report (`LCP`, `CLS`, `Total Byte Weight`)
   - `cwebp` / `avifenc` / `ffmpeg` or Squoosh compression pipeline
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
