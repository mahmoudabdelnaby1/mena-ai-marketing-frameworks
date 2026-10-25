# `FW-042` — Arabic BPE Tokenization Cost, Latency & `max_output_tokens` Budgeting Decision Aid
## أداة حساب وموازنة تضخم التوكنات (`Tokenization Inflation`) وحدود `max_output_tokens` في أنابيب المحتوى العربي

- **One-Sentence Promise (EN)**: Size `max_output_tokens`, batch chunk sizes, and API cost budgets for Arabic LLM pipelines using verified Arabic-to-English BPE token ratios (`1.8x–2.8x` tokens per word) so Arabic JSON and articles never truncate mid-sentence.
- **الوعد التطبيقي في جملة واحدة (AR)**: ضبط سقف مخرجات النماذج (`max_output_tokens`) وحجم الدفعات وميزانية استهلاك الـ API للنصوص العربية بناءً على معامل تضخم التوكنات الفعلي (`1.8 إلى 2.8 ضعف الإنجليزية`) لمنع انقطاع النصوص أو ملفات JSON في المنتصف.
- **Selected Artifact Type**: `DECISION_AID` *(Chosen because: Developers port English LLM pipeline configs (`max_output_tokens: 500` for a 350-word product description) directly to Arabic without realizing that Arabic script takes 2 bytes per letter in UTF-8 and splits into 1.8x–2.8x more BPE subword tokens per word than English—causing truncated JSON (`Unterminated string`) and 2x+ API cost/latency; a quantitative DECISION_AID fixes pipeline sizing.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-195`, `AMP-205`, `AMP-215`, `AMP-225`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when architecting bulk catalog generation, translation pipelines, RAG chatbots, or structured JSON extraction in Arabic via OpenAI, Anthropic, or Gemini APIs.
- **داعي الاستخدام (AR)**: تُستخدم عند هندسة أنابيب توليد أوصاف المنتجات بالجملة أو الترجمة الآلية أو استخراج بيانات JSON باللغة العربية عبر واجهات برمجة `OpenAI` و`Anthropic` و`Gemini`.
- **Do NOT Use When**: Do not set tight `max_output_tokens` caps based on English word-count estimates when requesting `response_format: {type: 'json_schema'}` in Arabic—truncated JSON invalidates the entire API call.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Target Arabic Word Count per API Output (`N_words_ar`)
   - Presence of Tashkeel / Vocalization (`AMP-332` — full Tashkeel adds another `1.5x–1.8x` token multiplier!)
   - Target Model Tokenizer (`OpenAI o200k_base` for GPT-4o/4.1/o3, `Claude 3.7/4` tokenizer, or `Gemini 2.5` SentencePiece)
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
