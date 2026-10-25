# `FW-009` — Amazon.sa & Amazon.eg 250-Byte UTF-8 Arabic Generic Keyword Compressor Prompt & Script
## قالب وأداة ضغط الكلمات المفتاحية الخفية (`Generic Keywords`) لمتاجر `Amazon.sa` و`Amazon.eg` تحت حد 250 بايت (`UTF-8`)

- **One-Sentence Promise (EN)**: Generate and byte-verify hidden `Generic Keywords` for `Amazon.sa`, `Amazon.ae`, and `Amazon.eg` that stay strictly under Amazon's `<250 UTF-8 bytes` limit (~22–26 Arabic words).
- **الوعد التطبيقي في جملة واحدة (AR)**: توليد وفحص حقل الكلمات المفتاحية الخفية (`Generic Keywords`) في أمازون السعودية والإمارات ومصر بحيث لا يتجاوز الحد الصارم (`249 بايت UTF-8` أي حوالي 22–26 كلمة عربية).
- **Selected Artifact Type**: `PROMPT_TEMPLATE` *(Chosen because: Marketers routinely confuse 250 characters with 250 UTF-8 bytes when prompting LLMs for Amazon backend keywords (causing Amazon Seller Central to drop the entire field because Arabic letters consume 2 bytes each); a PROMPT_TEMPLATE paired with an exact UTF-8 byte-counter script guarantees compliance.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-021`, `AMP-033`, `AMP-045`, `AMP-057`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-505`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when populating the backend `Generic Keywords` (`الكلمات المفتاحية العامة`) field in Amazon Seller Central for `Amazon.sa`, `Amazon.ae`, or `Amazon.eg`.
- **داعي الاستخدام (AR)**: يُستخدم عند تعبئة حقل الكلمات المفتاحية الخفية (`Generic Keywords`) في حساب البائع على `Amazon.sa` أو `Amazon.ae` أو `Amazon.eg`.
- **Do NOT Use When**: Do not repeat words already present in the visible Product Title or Bullet Points—Amazon indexes title/bullet words automatically, so repeating them wastes scarce UTF-8 bytes.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Final Arabic Product Title (`<=75` chars per `AMP-010`) and 5 Bullet Points (so the prompt excludes already-used words)
   - Target Marketplace (`Amazon.sa` KSA, `Amazon.ae` UAE, or `Amazon.eg` Egypt)
   - Regional synonym & dialect list (e.g., Saudi vs. Egyptian terms, common misspellings without Hamza)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `PROMPT_TEMPLATE` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `PROMPT_TEMPLATE` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
