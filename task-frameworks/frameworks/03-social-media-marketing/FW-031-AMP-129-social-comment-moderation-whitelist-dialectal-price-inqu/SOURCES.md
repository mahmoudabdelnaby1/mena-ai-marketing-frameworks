# Evidence Register & Source Boundaries — `FW-031` (`AMP-129`)

- **Framework Title (EN)**: Social Comment Moderation Whitelist & Dialectal Price-Inquiry Routing Checklist (`بكام` / `بكم`)
- **عنوان الأصل (AR)**: قائمة فحص وضبط الفلترة الآلية للتعليقات لحماية استفسارات الشراء باللهجات (`بكام` / `بكم` / `تفاصيل`)
- **Channel**: Social Media Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-074` | [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) | AISyncSo | `2026-09-24` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Shows why customer-facing AI agents trained on MSA fail to parse everyday Khaleeji phrasing, politeness formulas, and intent in Riyadh, Dubai, and Doha. | Enterprise AI agents in GCC. |
| `SRC-075` | [Your Chatbot Just Offended an Arabic Customer — Here's the Data Fix](https://aitaggers.com.au/blog/chatbot-offended-arabic-customer) | AI Taggers | `2026-10-08` | `2026-10-25` | `PRACTITIONER_GUIDE` (`OBSERVED_CASE`) | Explains how dialectal false friends (words polite in one Arab country but rude or abrupt in Gulf/Egyptian dialect) cause AI chatbots to offend customers. | Conversational AI training and guardrails. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-074` | [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) | AISyncSo | `2026-09-24` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Meta's official Private Replies API allows 1 automated DM response within 7 days of a user's comment on an IG/FB post or ad when triggered by keyword rules. | Fallback: Use regex/prefix matching on normalized Arabic text (`AMP-002`) so spelling variations trigger the reply reliably. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Social Media Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not reply to `'بكام؟'` with `'تم الرد على الخاص (Check DM)'` if your store sells standard fixed-price retail items—hiding prices in comments frustrates GCC/Egyptian shoppers and lowers ad conversion rate. / لا تكتفِ بالرد العلني المستفز «تم الرد على الخاص» للمنتجات ذات السعر الثابت؛ فإخفاء السعر يثير استياء المتسوقين في مصر والخليج ويخفض معدل التحويل.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Social Media Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
