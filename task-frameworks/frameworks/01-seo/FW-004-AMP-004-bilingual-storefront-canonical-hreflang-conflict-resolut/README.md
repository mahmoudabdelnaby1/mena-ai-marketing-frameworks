# `FW-004` — Bilingual Storefront Canonical & Hreflang Conflict Resolution Checklist (Salla, Zid & Custom MENA Stores)
## قائمة فحص وإصلاح تضارب `canonical` و`hreflang` في المتاجر ثنائية اللغة (العربية والإنجليزية)

- **One-Sentence Promise (EN)**: Detect and resolve cross-language canonical conflicts where `/en/` product pages canonicalize back to `/ar/` URLs while `hreflang` claims they are indexable alternates.
- **الوعد التطبيقي في جملة واحدة (AR)**: كشف وإصلاح التضارب التقني حين تشير علامة `canonical` في الصفحات الإنجليزية (`/en/`) إلى الرابط العربي (`/ar/`) بينما تطلب علامات `hreflang` فهرستها.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Cross-language canonical contradiction is a binary HTML `<head>` defect (found on 6 out of 6 English-enabled Salla stores in VOCTOS's Oct 2026 audit); a technical CHECKLIST with exact HTML inspection and Cloudflare Worker/theme override patterns fixes it cleanly.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-016`, `AMP-028`, `AMP-040`, `AMP-052`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever enabling English (`/en/`) alongside Arabic (`/ar/`) on Salla, Zid, Shopify Markets, or WooCommerce WPML/Polylang in KSA, UAE, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند تفعيل اللغة الإنجليزية (`/en/`) بجانب العربية (`/ar/`) على منصات سلة أو زد أو شوبيفاي أو ووكومرس في السعودية أو الإمارات أو مصر.
- **Do NOT Use When**: Do not enable `/en/` storefront routes if English titles and descriptions are not actually translated (`AMP-005`)—keep the store single-language Arabic until English copy is ready.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Sample pair of live Arabic and English product URLs (e.g., `https://store.sa/ar/p1` and `https://store.sa/en/p1`)
   - Raw HTML `<head>` source (fetched via `curl -s` or View Source, not rendered DOM alone)
   - Cloudflare DNS/Proxy access (if running a managed SaaS storefront that requires HTML edge rewriting)
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
