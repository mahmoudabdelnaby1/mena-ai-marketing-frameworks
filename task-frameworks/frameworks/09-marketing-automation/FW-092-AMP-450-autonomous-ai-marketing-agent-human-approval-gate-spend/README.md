# `FW-092` — Autonomous AI Marketing Agent Human-Approval Gate & Spend-Circuit-Breaker Governance Framework
## الإطار التشغيلي لبوابات الاعتماد البشري (`Human-in-the-Loop`) وقواطع الأمان المالية لوكلاء التسويق المستقلين (`Autonomous AI Agents`)

- **One-Sentence Promise (EN)**: Prevent autonomous AI marketing agents from mutating live ad budgets during learning phases, publishing unreviewed Arabic/religious/regulatory copy, or issuing unauthorized refunds by enforcing a 3-Tier `Read / Stage-Draft / Write` permission matrix and hard spend circuit-breakers.
- **الوعد التطبيقي في جملة واحدة (AR)**: منع وكلاء التسويق المستقلين بالذكاء الاصطناعي من التلاعب بميزانيات الإعلانات الحية أثناء مرحلة التعلم أو نشر محتوى غير مراجع ثقافياً ونظامياً عبر فرض مصفوفة صلاحيات صارمة (`قراءة / تجهيز مسودة / نشر بموافقة بشرية`) وقواطع أمان مالية.
- **Selected Artifact Type**: `OPERATING_FRAMEWORK` *(Chosen because: Agencies and growth teams connecting autonomous AI agents (`MCP servers`, `AutoGPT/LangGraph agents`, `Meta/Google Ads API scripts`) directly to live production ad accounts and social publishing endpoints risk catastrophic overnight budget spikes (e.g., an agent misreading a delayed COD conversion drop at 11 PM and hiking bids by 400%, or auto-publishing an unreviewed post during a national/religious occasion); a governance OPERATING_FRAMEWORK locks write-access behind cryptographic/human approval gates.)*
- **Consolidated Child Pattern IDs (`MERGE_INTO_EXISTING`)**: `AMP-460`, `AMP-470`, `AMP-480`, `AMP-490`, `AMP-500`
- **Screened Duplicate IDs (`REJECT_DUPLICATE`)**: None
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Markets & Languages**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | Arabic (`Egyptian Ammiya, Saudi/Gulf Khaleeji, White MSA`) & English

## When to Use This Asset (`متى تستخدم هذه الأداة؟`)

- **Trigger (EN)**: Use before granting any AI agent, automation script, or third-party AI optimization tool API access to Meta Ads, Google Ads, Snapchat/TikTok Ads, Salla/Zid/Shopify catalogs, or social/email publishing accounts.
- **داعي الاستخدام (AR)**: تُستخدم قبل منح أي وكيل ذكاء اصطناعي أو أداة تحسين آلي صلاحية الوصول (`API Token`) لحسابات الإعلانات أو المتاجر أو النشر.
- **Do NOT Use When**: Never grant an autonomous AI agent unthrottled `ads_management` write permissions to increase campaign budgets or publish live ad creatives without a human-in-the-loop approval step!

## Quick Start (3 Steps for a Non-Expert Marketer)

1. **Prepare Your Inputs (`جهّز المدخلات`)**:
   - Inventory of all connected AI Agent API tokens (`Meta Marketing API`, `Google Ads API`, `Salla/Zid/Shopify Admin API`, `WhatsApp Cloud API`)
   - Maximum Daily Budget Delta Ceiling (`<= 15–20%` change per 48 hours so learning phases never reset!)
   - Human Approval Slack / Microsoft Teams / WhatsApp Admin channel (`Approve / Reject` webhook)
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
