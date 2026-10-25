# End-to-End Worked Example & Failure Recovery — `FW-042` (`AMP-185`)

- **Framework**: Arabic BPE Tokenization Cost, Latency & `max_output_tokens` Budgeting Decision Aid
- **العنوان بالعربية**: أداة حساب وموازنة تضخم التوكنات (`Tokenization Inflation`) وحدود `max_output_tokens` في أنابيب المحتوى العربي
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Pipeline**: Multi-client Agency Catalog Pipeline generating bilingual (`AR + EN`) descriptions + 5 bullets + FAQ for `5,000` Zid/Salla SKUs via OpenAI `GPT-4o` Structured Outputs (`strict: true`).
- **Problem**: Developer copied `max_completion_tokens: 700` from their US Shopify script. `64%` of Arabic API calls failed with `finish_reason: "length"` and broken JSON because the bilingual + Arabic output required `~1,450` completion tokens per SKU.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Sizing Calculation via `calculate_arabic_max_tokens(target_arabic_words=320, has_tashkeel=False, json_fields=8)`**:
  - Recommended `max_completion_tokens`: **`1,776` tokens** (Configured to **`2,048` tokens** in production with explicit check `if response.choices[0].finish_reason == "length": retry_with_higher_cap()`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Added `finish_reason` Assertion**: Added a mandatory assertion in the Python worker: before running `json.loads()`, check `choice.finish_reason == "stop"` (OpenAI) or `stop_reason == "end_turn"` (Claude) / `finish_reason == "STOP"` (Gemini).
2. **Switched Bulk Non-Realtime Jobs to Batch API (50% Cost Discount)**: Because Arabic tokenization increases token volume by `~2.2x`, routed overnight catalog runs through OpenAI/Anthropic Batch API (`50%` token cost reduction) to neutralize the Arabic token premium.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Truncation failure rate dropped from `64%` to **`0.0%`** across all 5,000 SKUs, while Batch API routing offset the 2.2x Arabic token multiplier.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A voiceover automation script passes a 400-word Arabic script to an LLM asking for full Tashkeel (`حركات التشكيل الكاملة`) with `max_tokens: 800`; because every fatḥah/kasrah/ḍammah adds extra tokens, the vocalized script cuts off halfway through the video.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  When requesting full Arabic Tashkeel (`AMP-332`), multiply your token budget by **`6.5x`** the word count and process scripts in `<= 150-word` chunks.
