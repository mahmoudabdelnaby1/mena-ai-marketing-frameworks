# `FW-031` — Social Comment Moderation Whitelist & Dialectal Price-Inquiry Routing Checklist (`بكام` / `بكم`)
## قائمة فحص وضبط الفلترة الآلية للتعليقات لحماية استفسارات الشراء باللهجات (`بكام` / `بكم` / `تفاصيل`)

- **One-Sentence Promise (EN)**: Configure AI comment moderation and auto-DM workflows so short colloquial buyer inquiries (`'بكام؟'`, `'بكم؟'`, `'موجود؟'`, `'تفاصيل'`) are converted into sales instead of being auto-hidden as spam or low-quality comments.
- **الوعد التطبيقي في جملة واحدة (AR)**: ضبط أدوات إدارة التعليقات والرد الآلي بحيث تتحول استفسارات الشراء القصيرة باللهجات («بكام؟»، «بكم؟»، «موجود؟»، «تفاصيل») إلى مبيعات فورية بدلاً من إخفائها بالخطأ كرسائل مزعجة.
- **Selected Artifact Type**: `CHECKLIST` *(Chosen because: In Egypt and the GCC, up to 60% of high-intent social commerce comments consist of 1–2 colloquial words (`'بكام'`, `'بكم'`, `'السعر'`, `'في توصيل؟'`); generic English-trained AI moderation tools hide short repetitive comments as spam or negative sentiment—making a whitelist CHECKLIST essential.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-139`, `AMP-149`, `AMP-159`, `AMP-169`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use when configuring automated comment moderation or comment-to-DM automation tools (ManyChat, Respond.io, Meta Inbox Automations, Brandwatch, Sprinklr) on Instagram, Facebook, or TikTok.
- **داعي الاستخدام (AR)**: تُستخدم عند إعداد أدوات إخفاء التعليقات أو الرد التلقائي (ManyChat, Respond.io, Meta Suite) على إنستغرام وفيسبوك وتيك توك.
- **Do NOT Use When**: Do not reply to `'بكام؟'` with `'تم الرد على الخاص (Check DM)'` if your store sells standard fixed-price retail items—hiding prices in comments frustrates GCC/Egyptian shoppers and lowers ad conversion rate.

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - List of active social moderation tools & Meta Page/Instagram Moderation Keyword Blocklists
   - Product catalog price & payment summary for active promoted posts
   - Comment-to-DM automation rules (ManyChat / Meta Inbox)
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
