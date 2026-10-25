# Evidence Register & Source Boundaries — `FW-048` (`AMP-236`)

- **Framework Title (EN)**: GCC & Egypt B2B Executive Email Deliverability (SPF/DKIM/DMARC) & Bilingual Conciseness Checklist
- **عنوان الأصل (AR)**: قائمة فحص موثوقية نطاق البريد (`SPF/DKIM/DMARC`) وهيكلة رسائل الشركات (`B2B`) ثنائية اللغة في الخليج ومصر
- **Channel**: Email Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-074` | [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) | AISyncSo | `2026-09-24` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Shows why customer-facing AI agents trained on MSA fail to parse everyday Khaleeji phrasing, politeness formulas, and intent in Riyadh, Dubai, and Doha. | Enterprise AI agents in GCC. |
| `SRC-086` | [Common Mistakes When Using AI in B2B Sales and Marketing](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) | Founderz | `2026-08-15` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Automating B2B outreach and lead generation on top of uncleaned CRM data or without sales-marketing ICP alignment amplifies errors and lengthens the sales cycle. | B2B AI marketing and CRM automation. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-086` | [Common Mistakes When Using AI in B2B Sales and Marketing](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) | Founderz | `2026-08-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Enterprise mail gateways strictly enforce SPF/DKIM alignment, DMARC policies, and low link-to-text ratios on inbound B2B emails. | Fallback: Verify DNS records via `dig TXT _dmarc.yourdomain.com` before launching any B2B sequence. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Email Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not send bulk marketing sequences to unconsented scraped lists (`AMP-232`) or from your primary corporate root domain without subdomain isolation. / لا ترسل حملات تسويقية لقوائم مجمعة بدون موافقة (`AMP-232`) ولا تستخدم النطاق الرئيسي للشركة في الحملات الجماعية دون عزل النطاق الفرعي.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Email Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
