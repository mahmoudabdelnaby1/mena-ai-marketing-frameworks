# `FW-034` — Arabic Dialect Isolation & Anti-Hybrid-Collision Prompt Template (Egyptian Ammiya vs. Saudi/Gulf Khaleeji vs. White MSA)
## قالب عزل اللهجات العربية ومنع الخلط اللهجي الهجين (العامية المصرية مقابل الخليجية السعودية مقابل الفصحى البيضاء)

- **One-Sentence Promise (EN)**: Lock LLM copy generation to one pure Arabic dialect register—preventing jarring mid-sentence collisions of Egyptian (`كده/عايز`), Levantine (`هلق/كتير`), and Saudi Khaleeji (`الحين/ودك`) in the same script.
- **الوعد التطبيقي في جملة واحدة (AR)**: تقييد النموذج اللغوي بسجل لهجي واحد نقي ومنع الخلط الهجين المحرج بين العامية المصرية (`كده/عايز`) والشامية (`هلق/كتير`) والخليجية (`الحين/ودك`) داخل النص الواحد.
- **Selected Artifact Type**: `PROMPT_TEMPLATE` *(Chosen because: Peer-reviewed Arabic LLM research (F1000Research 2025/2026) and localization audits confirm that when prompted simply for 'colloquial Arabic' (`بالعامية`), models blend Egyptian, Levantine, and Gulf tokens within the same paragraph; a PROMPT_TEMPLATE with a Negative Dialect Exclusion Table eliminates hybrid collisions.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-187`, `AMP-197`, `AMP-207`, `AMP-217`, `AMP-227`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-517`
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever writing social captions, video scripts, ad copy, WhatsApp templates, or landing page hooks in spoken regional Arabic.
- **داعي الاستخدام (AR)**: تُستخدم عند كتابة نصوص الإعلانات أو سكريبتات الفيديو أو منشورات التواصل الاجتماعي أو رسائل واتساب باللهجة المحلية.
- **Do NOT Use When**: Do not use heavy street slang for formal enterprise B2B contracts, legal terms, or medical leaflets—use Modern White Arabic (`الفصحى البيضاء المعاصرة`) for those.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Target Market Track (`Track A: Saudi White Khaleeji`, `Track B: Emirati Gulf`, `Track C: Egyptian Cairene Ammiya`, or `Track D: Modern White MSA`)
   - Target Grammatical Gender (`Masculine Singular`, `Feminine Singular`, or `Plural/Neutral` — `AMP-182`)
   - Core Offer & Brand Persona
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
