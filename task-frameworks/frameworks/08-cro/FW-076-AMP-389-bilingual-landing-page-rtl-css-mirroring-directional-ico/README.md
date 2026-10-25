# `FW-076` — Bilingual Landing Page RTL CSS Mirroring, Directional Icon & Sticky-CTA Collision Checklist
## قائمة فحص الانعكاس الكامل لواجهات اليمين لليسار (`RTL CSS Mirroring`) واتجاه الأسهم ومنع تصادم الأزرار العائمة في الجوال

- **One-Sentence Promise (EN)**: Audit and fix incomplete RTL CSS mirroring on Arabic landing pages—flipping directional progress arrows, fixing reverse-scrolling Swiper/Slick carousels, and stopping floating WhatsApp buttons from covering the mobile 'Add to Cart / Checkout' CTA.
- **الوعد التطبيقي في جملة واحدة (AR)**: تدقيق وإصلاح الانعكاس الناقص لواجهات `RTL` في صفحات الهبوط العربية (عكس اتجاه أسهم المتابعة، ضبط السلايدر، ومنع أيقونة واتساب العائمة من تغطية زر «إضافة للسلة / إتمام الطلب» على الجوال).
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: AI landing-page builders and poorly localized themes apply `direction: rtl` to text while leaving physical CSS (`margin-left`, `right: 20px`), directional SVG arrows (`→`), and carousel physics in LTR—causing 'Continue' arrows to point backward (`→` instead of `←`), carousels to freeze on swipe, and floating WhatsApp/chat widgets to sit directly on top of the mobile sticky Checkout button!)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-399`, `AMP-409`, `AMP-419`, `AMP-429`, `AMP-439`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-539`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before launching any Arabic or bilingual landing page, Salla/Zid/Shopify theme customization, or checkout redesign on mobile and desktop.
- **داعي الاستخدام (AR)**: تُستخدم قبل إطلاق أي صفحة هبوط عربية أو ثنائية اللغة أو تعديل قوالب سلة وزد وشوبيفاي على الجوال وسطح المكتب.
- **Do NOT Use When**: Do not mirror universal non-directional icons (checkmarks `✓`, clock faces, play buttons `▶` on standard media players, or brand logos) when mirroring directional UI arrows!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Live Arabic Landing Page / Storefront URL viewed on a `375x812px` mobile viewport
   - Theme CSS stylesheet and Swiper/Slick carousel initialization script
   - List of active floating widgets (WhatsApp button, Chat widget, Loyalty launcher, Cookie banner, Sticky Add-to-Cart bar)
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
