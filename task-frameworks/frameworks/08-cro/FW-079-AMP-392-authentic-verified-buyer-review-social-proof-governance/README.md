# `FW-079` — Authentic Verified-Buyer Review & Social Proof Governance Checklist (Eliminating Fake AI Review Widgets)
## قائمة فحص حوكمة التقييمات وإثباتات الثقة الاجتماعية (`Social Proof` — منع ودجات التقييمات الوهمية المولدة بالذكاء الاصطناعي)

- **One-Sentence Promise (EN)**: Remove deceptive AI-generated review widgets and fake `'سارة من الرياض اشترت قبل دقيقتين'` popups that violate Saudi E-Commerce Law, UAE Consumer Protection Law, and Egypt Law 181/2018, replacing them with automated post-delivery WhatsApp verified-buyer review collection.
- **الوعد التطبيقي في جملة واحدة (AR)**: إزالة إضافات التقييمات الوهمية وإشعارات الشراء الزائفة («سارة من الرياض اشترت قبل دقيقتين») التي تخالف نظام التجارة الإلكترونية السعودي وقانون حماية المستهلك الإماراتي والمصري، واستبدالها بنظام جمع تقييمات حقيقية موثقة بعد التسليم عبر واتساب.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: AI store-builder plugins often pre-populate new stores with 50 fake Arabic reviews (`'منتج رائع جداً أنصح به بشدة - محمد العتيبي'`) and fake real-time purchase toast popups; Arab shoppers immediately spot translated-sounding fake reviews, and Saudi Ministry of Commerce / UAE / Egypt CPA laws strictly penalize deceptive commercial representations—making a cleanup + verified-review collection CHECKLIST essential.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-402`, `AMP-412`, `AMP-422`, `AMP-432`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when auditing product pages, landing pages, or app store listings across KSA, UAE, and Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند تدقيق صفحات المنتجات وصفحات الهبوط في السعودية والإمارات ومصر.
- **Do NOT Use When**: Never import scraped AliExpress/Amazon reviews translated by AI into Arabic onto your store, and never run random-timer 'X from Jeddah just bought this' popups.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Audit of installed review & social-proof apps (`Judge.me`, `Loox`, `Salla Reviews`, `Zid Reviews`, `Sales Pop`)
   - Courier `DELIVERED` webhook trigger (`T+3 days after physical delivery`)
   - Saudi `Maroof` (`معروف`) / Saudi Business Center (`المركز السعودي للأعمال - موثق`) badge link
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
