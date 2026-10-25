# Strict JSON Schema Enforcement Workflow for Arabic CRM, Webhook & Catalog Automations (`strict: true` / `responseSchema`)
## <span dir="rtl">مسار عمل فرض مخرجات `JSON Schema` الصارمة (`strict: true`) في أتمتة الـ CRM والويب هوك والكتالوجات العربية</span>

> **Asset ID**: `FW-087` (`AMP-445`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Marketing Automation | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Eliminate crashed Make/Zapier/n8n/Python webhooks caused by LLMs wrapping Arabic JSON in conversational prose (`'بالتأكيد! إليك ملف JSON:'`), changing key names into Arabic, or truncating strings (`AMP-185`).
- **AR**: <span dir="rtl">القضاء نهائياً على تعطل أنابيب الأتمتة (`Make / Zapier / n8n / Webhooks`) الناتج عن إضافة النموذج اللغوي لمقدمات حوارية («بالتأكيد! إليك النتيجة:») أو ترجمة مفاتيح الـ JSON للعربية أو كسر الأقواس.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever connecting an LLM API (`OpenAI`, `Gemini`, `Claude`) to a CRM (`HubSpot`, `Salesforce`, `Zoho`), e-commerce catalog (`Salla`, `Zid`, `Shopify`), or automation platform (`n8n`, `Make`, `Zapier`).
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند ربط واجهات برمجة النماذج اللغوية بأنظمة إدارة العملاء (`CRM`) أو المتاجر الإلكترونية أو منصات الأتمتة (`n8n`, `Make`, `Zapier`).</span>
- **When NOT to Use It (EN)**: Never rely on regex stripping (`text.replace('```json', '')`) on free-text LLM completions for production webhooks—use native API-level Structured Outputs!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تعتمد على المخرجات النصية الحرة مع محاولة تنظيفها بـ Regex في بيئات الإنتاج؛ فعّل دائماً `json_schema` الصارم من داخل إعدادات الـ API.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Downstream Webhook / CRM Field Schema (exact ASCII field names and allowed `enum` values)
- Arabic Input Payload (e.g., inbound WhatsApp message, lead form note, or raw product text)
- Token budget calculation (`AMP-185` — ensuring `max_completion_tokens >= 1024` so Arabic strings never clip)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### API-Level Strict JSON Schema Blueprint for Arabic Marketing Pipelines

#### 1. The 4 Golden Rules of Arabic Structured Outputs
1. **Enable Native `json_schema` (`strict: true`) / `responseSchema` at the API Level**:
   - **OpenAI (`GPT-4o / GPT-4.1 / o3`)**: Pass `response_format={"type": "json_schema", "json_schema": {"name": "...", "strict": True, "schema": {...}}}` with `"additionalProperties": False` and every property listed in `"required"`.
   - **Google Gemini (`Gemini 2.5 Pro / Flash`)**: Pass `generation_config={"response_mime_type": "application/json", "response_schema": ...}`.
   - **Anthropic Claude (`Claude 3.7/4 Sonnet`)**: Define a single tool with `input_schema` and force `tool_choice={"type": "tool", "name": "emit_structured_lead"}`.
2. **Keep All JSON Keys & Enum Constants in Strict ASCII English**:
   - Never name a JSON key `"المدينة"` or allow free-text Arabic enum values (`"الرياض"` vs `"مدينة الرياض"` vs `"رياظ"`)—use `"city_code": {"type": "string", "enum": ["RIYADH", "JEDDAH", "DAMMAM", "DUBAI", "CAIRO", "OTHER"]}` while putting the natural Arabic reply in `"customer_reply_ar"`!
3. **Check `finish_reason` & `refusal` Before Calling `json.loads()`**:
   - Even with `strict: true`, if `finish_reason == "length"` (`AMP-185`) or `message.refusal` is populated, the JSON string is not parsed directly; handle both branches explicitly in code!

#### 2. Copy-Ready Python Production Wrapper (OpenAI / Gemini Strict Arabic Lead Router)
```python
import json

LEAD_ROUTING_JSON_SCHEMA = {
    "name": "mena_lead_triage_payload",
    "strict": True,
    "schema": {
        "type": "object",
        "properties": {
            "intent_category": {
                "type": "string",
                "enum": ["READY_TO_BUY", "PRICE_INQUIRY", "ORDER_STATUS_DELAY", "OPT_OUT_STOP", "SPAM_IRRELEVANT"]
            },
            "detected_country_iso": {
                "type": "string",
                "enum": ["SA", "AE", "EG", "KW", "QA", "BH", "OM", "UNKNOWN"]
            },
            "normalized_phone_e164": {"type": ["string", "null"]},
            "escalate_to_human": {"type": "boolean"},
            "polite_reply_ar": {"type": "string"}
        },
        "required": [
            "intent_category",
            "detected_country_iso",
            "normalized_phone_e164",
            "escalate_to_human",
            "polite_reply_ar"
        ],
        "additionalProperties": False
    }
}

def parse_strict_llm_response(api_response_choice) -> dict:
    if getattr(api_response_choice, "finish_reason", "stop") == "length":
        raise RuntimeError("TOKEN_TRUNCATION_AMP_185: Increase max_completion_tokens (>= 2048 for Arabic).")
    msg = api_response_choice.message
    if getattr(msg, "refusal", None):
        return {
            "intent_category": "SPAM_IRRELEVANT",
            "detected_country_iso": "UNKNOWN",
            "normalized_phone_e164": None,
            "escalate_to_human": True,
            "polite_reply_ar": "شكراً لتواصلك معنا، سيقوم أحد ممثلي خدمة العملاء بالرد عليك قريباً."
        }
    return json.loads(msg.content)
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Pipeline**: n8n / Python Webhook receiving 2,500 daily inbound Instagram & WhatsApp messages across KSA and Egypt, routing them into HubSpot CRM.
- **Previous Failure**: Used a standard free-text prompt (`"Return JSON"`). `140` times per day (`5.6%` failure rate), the model returned `"بالتأكيد! إليك تحليل الرسالة:
```json
{...}"` or translated `"intent_category"` into `"فئة_النية"`, crashing the HubSpot webhook and dropping hot buyer leads.

### Step B: Initial Output (`المخرج الأولي`)
- **Output with `LEAD_ROUTING_JSON_SCHEMA` (`strict: True`) on Inbound Message `"بكم التوصيل لحي الملقا بالرياض؟ جوالي ٠٥٥١٢٣٤٥٦٧"`**:
```json
{
  "intent_category": "PRICE_INQUIRY",
  "detected_country_iso": "SA",
  "normalized_phone_e164": "+966551234567",
  "escalate_to_human": false,
  "polite_reply_ar": "حياك الله! التوصيل لحي الملقا بالرياض مجاني للطلبات فوق 250 ر.س ويصلك خلال 24 ساعة. تفضل رابط الطلب المباشر:"
}
```

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Locked Picklist `enum` Values to Exact HubSpot Internal Property Values**: Matched `["SA", "AE", "EG", ...]` 1:1 with HubSpot's dropdown internal values so `PATCH /crm/v3/objects/contacts` never rejects a non-matching Arabic city string.
2. **Added `AMP-123` & `AMP-233` Intent Hooks**: Mapped `"OPT_OUT_STOP"` directly to the cross-channel suppression webhook (`AMP-233`).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Webhook JSON parse failure rate dropped from `5.6%` (`140 crashed leads/day`) to **`0.00%`** across `75,000+` consecutive Arabic messages.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A developer sets `response_format: {type: 'json_object'}` (legacy JSON mode) instead of `{type: 'json_schema', strict: true}`; the model outputs valid JSON syntax (`{"النية": "شراء"}`), which still crashes the CRM webhook because the key name changed from `intent_category` to `النية`!
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always use **`type: "json_schema"` with `strict: true`** (OpenAI) or **`responseSchema`** (Gemini), never legacy unconstrained `type: "json_object"`.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **OpenAI Structured Outputs (`strict: true` JSON Schema) & Google Gemini `responseSchema`** | `supported` | [Official Docs](https://developers.openai.com/api/docs/guides/structured-outputs) (`2026-10-25`) | Confirmed via OpenAI and Google Gemini API documentation: constrained decoding guarantees the output matches the supplied JSON Schema keys, types, and enums. | Always check `finish_reason != 'length'` (`AMP-185`) and `refusal == null` before parsing. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Webhook JSON Schema Validation Pass Rate (`Target: 100.0%`) and Zero dropped CRM leads from malformed LLM output.
- **Baseline**: Prior 30-day webhook `JSONDecodeError` / `KeyError` exception count.
- **Observation Window**: Monitored continuously in worker error logs.
- **Interpretation Boundary**: Strict JSON Schema guarantees structural integrity, while system prompt rules (`AMP-123`) govern semantic classification accuracy.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) — *OpenAI* (Published `2026-08-01`, Accessed `2026-10-25`): Strict JSON Schema enforcement (strict: true) guarantees schema compliance in GPT-4o, GPT-4.1, and o3, unlike legacy JSON mode or free-text prompting.
- [Structured outputs - Interactions API - Google AI for Developers](https://ai.google.dev/gemini-api/docs/structured-output) — *Google AI for Developers* (Published `2026-10-21`, Accessed `2026-10-25`): Gemini API supports strict JSON Schema outputs for predictable downstream CRM, catalog, and ad-feed automation.
