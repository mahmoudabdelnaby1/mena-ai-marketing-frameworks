# End-to-End Worked Example & Failure Recovery — `FW-087` (`AMP-445`)

- **Framework**: Strict JSON Schema Enforcement Workflow for Arabic CRM, Webhook & Catalog Automations (`strict: true` / `responseSchema`)
- **العنوان بالعربية**: مسار عمل فرض مخرجات `JSON Schema` الصارمة (`strict: true`) في أتمتة الـ CRM والويب هوك والكتالوجات العربية
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Pipeline**: n8n / Python Webhook receiving 2,500 daily inbound Instagram & WhatsApp messages across KSA and Egypt, routing them into HubSpot CRM.
- **Previous Failure**: Used a standard free-text prompt (`"Return JSON"`). `140` times per day (`5.6%` failure rate), the model returned `"بالتأكيد! إليك تحليل الرسالة:
```json
{...}"` or translated `"intent_category"` into `"فئة_النية"`, crashing the HubSpot webhook and dropping hot buyer leads.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

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

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Locked Picklist `enum` Values to Exact HubSpot Internal Property Values**: Matched `["SA", "AE", "EG", ...]` 1:1 with HubSpot's dropdown internal values so `PATCH /crm/v3/objects/contacts` never rejects a non-matching Arabic city string.
2. **Added `AMP-123` & `AMP-233` Intent Hooks**: Mapped `"OPT_OUT_STOP"` directly to the cross-channel suppression webhook (`AMP-233`).

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Webhook JSON parse failure rate dropped from `5.6%` (`140 crashed leads/day`) to **`0.00%`** across `75,000+` consecutive Arabic messages.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A developer sets `response_format: {type: 'json_object'}` (legacy JSON mode) instead of `{type: 'json_schema', strict: true}`; the model outputs valid JSON syntax (`{"النية": "شراء"}`), which still crashes the CRM webhook because the key name changed from `intent_category` to `النية`!
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always use **`type: "json_schema"` with `strict: true`** (OpenAI) or **`responseSchema`** (Gemini), never legacy unconstrained `type: "json_object"`.
