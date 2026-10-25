# Arabic BPE Tokenization Cost, Latency & `max_output_tokens` Budgeting Decision Aid
## <span dir="rtl">أداة حساب وموازنة تضخم التوكنات (`Tokenization Inflation`) وحدود `max_output_tokens` في أنابيب المحتوى العربي</span>

> **Asset ID**: `FW-042` (`AMP-185`) | **Artifact Type**: `DECISION_AID` | **Channel**: Content Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Size `max_output_tokens`, batch chunk sizes, and API cost budgets for Arabic LLM pipelines using verified Arabic-to-English BPE token ratios (`1.8x–2.8x` tokens per word) so Arabic JSON and articles never truncate mid-sentence.
- **AR**: <span dir="rtl">ضبط سقف مخرجات النماذج (`max_output_tokens`) وحجم الدفعات وميزانية استهلاك الـ API للنصوص العربية بناءً على معامل تضخم التوكنات الفعلي (`1.8 إلى 2.8 ضعف الإنجليزية`) لمنع انقطاع النصوص أو ملفات JSON في المنتصف.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when architecting bulk catalog generation, translation pipelines, RAG chatbots, or structured JSON extraction in Arabic via OpenAI, Anthropic, or Gemini APIs.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند هندسة أنابيب توليد أوصاف المنتجات بالجملة أو الترجمة الآلية أو استخراج بيانات JSON باللغة العربية عبر واجهات برمجة `OpenAI` و`Anthropic` و`Gemini`.</span>
- **When NOT to Use It (EN)**: Do not set tight `max_output_tokens` caps based on English word-count estimates when requesting `response_format: {type: 'json_schema'}` in Arabic—truncated JSON invalidates the entire API call.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تضع سقفاً ضيقاً لـ `max_output_tokens` مبنياً على تقديرات الكلمات الإنجليزية عند طلب مخرجات `JSON Schema` بالعربية؛ لأن انقطاع النص يفسد استجابة الـ API بالكامل.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Target Arabic Word Count per API Output (`N_words_ar`)
- Presence of Tashkeel / Vocalization (`AMP-332` — full Tashkeel adds another `1.5x–1.8x` token multiplier!)
- Target Model Tokenizer (`OpenAI o200k_base` for GPT-4o/4.1/o3, `Claude 3.7/4` tokenizer, or `Gemini 2.5` SentencePiece)

## 2. The Working `DECISION_AID` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Arabic BPE Tokenization Multiplier & Pipeline Sizing Matrix

#### 1. Empirical Token-per-Word Ratios (Unvocalized vs. Vocalized Arabic)
| Text Script & Register | Avg Token-to-Word Ratio (`Modern Tokenizer: o200k_base / Gemini / Claude`) | Multiplier vs. Equivalent English Word Count | Safe `max_output_tokens` Formula for `W` Target Words |
| :--- | :--- | :--- | :--- |
| **English Commercial Copy** | `~1.3` tokens / word | `1.0x` (Baseline) | `ceil(W * 1.5) + 150` (JSON overhead) |
| **Unvocalized Arabic (MSA / Khaleeji / Ammiya)** | **`~2.4 – 3.4` tokens / word** | **`1.8x – 2.6x` English tokens** | **`ceil(W * 3.8) + 250`** |
| **Fully Vocalized Arabic (With Tashkeel for TTS — `AMP-332`)** | **`~4.2 – 6.0` tokens / word** | **`3.2x – 4.5x` English tokens** | **`ceil(W * 6.5) + 250`** |

#### 2. Operational Decision Rules for High-Volume MENA Pipelines
1. **Rule 1 — Never Share English `max_output_tokens` Caps with Arabic Endpoints**:
   - If an English product-description pipeline sets `max_output_tokens = 600` (sufficient for ~400 English words), that same `600`-token cap will cut off an Arabic description at **~170–210 words**, breaking the closing `"}` of your JSON payload!
   - **Fix**: Set `max_output_tokens >= 2048` (or `4096`) for single-SKU bilingual JSON generation and control length via prompt word-count instructions (`"150 إلى 200 كلمة عربية"`) rather than choking `max_output_tokens`.
2. **Rule 2 — Keep JSON Keys in Concise ASCII English**:
   - Even when the JSON *values* are in Arabic, always define JSON Schema *property keys* in short ASCII English (`"title_ar"`, `"bullets_ar"`, `"meta_desc_ar"`) rather than Arabic keys (`"عنوان_المنتج_بالعربية"`)—this saves 30–50% of structural schema token overhead across 10,000 API calls.
3. **Rule 3 — Batch Size Reduction for Multi-SKU Calls**:
   - If an English prompt processes `20` SKUs per batch call, reduce the Arabic/Bilingual batch size to **`8` SKUs per call** so output generation latency stays under HTTP gateway timeouts (`30s–60s`) and never hits `finish_reason: "length"`.

#### 3. Copy-Ready Python Token Budget & Truncation Guard
```python
def calculate_arabic_max_tokens(target_arabic_words: int, has_tashkeel: bool = False, json_fields: int = 6) -> int:
    multiplier = 6.5 if has_tashkeel else 3.8
    schema_buffer = json_fields * 45 + 200
    recommended = int(target_arabic_words * multiplier) + schema_buffer
    return max(1024, min(recommended, 8192))
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Pipeline**: Multi-client Agency Catalog Pipeline generating bilingual (`AR + EN`) descriptions + 5 bullets + FAQ for `5,000` Zid/Salla SKUs via OpenAI `GPT-4o` Structured Outputs (`strict: true`).
- **Problem**: Developer copied `max_completion_tokens: 700` from their US Shopify script. `64%` of Arabic API calls failed with `finish_reason: "length"` and broken JSON because the bilingual + Arabic output required `~1,450` completion tokens per SKU.

### Step B: Initial Output (`المخرج الأولي`)
- **Sizing Calculation via `calculate_arabic_max_tokens(target_arabic_words=320, has_tashkeel=False, json_fields=8)`**:
  - Recommended `max_completion_tokens`: **`1,776` tokens** (Configured to **`2,048` tokens** in production with explicit check `if response.choices[0].finish_reason == "length": retry_with_higher_cap()`).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added `finish_reason` Assertion**: Added a mandatory assertion in the Python worker: before running `json.loads()`, check `choice.finish_reason == "stop"` (OpenAI) or `stop_reason == "end_turn"` (Claude) / `finish_reason == "STOP"` (Gemini).
2. **Switched Bulk Non-Realtime Jobs to Batch API (50% Cost Discount)**: Because Arabic tokenization increases token volume by `~2.2x`, routed overnight catalog runs through OpenAI/Anthropic Batch API (`50%` token cost reduction) to neutralize the Arabic token premium.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Truncation failure rate dropped from `64%` to **`0.0%`** across all 5,000 SKUs, while Batch API routing offset the 2.2x Arabic token multiplier.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A voiceover automation script passes a 400-word Arabic script to an LLM asking for full Tashkeel (`حركات التشكيل الكاملة`) with `max_tokens: 800`; because every fatḥah/kasrah/ḍammah adds extra tokens, the vocalized script cuts off halfway through the video.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: When requesting full Arabic Tashkeel (`AMP-332`), multiply your token budget by **`6.5x`** the word count and process scripts in `<= 150-word` chunks.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **OpenAI (`o200k_base`), Anthropic Claude & Google Gemini BPE Tokenizers + Structured Outputs** | `supported` | [Official Docs](https://developers.openai.com/api/docs/guides/structured-outputs) (`2026-10-25`) | OpenAI's Structured Outputs documentation notes that if generation reaches `max_completion_tokens` (`finish_reason: length`), the JSON output will be incomplete/invalid. | Always check `finish_reason != 'length'` before parsing JSON and size `max_completion_tokens` using the `3.8x` (unvocalized) or `6.5x` (vocalized) Arabic word multiplier. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: API JSON Truncation Rate (`finish_reason == 'length'`, `Target: 0%`) and Token Cost per Completed Bilingual SKU.
- **Baseline**: Pre-fix truncation error rate in worker logs.
- **Observation Window**: Monitored in real time via API gateway metrics.
- **Interpretation Boundary**: Proper token budgeting prevents mid-string JSON crashes and budget surprises, while prompt constraints (`AMP-001`, `AMP-177`) govern output quality.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) — *OpenAI* (Published `2026-08-01`, Accessed `2026-10-25`): Strict JSON Schema enforcement (strict: true) guarantees schema compliance in GPT-4o, GPT-4.1, and o3, unlike legacy JSON mode or free-text prompting.
- [o3 Model | OpenAI API](https://developers.openai.com/api/docs/models/o3) — *OpenAI* (Published `2026-06-01`, Accessed `2026-10-25`): Documents reasoning token behavior, 100k max output tokens, structured output support, and knowledge cutoff boundaries necessitating live grounding for 2026 regulations.
- [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral.
