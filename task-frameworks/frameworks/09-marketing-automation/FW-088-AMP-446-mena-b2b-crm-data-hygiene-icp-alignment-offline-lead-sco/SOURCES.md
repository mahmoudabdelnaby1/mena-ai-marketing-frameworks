# Evidence Register & Source Boundaries — `FW-088` (`AMP-446`)

- **Framework Title (EN)**: MENA B2B CRM Data Hygiene, ICP Alignment & Offline Lead-Scoring Feedback Framework
- **عنوان الأصل (AR)**: الإطار التشغيلي لتنظيف بيانات `CRM` ومواءمة معايير العميل المثالي (`ICP`) بين التسويق والمبيعات في قطاع الأعمال (`B2B`)
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-047` | [Google Ads Channel Priority, Lead Scoring and a February 2027 Display Change: A Checklist for Arab Advertisers](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) | VOCTOS | `2026-10-16` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents Google Ads Oct 2026 channel priority changes, offline lead-scoring requirements, and the Feb 2027 removal of current Display spend allocation controls on Search campaigns. | Google Ads campaign management in Arab markets. |
| `SRC-054` | [Lead Generation Benchmarks in Egypt](https://23hublab.com/lead-generation-benchmarks-in-egypt/) | 23HubLab | `2026-05-12` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | LinkedIn B2B leads in Egypt convert to meetings at 25-40% vs 8-18% for Meta lead forms; structured lead nurturing lifts 12-month conversion by 20-40%. | Egyptian B2B and high-ticket B2C lead generation. |
| `SRC-086` | [Common Mistakes When Using AI in B2B Sales and Marketing](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) | Founderz | `2026-08-15` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Automating B2B outreach and lead generation on top of uncleaned CRM data or without sales-marketing ICP alignment amplifies errors and lengthens the sales cycle. | B2B AI marketing and CRM automation. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-047` | [Google Ads Channel Priority, Lead Scoring and a February 2027 Display Change: A Checklist for Arab Advertisers](https://voctos.net/google-ads-channel-priority-lead-scoring-arab-advertisers/) | VOCTOS | `2026-10-16` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Passing CRM-qualified lead stages (`MQL/SQL`) back to Google Ads and Meta prevents automated bidding from optimizing toward cheap unqualified form-fills. | Fallback: If real-time CRM API sync is unavailable, upload a weekly CSV of `GCLID` + SHA-256 hashed `email`/`phone` for qualified SQLs. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never automate outbound B2B emails/WhatsApp messages from CRM triggers until duplicate company records, Arabic-Indic phone numbers (`AMP-388`), and non-ICP disqualifiers (`Job Seeker / Student / Vendor`) are scrubbed. / لا تقم بتفعيل الإرسال الآلي من الـ CRM قبل دمج السجلات المكررة، وتطبيع أرقام الهواتف، وعزل طلبات التوظيف والطلاب والموردين.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
