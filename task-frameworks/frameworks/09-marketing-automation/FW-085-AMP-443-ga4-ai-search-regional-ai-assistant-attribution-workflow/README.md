# `FW-085` — GA4 AI Search & Regional AI Assistant Attribution Workflow (Capturing the 96.9% in Organic Search + Custom Regex for Perplexity, Claude & HUMAIN Chat)
## مسار عمل تتبع إحالات محركات الذكاء الاصطناعي في `GA4` (رصد الـ `96.9%` المسجلة داخل البحث العضوي + فصل `Perplexity` و`Claude` و`HUMAIN Chat` من الإحالات)

- **One-Sentence Promise (EN)**: Stop under-counting AI search traffic by 30x in GA4 by combining a Custom Channel Group regex (capturing `Perplexity`, `Claude`, `HUMAIN Chat`, `Poe`, `You.com` alongside `ChatGPT`/`Gemini`/`DeepSeek`/`Copilot`/`Grok`) with a Google Search Console AI-Overview landing-page join.
- **الوعد التطبيقي في جملة واحدة (AR)**: إيقاف فقدان 96.9% من زيارات بحث الذكاء الاصطناعي في تقارير `GA4` عبر الجمع بين قاعدة Regex مخصصة (تلتقط `Perplexity` و`Claude` و`HUMAIN Chat` التي تسقط في `Referral`) وربط صفحات الهبوط مع تقارير `Search Console`.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: VOCTOS's landmark October 2026 GA4 study in Arab markets proved two critical facts: (1) GA4's default `AI Assistant` channel (introduced 13 May 2026) only matches a narrow list of chatbot referrers (`ChatGPT`, `Gemini`, `DeepSeek`, `Copilot`, `Grok`) while dropping `Perplexity.ai`, `Claude.ai`, and Saudi Arabia's `HUMAIN Chat` into generic `Referral`, and (2) **96.9% of measured AI search clicks** for studied Saudi properties arrived from **Google `AI Overviews` and `AI Mode`**, which Google records inside **`Organic Search`** (NOT in `AI Assistant`!)! Looking only at GA4's default `AI Assistant` row misses 96.9% of AI search traffic.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-453`, `AMP-463`, `AMP-473`, `AMP-483`, `AMP-493`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever configuring Google Analytics 4 (`GA4`) or reporting on AI Search (`AEO / GEO`) traffic and conversions in KSA, UAE, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد تقارير `GA4` أو قياس زيارات وتحويلات محركات الذكاء الاصطناعي في السعودية والإمارات ومصر.
- **Do NOT Use When**: Never show a client GA4's default `AI Assistant` channel row (`e.g., 45 sessions`) and tell them 'that is 100% of your AI search traffic'—that omits 96.9% of AI citations coming through Google `AI Overviews` / `AI Mode` + `Perplexity`/`Claude`/`HUMAIN`!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - GA4 Admin access (`Admin -> Data display -> Channel groups -> Create new channel group`)
   - Google Search Console (`GSC`) linked to GA4 / BigQuery export
   - List of informational/comparison landing pages optimized for AEO (`AMP-180`)
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
