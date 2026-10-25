# Evidence Register & Source Boundaries — `FW-025` (`AMP-123`)

- **Framework Title (EN)**: Arabic Customer-Service Chatbot Dialect Guardrail & 'False-Friends' Lexicon Checklist
- **عنوان الأصل (AR)**: قائمة فحص وضبط لهجات بوتات خدمة العملاء بالعربية (منع «الأصدقاء الكاذبين» بين اللهجات والردود الفظة)
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
| `SRC-074` | [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) | AISyncSo | `2026-09-24` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Modern frontier LLMs accurately parse Gulf and Egyptian idioms when explicitly instructed via system prompt guardrails, whereas legacy keyword/MSA-only classifiers fail on negation-based praise ('ما قصرت') and sarcasm. | Fallback: Route any message with sentiment confidence `< 0.80` or mixed positive/delay tokens directly to a human queue. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Social Media Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not let an AI chatbot handle angry refund disputes, medical adverse events, or legal threats without immediate human agent handoff (`AMP-128`). / لا تسمح للبوت بالتعامل الذاتي مع النزاعات المالية الحادة أو الشكاوى الطبية أو التهديدات القانونية دون تحويل فوري لموظف بشري (`AMP-128`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Social Media Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
