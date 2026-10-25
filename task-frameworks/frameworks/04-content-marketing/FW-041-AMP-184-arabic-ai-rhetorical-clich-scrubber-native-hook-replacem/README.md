# `FW-041` — Arabic AI Rhetorical Cliché Scrubber & Native Hook Replacement Checklist
## قائمة فحص وتطهير المحتوى العربي من الكليشيهات المترجمة للذكاء الاصطناعي (`في عالم يتسارع فيه...` / `هل تبحث عن...`)

- **One-Sentence Promise (EN)**: Detect and strip 30+ dead AI Arabic rhetorical clichés (`'في عالمنا الرقمي المتسارع'`, `'لا شك أن'`, `'تُعدّ بمثابة'`) and replace them with direct, high-retention native Arabic openings.
- **الوعد التطبيقي في جملة واحدة (AR)**: رصد وحذف أكثر من 30 عبارة نمطية مكررة تفضح الكتابة الآلية («في عالم يتسارع فيه...»، «هل تبحث عن...»، «تُعدّ بمثابة...») واستبدالها بمقدمات عربية مباشرة ترفع معدل إكمال القراءة.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: LLMs trained on translated English SEO corpora open 80%+ of Arabic articles and posts with the exact same calqued templates (`'في عالم يتسارع فيه...'` = `'In today's fast-paced world...'`), causing Arab readers to bounce in the first 3 seconds; a deterministic regex CHECKLIST and replacement matrix eliminates AI-smell.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-194`, `AMP-204`, `AMP-214`, `AMP-224`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Content Manager, Arabic Copywriter, Editorial Lead, Compliance Reviewer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use as a mandatory post-generation editing pass on every Arabic blog article, social post, newsletter, press release, or landing page.
- **داعي الاستخدام (AR)**: تُستخدم كخطوة تحريرية إلزامية بعد توليد أي مقال أو منشور أو رسالة بريدية أو صفحة هبوط باللغة العربية.
- **Do NOT Use When**: Do not allow any article or social caption to publish if its first 2 sentences contain a throat-clearing cliché instead of the core answer or problem.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Draft Arabic Article, Social Post, or Script
   - 1 Concrete Data Point, Counter-Intuitive Fact, or Real Customer Friction Point to use as the replacement opening
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
