# Evidence Register & Source Boundaries — `FW-042` (`AMP-185`)

- **Framework Title (EN)**: Arabic BPE Tokenization Cost, Latency & `max_output_tokens` Budgeting Decision Aid
- **عنوان الأصل (AR)**: أداة حساب وموازنة تضخم التوكنات (`Tokenization Inflation`) وحدود `max_output_tokens` في أنابيب المحتوى العربي
- **Channel**: Content Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-039` | [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral. | Amazon.sa, Amazon.ae, and Noon KSA/UAE/Egypt marketplace rules as of Oct 2026. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-018` | [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) | OpenAI | `2026-08-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Strict JSON Schema enforcement (strict: true) guarantees schema compliance in GPT-4o, GPT-4.1, and o3, unlike legacy JSON mode or free-text prompting. | Prevents syntax errors in MarTech webhooks, though semantic accuracy still requires validation. |
| `SRC-019` | [o3 Model | OpenAI API](https://developers.openai.com/api/docs/models/o3) | OpenAI | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Documents reasoning token behavior, 100k max output tokens, structured output support, and knowledge cutoff boundaries necessitating live grounding for 2026 regulations. | Reasoning models have higher latency/cost than mini models for simple routing. |
| `SRC-018` | [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) | OpenAI | `2026-08-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | OpenAI's Structured Outputs documentation notes that if generation reaches `max_completion_tokens` (`finish_reason: length`), the JSON output will be incomplete/invalid. | Fallback: Always check `finish_reason != 'length'` before parsing JSON and size `max_completion_tokens` using the `3.8x` (unvocalized) or `6.5x` (vocalized) Arabic word multiplier. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Content Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not set tight `max_output_tokens` caps based on English word-count estimates when requesting `response_format: {type: 'json_schema'}` in Arabic—truncated JSON invalidates the entire API call. / لا تضع سقفاً ضيقاً لـ `max_output_tokens` مبنياً على تقديرات الكلمات الإنجليزية عند طلب مخرجات `JSON Schema` بالعربية؛ لأن انقطاع النص يفسد استجابة الـ API بالكامل.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Content Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
