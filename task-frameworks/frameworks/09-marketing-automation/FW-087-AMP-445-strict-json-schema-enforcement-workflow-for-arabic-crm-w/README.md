# `FW-087` — Strict JSON Schema Enforcement Workflow for Arabic CRM, Webhook & Catalog Automations (`strict: true` / `responseSchema`)
## مسار عمل فرض مخرجات `JSON Schema` الصارمة (`strict: true`) في أتمتة الـ CRM والويب هوك والكتالوجات العربية

- **One-Sentence Promise (EN)**: Eliminate crashed Make/Zapier/n8n/Python webhooks caused by LLMs wrapping Arabic JSON in conversational prose (`'بالتأكيد! إليك ملف JSON:'`), changing key names into Arabic, or truncating strings (`AMP-185`).
- **الوعد التطبيقي في جملة واحدة (AR)**: القضاء نهائياً على تعطل أنابيب الأتمتة (`Make / Zapier / n8n / Webhooks`) الناتج عن إضافة النموذج اللغوي لمقدمات حوارية («بالتأكيد! إليك النتيجة:») أو ترجمة مفاتيح الـ JSON للعربية أو كسر الأقواس.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Prompt-only instructions like `'Return only valid JSON and nothing else'` fail 3–8% of the time in production when inputs contain Arabic quotes (`"` / `«»`), multi-line WhatsApp messages, or dialect slang; enforcing API-level `response_format: {type: 'json_schema', strict: true}` (OpenAI) or `responseSchema` (Google Gemini) / Tool Use (Anthropic Claude) guarantees 100% schema adherence.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-455`, `AMP-465`, `AMP-475`, `AMP-485`, `AMP-495`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever connecting an LLM API (`OpenAI`, `Gemini`, `Claude`) to a CRM (`HubSpot`, `Salesforce`, `Zoho`), e-commerce catalog (`Salla`, `Zid`, `Shopify`), or automation platform (`n8n`, `Make`, `Zapier`).
- **داعي الاستخدام (AR)**: تُستخدم عند ربط واجهات برمجة النماذج اللغوية بأنظمة إدارة العملاء (`CRM`) أو المتاجر الإلكترونية أو منصات الأتمتة (`n8n`, `Make`, `Zapier`).
- **Do NOT Use When**: Never rely on regex stripping (`text.replace('```json', '')`) on free-text LLM completions for production webhooks—use native API-level Structured Outputs!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Downstream Webhook / CRM Field Schema (exact ASCII field names and allowed `enum` values)
   - Arabic Input Payload (e.g., inbound WhatsApp message, lead form note, or raw product text)
   - Token budget calculation (`AMP-185` — ensuring `max_completion_tokens >= 1024` so Arabic strings never clip)
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
