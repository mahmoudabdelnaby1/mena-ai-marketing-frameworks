# `FW-036` — Vision 2030, GASTAT, CAPMAS & Central Bank Citation Grounding Workflow (Anti-Hallucination)
## مسار عمل توثيق إحصاءات رؤية 2030 والهيئة العامة للإحصاء (`GASTAT`) والجهاز المركزي (`CAPMAS`) ومنع هلوسة الأرقام

- **One-Sentence Promise (EN)**: Prevent LLMs from fabricating fake percentages attributed to Saudi Vision 2030, GASTAT, SAMA, CST, UAE FCSC, or Egypt CAPMAS/CBE by enforcing quote-first retrieval and an explicit `'UNVERIFIED_STAT'` abstain gate.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع النماذج اللغوية من اختلاق نسب مئوية وإحصاءات وهمية ونسبتها زوراً لرؤية السعودية 2030 أو الهيئة العامة للإحصاء (`GASTAT`) أو البنك المركزي أو الجهاز المركزي للتعبئة العامة والإحصاء (`CAPMAS`).
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: When writers ask an LLM for 'a statistic about Saudi e-commerce growth under Vision 2030 or Egyptian fintech adoption', the model fabricates plausible percentages (`'84.3% according to GASTAT 2026'`) unless constrained by Anthropic/OpenAI's quote-first grounding workflow; an OPERATING_FRAMEWORK enforces verbatim source extraction first.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-189`, `AMP-199`, `AMP-209`, `AMP-219`, `AMP-229`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-519`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when drafting B2B whitepapers, investor/board decks, PR press releases, LinkedIn thought leadership, or SEO authority articles citing MENA economic/market statistics.
- **داعي الاستخدام (AR)**: تُستخدم عند كتابة التقارير، العروض التقديمية، البيانات الصحفية، أو المقالات المتخصصة التي تستشهد بإحصاءات اقتصادية أو حكومية في السعودية والإمارات ومصر.
- **Do NOT Use When**: Never allow an LLM to generate a statistic from its internal weights without a verified URL/PDF excerpt attached in the context window.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Verified Primary Source Excerpts or PDFs (e.g., official GASTAT, SAMA, CST, Vision 2030 Annual Report, CAPMAS, CBE, DataReportal, or VOCTOS/23HubLab study text)
   - Topic & Target Audience of the article or whitepaper
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
