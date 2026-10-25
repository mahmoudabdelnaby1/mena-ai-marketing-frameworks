# `FW-028` — Social-to-WhatsApp Click-to-Chat Attribution & Pre-Qualification Triage Workflow
## مسار عمل تتبع إحالات روابط «انقر للدردشة في واتساب» (`Click-to-WhatsApp`) وفرز العملاء قبل التحويل للمبيعات

- **One-Sentence Promise (EN)**: Capture campaign attribution (`UTM` / `fbclid` / `gclid`) and pre-qualify buyers before routing social Click-to-WhatsApp traffic to human sales reps so chats do not appear as `Direct` in GA4 or overwhelm agents with unqualified `'بكام؟'` messages.
- **الوعد التطبيقي في جملة واحدة (AR)**: الاحتفاظ ببيانات الإحالة الإعلانية (`UTM / fbclid / gclid`) وتأهيل العميل آلياً قبل تحويله لمندوب المبيعات في واتساب لمنع ضياع المصدر تحت قناة `Direct` في GA4 أو إغراق الموظفين باستفسارات غير مؤهلة.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Direct `wa.me/` links in social bios and ads strip HTTP referrers and flood human agents with unsegmented inquiries; an OPERATING_FRAMEWORK combining reference-code pre-filled messages, AI 3-question triage, and CAPI/GA4 server logging restores full-funnel attribution.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-136`, `AMP-146`, `AMP-156`, `AMP-166`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: `AMP-516`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use whenever driving social media (Instagram, TikTok, Snapchat, Facebook) or paid search traffic into WhatsApp Business in Egypt, KSA, or UAE.
- **داعي الاستخدام (AR)**: يُستخدم عند توجيه زيارات الإعلانات أو الحسابات الاجتماعية (إنستغرام، تيك توك، سناب شات، فيسبوك) إلى محادثات واتساب للأعمال في مصر أو السعودية أو الإمارات.
- **Do NOT Use When**: Do not count a raw 'WhatsApp Link Click' on a landing page as a completed `Purchase` or `Qualified Lead` conversion in Meta/Google Ads (`AMP-069` / `AMP-394`).

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - WhatsApp Business API (`Cloud API` / Wati / Respond.io / ManyChat / SleekFlow) webhook access
   - Campaign UTM & Reference Code naming convention (`[Ref: IG-RAM-04]`)
   - 3-Question Qualification Script (Product/Service interest, City/Delivery Zone, Budget/Payment Preference)
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
