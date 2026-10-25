# `FW-039` — Arabic Grammatical Gender-Targeting & Dual/Plural Morphology Prompt Template
## قالب ضبط المخاطب النحوي والتأنيث والتذكير في النصوص التسويقية العربية (تجاوز حيادية الضمير الإنجليزي `You`)

- **One-Sentence Promise (EN)**: Prevent English-sourced prompts from defaulting to masculine-only Arabic verbs (`اشترِ الآن / استمتع`) when addressing female shoppers (`اشترِي الآن / استمتعي / لكِ`) in beauty, modest fashion, jewelry, and maternal categories.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع البرومبتات المترجمة من الإنجليزية (`You`) من مخاطبة الجمهور النسائي بصيغة المذكر المفرد (`اشترِ / استمتع / لكَ`) وضبط تصريف الأفعال والضمائر والصفات للمؤنث (`اشترِي / استمتعي / لكِ`) أو الصيغة المحايدة.
- **Selected Artifact Type**: `PROMPT_TEMPLATE` *(Chosen because: Because English `'you'` is gender-neutral, LLMs translating or generating from English briefs default to the Arabic 2nd-person masculine singular (`أنتَ / اكتشف / احصل`), alienating female buyers in cosmetics, abayas, bridal, and mom-and-baby verticals; a grammatical-gender PROMPT_TEMPLATE locks verb and pronoun inflection.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-192`, `AMP-202`, `AMP-212`, `AMP-222`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever generating Arabic ad copy, push notifications, app UI, email lifecycle flows, or product descriptions where audience gender is predominantly female, predominantly male, or mixed.
- **داعي الاستخدام (AR)**: تُستخدم عند كتابة الإعلانات أو إشعارات التطبيقات أو رسائل البريد أو أوصاف المنتجات الموجهة لجمهور نسائي أو رجالي أو مختلط.
- **Do NOT Use When**: Do not use awkward slash notation (`عزيزي/عزيزتي المشترك/ـة`) in social media ads or push notifications—choose either the specific audience gender inflection or clean gender-inclusive noun phrasing (`نرحب بكم` / `خطوة واحدة تفصلك عن...`).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Audience Gender Profile (`100% Female`, `100% Male`, `Segmented by CRM Gender Field`, or `Mixed/Unknown`)
   - Dialect Track (`Saudi Khaleeji`, `Emirati`, `Egyptian Ammiya`, or `White MSA`)
   - Draft English or Uninflected Copy
2. **Copy or Run the Artifact (`انسخ القالب أو طبّق قائمة الفحص`)**:
   - Open [`ASSET.md`](./ASSET.md) and copy the ready-to-use `PROMPT_TEMPLATE` block (or run the included validation snippet).
3. **Compare Against the Worked Example & Verify (`قارن بالمثال العملي وتجنب الأخطاء`)**:
   - Review [`EXAMPLE.md`](./EXAMPLE.md) to see the realistic input brief → raw output → human review edits → final usable result, plus the common failure mode and recovery step.
   - Check [`SOURCES.md`](./SOURCES.md) for primary official documentation, access dates (`2026-10-25`), and regulatory/technical boundaries.

## Files in This Folder

- [`README.md`](./README.md): Plain-language overview, selected artifact type, use trigger, and 3-step quick start.
- [`ASSET.md`](./ASSET.md): The complete, copy-ready `PROMPT_TEMPLATE` (bilingual Arabic + English), model capability branches, regional adaptation matrix, and measurement plan.
- [`EXAMPLE.md`](./EXAMPLE.md): End-to-end worked example with human review pass and failure/recovery scenario.
- [`SOURCES.md`](./SOURCES.md): Direct primary references (`2026-10-25`), separating problem evidence from official capability/regulatory evidence.
- [`PUBLIC-PAGE-CONTENT.md`](./PUBLIC-PAGE-CONTENT.md): Complete user-facing web publication page containing both the full working artifact and the complete worked example.
