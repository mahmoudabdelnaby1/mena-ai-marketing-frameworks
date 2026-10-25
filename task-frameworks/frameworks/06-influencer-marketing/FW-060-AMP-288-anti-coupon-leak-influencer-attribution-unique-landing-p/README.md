# `FW-060` — Anti-Coupon-Leak Influencer Attribution & Unique Landing-Page / Cart-Link Workflow
## مسار عمل قياس عائد المؤثرين ومنع تسرب أكواد الخصم الثابتة (`Promo Code Cannibalization`) لزيارات الدفع العضوية

- **One-Sentence Promise (EN)**: Prevent browser coupon extensions and Telegram/WhatsApp coupon groups from hijacking static influencer promo codes (`AHMED10`) at checkout—stopping AI attribution models from over-crediting creators for organic sales they didn't drive.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع إضافات المتصفح ومجموعات الكوبونات من سرقة أكواد خصم المؤثرين الثابتة وتطبيقها على المتسوقين العضويين عند الدفع، وضمان قياس المبيعات الحقيقية التي جلبها المؤثر فعلياً.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: In KSA, UAE, and Egypt, static creator promo codes (`SARA15`, `NOOR20`) are scraped within hours by coupon websites, browser extensions, and Telegram channels; organic shoppers already at checkout paste the leaked code, and naive last-touch/code-based AI attribution credits the influencer for 100% of those cannibalized organic orders! An OPERATING_FRAMEWORK combining auto-applied deep links, first-touch UTM validation, and 72-hour code expiration windows fixes creator ROI measurement.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-298`, `AMP-308`, `AMP-318`, `AMP-328`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-528`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever issuing promo codes or affiliate links to influencers in KSA, UAE, or Egypt on Salla, Zid, Shopify, WooCommerce, or custom apps.
- **داعي الاستخدام (AR)**: تُستخدم عند إصدار أكواد خصم أو روابط إحالة للمؤثرين على سلة أو زد أو شوبيفاي أو ووكومرس في السعودية والإمارات ومصر.
- **Do NOT Use When**: Never pay creator commission or evaluate influencer ROAS on `Total Orders Using Promo Code X` without splitting `Click-Verified Influencer Sessions` vs. `Zero-Click Checkout Code Paste`.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Storefront Auto-Apply Discount URL structure (e.g., `https://store.sa/discount/SARA15?redirect=/collections/best&utm_source=snapchat&utm_medium=influencer&utm_campaign=sara_oct26`)
   - GA4 / Backend Order Attribution Table (`first_user_source_medium`, `session_source_medium`, `coupon_code`, `time_from_landing_to_checkout`)
   - Creator Burst Window (`48–72 hours` post-story)
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
