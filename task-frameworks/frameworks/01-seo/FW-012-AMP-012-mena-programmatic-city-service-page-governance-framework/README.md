# `FW-012` — MENA Programmatic City/Service Page Governance Framework (Anti-Scaled Content Abuse)
## الإطار التشغيلي لحوكمة صفحات المدن والخدمات المولدة برمجياً (تجنب عقوبة `Scaled Content Abuse` في جوجل)

- **One-Sentence Promise (EN)**: Decide which regional city/service landing pages deserve standalone URLs and enforce unique local proof requirements so AI page generation never triggers Google's Scaled Content Abuse penalty.
- **الوعد التطبيقي في جملة واحدة (AR)**: تحديد صفحات المدن والخدمات التي تستحق روابط مستقلة وإلزامها ببيانات محلية حقيقية (الرياض، جدة، الدمام، القاهرة، دبي) لمنع الوقوع تحت طائلة سياسة المحتوى المضخم (`Scaled Content Abuse`) في جوجل.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Spinning up hundreds of near-identical city/service pages by swapping `'الرياض'` with `'جدة'` or `'القاهرة'` is an operational governance failure that violates Google's Scaled Content Abuse policy; an OPERATING_FRAMEWORK with hard uniqueness gates prevents site-wide manual or algorithmic demotion.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-024`, `AMP-036`, `AMP-048`, `AMP-060`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-502`
- **Intended Audience**: SEO Specialist, E-Commerce Manager, Content Strategist, Technical SEO Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before launching multi-city or multi-category SEO landing pages across KSA (Riyadh, Jeddah, Dammam/Khobar), UAE (Dubai, Abu Dhabi, Sharjah), or Egypt (Cairo, New Cairo, Sheikh Zayed, Alexandria).
- **داعي الاستخدام (AR)**: يُستخدم قبل إطلاق صفحات هبوط متعددة المدن أو الفئات في السعودية (الرياض، جدة، الدمام/الخبر) أو الإمارات (دبي، أبوظبي، الشارقة) أو مصر (القاهرة، التجمع، الشيخ زايد، الإسكندرية).
- **Do NOT Use When**: Do not generate a standalone city URL if your business has zero distinct operational data (no specific delivery SLA, shipping cost, physical branch, local portfolio, or regulatory license) for that city.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - First-Party Operational Matrix per City (actual branch address, delivery SLA, shipping fee, local municipal/regulatory permit, local project examples)
   - City-Specific Demand & Persona Matrix (e.g., Riyadh enterprise/government focus vs. Jeddah retail/tourism vs. Dammam industrial/B2B)
   - Google Search Console query data confirming distinct city-modifier search demand
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
