# Evidence Register & Source Boundaries — `FW-087` (`AMP-445`)

- **Framework Title (EN)**: Strict JSON Schema Enforcement Workflow for Arabic CRM, Webhook & Catalog Automations (`strict: true` / `responseSchema`)
- **عنوان الأصل (AR)**: مسار عمل فرض مخرجات `JSON Schema` الصارمة (`strict: true`) في أتمتة الـ CRM والويب هوك والكتالوجات العربية
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-018` | [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) | OpenAI | `2026-08-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Strict JSON Schema enforcement (strict: true) guarantees schema compliance in GPT-4o, GPT-4.1, and o3, unlike legacy JSON mode or free-text prompting. | Prevents syntax errors in MarTech webhooks, though semantic accuracy still requires validation. |
| `SRC-024` | [Structured outputs - Interactions API - Google AI for Developers](https://ai.google.dev/gemini-api/docs/structured-output) | Google AI for Developers | `2026-10-21` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Gemini API supports strict JSON Schema outputs for predictable downstream CRM, catalog, and ad-feed automation. | Requires explicit schema definition in API calls. |
| `SRC-018` | [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) | OpenAI | `2026-08-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Confirmed via OpenAI and Google Gemini API documentation: constrained decoding guarantees the output matches the supplied JSON Schema keys, types, and enums. | Fallback: Always check `finish_reason != 'length'` (`AMP-185`) and `refusal == null` before parsing. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-018` | [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) | OpenAI | `2026-08-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Strict JSON Schema enforcement (strict: true) guarantees schema compliance in GPT-4o, GPT-4.1, and o3, unlike legacy JSON mode or free-text prompting. | Prevents syntax errors in MarTech webhooks, though semantic accuracy still requires validation. |
| `SRC-024` | [Structured outputs - Interactions API - Google AI for Developers](https://ai.google.dev/gemini-api/docs/structured-output) | Google AI for Developers | `2026-10-21` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Gemini API supports strict JSON Schema outputs for predictable downstream CRM, catalog, and ad-feed automation. | Requires explicit schema definition in API calls. |
| `SRC-018` | [Structured model outputs | OpenAI API](https://developers.openai.com/api/docs/guides/structured-outputs) | OpenAI | `2026-08-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Confirmed via OpenAI and Google Gemini API documentation: constrained decoding guarantees the output matches the supplied JSON Schema keys, types, and enums. | Fallback: Always check `finish_reason != 'length'` (`AMP-185`) and `refusal == null` before parsing. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never rely on regex stripping (`text.replace('```json', '')`) on free-text LLM completions for production webhooks—use native API-level Structured Outputs! / لا تعتمد على المخرجات النصية الحرة مع محاولة تنظيفها بـ Regex في بيئات الإنتاج؛ فعّل دائماً `json_schema` الصارم من داخل إعدادات الـ API.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
