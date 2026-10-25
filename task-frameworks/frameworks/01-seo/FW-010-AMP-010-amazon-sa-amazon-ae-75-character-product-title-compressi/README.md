# `FW-010` — Amazon.sa & Amazon.ae 75-Character Product Title Compression Prompt & Policy Template
## قالب صياغة وضغط عناوين منتجات `Amazon.sa` و`Amazon.ae` ضمن السقف الرسمي (75 حرفاً) لمنع إعادة الكتابة الآلية

- **One-Sentence Promise (EN)**: Craft high-converting Arabic and English Amazon product titles strictly within the 75-character policy cap so Amazon does not truncate or auto-rewrite your title after 14 days.
- **الوعد التطبيقي في جملة واحدة (AR)**: صياغة عناوين منتجات أمازون السعودية والإمارات ضمن السقف الرسمي (75 حرفاً) لمنع بتر العنوان أو تغييره تلقائياً بواسطة ذكاء أمازون الاصطناعي بعد 14 يوماً.
- **Selected Artifact Type**: `CONTENT_TEMPLATE` *(Chosen because: Amazon's June/July 2026 title policy update enforces a 75-character cap on Saudi and UAE Seller Central policy pages and replaces non-compliant titles automatically after 14 days; a strict CONTENT_TEMPLATE with slot budgets lets catalog managers write compliant titles every time.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-022`, `AMP-034`, `AMP-046`, `AMP-058`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-504`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when creating or updating ASIN titles on `Amazon.sa`, `Amazon.ae`, or `Amazon.eg` via Seller Central or Vendor Central.
- **داعي الاستخدام (AR)**: يُستخدم عند إنشاء أو تحديث عناوين المنتجات (`Product Title`) على `Amazon.sa` أو `Amazon.ae` أو `Amazon.eg`.
- **Do NOT Use When**: Do not stuff promotional phrases (`شحن مجاني`, `أفضل مبيعاً`, `خصم 50%`), symbols (`!`, `*`, `؟`), or repeat the same root word more than twice in an Amazon title—both violate Amazon policy regardless of character length.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Brand Name (Arabic & English)
   - Core Product Noun (highest search-volume native term from `AMP-001`)
   - 1–2 Defining Specs (Capacity/Size/Power/Material + Color/Count)
   - Bullet Point #1 & Backend Generic Keywords (`AMP-009`) to hold overflow attributes
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `CONTENT_TEMPLATE` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `CONTENT_TEMPLATE` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
