# `FW-013` — MENA Cross-Market Budget Isolation Decision Aid (Preventing the 4–5x Egypt vs. GCC CPM Arbitrage Trap)
## أداة قرار فصل الميزانيات الإعلانية بين مصر والخليج (منع فخ التهام الميزانية بسبب فارق الـ CPM البالغ 4–5 أضعاف)

- **One-Sentence Promise (EN)**: Structure Meta Advantage+ and Google PMax campaign budgets by CPM/AOV tier so automated bidding does not dump 85%+ of regional spend into the lowest-CPM country while starving high-AOV GCC buyers.
- **الوعد التطبيقي في جملة واحدة (AR)**: هيكلة ميزانيات حملات Meta Advantage+ وGoogle PMax حسب شريحة تكلفة الظهور (CPM) ومتوسط سلة الشراء (AOV) لمنع الخوارزمية من ضخ 85%+ من الميزانية في السوق الأرخص وحرمان أسواق الخليج ذات العائد المرتفع.
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: Campaign budget pooling across countries with a 4–5x CPM gap is a structural media-buying architecture decision; a quantitative DECISION_AID with CPM/AOV isolation tiers and budget allocation formulas prevents algorithmic spend starvation.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-071`, `AMP-081`, `AMP-091`, `AMP-101`, `AMP-111`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-511`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever launching Meta Advantage+ Shopping/App/Leads, Google Performance Max, TikTok Smart+, or Snapchat campaigns across 2 or more MENA countries (e.g., UAE + KSA + Egypt).
- **داعي الاستخدام (AR)**: تُستخدم عند إطلاق حملات Meta Advantage+ أو Google PMax أو TikTok أو Snapchat تستهدف أكثر من دولة عربية (مثل الإمارات والسعودية ومصر معاً).
- **Do NOT Use When**: Do not split cities within the same country into micro-budgets if total daily spend cannot support ~50 conversions/week per campaign—isolate by country/CPM tier first.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Target countries and historical CPM / CPC / CPA benchmarks per country
   - Net Delivered Average Order Value (AOV) and Gross Margin per country (accounting for COD return rate in Egypt/KSA)
   - Total monthly media budget and minimum conversion volume threshold (50 conversions/week per campaign)
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
