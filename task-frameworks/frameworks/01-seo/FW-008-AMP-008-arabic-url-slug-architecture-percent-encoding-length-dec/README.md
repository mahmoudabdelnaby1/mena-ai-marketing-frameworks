# `FW-008` — Arabic URL Slug Architecture & Percent-Encoding Length Decision Aid
## أداة القرار المعماري لروابط صفحات الويب العربية (`URL Slugs`) ومنع انفجار الترميز المئوي (`%D8%`)

- **One-Sentence Promise (EN)**: Choose and enforce a URL slug convention that prevents 6x UTF-8 percent-encoding expansion from breaking WordPress's 200-char database limit and GA4's 420-char `page_location` cap.
- **الوعد التطبيقي في جملة واحدة (AR)**: اختيار وتطبيق معمارية روابط (`URL Slugs`) تمنع تضخم الحروف العربية بالترميز المئوي (6 أضعاف) من كسر حد ووردبريس (200 حرف) وحد GA4 البالغ 420 حرفاً.
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: Choosing between ASCII English slugs under `/ar/`, transliterated slugs, or ultra-short 3-word Arabic slugs is an architectural decision with hard byte thresholds (200 chars in WordPress `post_name`, 420 chars in GA4 `page_location`); a quantitative DECISION_AID makes the threshold math unmistakable.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-020`, `AMP-032`, `AMP-044`, `AMP-056`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-506`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when launching a new Arabic/bilingual website, migrating a store, or configuring AI blog/product publishing pipelines in WordPress, Shopify, Salla, Zid, or Next.js.
- **داعي الاستخدام (AR)**: تُستخدم عند إطلاق موقع عربي أو ثنائي اللغة، أو ترحيل متجر، أو ضبط أنابيب النشر الآلي بالذكاء الاصطناعي على ووردبريس أو شوبيفاي أو سلة أو زد.
- **Do NOT Use When**: Do not bulk-change URL slugs on existing high-ranking Arabic pages without a 1:1 `301` redirect map and canonical update—only rewrite existing slugs if they are actively truncated or broken.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - CMS / E-Commerce platform (`WordPress/WooCommerce`, `Salla`, `Zid`, `Shopify`, `Custom Next.js`)
   - Average query parameter length appended by paid ads (`?utm_source=...&fbclid=...&gclid=...`, typically 120–180 ASCII chars)
   - Target page title in Arabic and English
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `DECISION_AID` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `DECISION_AID` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
