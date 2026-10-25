# `FW-006` — Zid & MENA Storefront `robots.txt` Sitemap Directive & AI-Crawler Governance Checklist
## قائمة فحص ملف `robots.txt` وإعلان `Sitemap:` وضبط زواحف الذكاء الاصطناعي في متاجر زد والمنطقة

- **One-Sentence Promise (EN)**: Verify `Sitemap:` directive presence and intentional AI-crawler rules (`GPTBot`, `ClaudeBot`, `Google-Extended`, `PerplexityBot`) in storefront `robots.txt` files.
- **الوعد التطبيقي في جملة واحدة (AR)**: التحقق من وجود سطر `Sitemap:` في ملف `robots.txt` وضبط صلاحيات زواحف الذكاء الاصطناعي (`GPTBot`، `ClaudeBot`، `Google-Extended`) بوعي.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: VOCTOS's Oct 2026 audit of 10 Zid stores proved that 9 of 10 stores lacked a `Sitemap:` line in their 1,268-line default `robots.txt` (while allowing `GPTBot`/`ClaudeBot` and blocking `PetalBot`); a concise CHECKLIST prevents blind assumptions and ensures proper sitemap discovery.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-018`, `AMP-030`, `AMP-042`, `AMP-054`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use during technical SEO onboarding for any Zid, Salla, Shopify, or WooCommerce store in KSA, UAE, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند التهيئة التقنية للـ SEO لأي متجر على زد أو سلة أو شوبيفاي أو ووكومرس في السعودية أو الإمارات أو مصر.
- **Do NOT Use When**: Do not assume blocking `Google-Extended` blocks Google Search indexing—`Googlebot` controls Search & AI Overviews indexing, while `Google-Extended` controls Gemini training/grounding.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Live `https://store-domain.com/robots.txt` output
   - Verified `sitemap.xml` URL (`200 OK`)
   - Google Search Console & Bing Webmaster Tools property access
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
