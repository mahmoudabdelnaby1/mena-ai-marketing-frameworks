# `FW-025` — Arabic Customer-Service Chatbot Dialect Guardrail & 'False-Friends' Lexicon Checklist
## قائمة فحص وضبط لهجات بوتات خدمة العملاء بالعربية (منع «الأصدقاء الكاذبين» بين اللهجات والردود الفظة)

- **One-Sentence Promise (EN)**: Prevent AI customer-service chatbots on WhatsApp, Instagram, and web chat from offending Arab shoppers through cross-dialectal 'false friends', misread Gulf polite idioms, or robotic MSA replies.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع بوتات خدمة العملاء بالذكاء الاصطناعي على واتساب وإنستغرام والموقع من إساءة فهم تعبيرات المجاملة الخليجية والمصرية أو استخدام مفردات تحمل معاني مسيئة في لهجة أخرى.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: Enterprise Arabic NLP audits (AISync / AI Taggers 2026) document that LLMs trained on mixed Arabic corpora misinterpret Gulf politeness idioms (`'يعطيك العافية'`, `'ما قصرت'`, `'سم'`, `'أبشر'`) or emit cross-dialectal false friends that offend customers; a pre-deployment CHECKLIST and system-prompt lexicon lock prevent live PR incidents.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-133`, `AMP-143`, `AMP-153`, `AMP-163`, `AMP-173`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-513`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before deploying or updating any AI customer-support agent on WhatsApp Business, Instagram DM, Facebook Messenger, or website live chat in KSA, UAE, Kuwait, Qatar, or Egypt.
- **داعي الاستخدام (AR)**: تُستخدم قبل إطلاق أو تحديث أي بوت خدمة عملاء بالذكاء الاصطناعي على واتساب أو إنستغرام أو ماسنجر أو دردشة الموقع في الخليج ومصر.
- **Do NOT Use When**: Do not let an AI chatbot handle angry refund disputes, medical adverse events, or legal threats without immediate human agent handoff (`AMP-128`).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Target Customer Geography (`KSA/GCC` vs. `Egypt` vs. `Multi-Country`)
   - System Prompt & Knowledge Base of the WhatsApp / Social DM Agent
   - List of 50 real historical customer chat transcripts (including angry, sarcastic, and polite local phrasing)
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `CHECKLIST` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `CHECKLIST` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
