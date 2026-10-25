# Evidence Register & Source Boundaries — `FW-038` (`AMP-181`)

- **Framework Title (EN)**: XML-Indexed Brand Voice & Context-Window Hygiene Workflow for Long Arabic Drafts
- **عنوان الأصل (AR)**: مسار عمل فهرسة أدلة الهوية اللغوية بهيكلة `XML` لمنع انحراف التعليمات (`Instruction Drift`) في النصوص العربية الطويلة
- **Channel**: Content Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-021` | [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Recommends XML tag structuring, explicit role/audience context, few-shot examples, and verification criteria to avoid generic outputs. | Model-agnostic best practices validated on Claude models. |
| `SRC-023` | [Context windows - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Larger context windows do not guarantee uniform recall; dumping unindexed guidelines and noisy history degrades instruction adherence. | Supports modular context curation over monolithic prompt stuffing. |
| `SRC-023` | [Context windows - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Anthropic documentation notes that as context length grows with unindexed or conflicting material, instruction adherence can degrade; XML tags (`<brand_constitution>`) and clean few-shot examples preserve precision. | Fallback: Keep the active style prompt under 1,000 tokens and generate long Arabic documents in modular sections. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-021` | [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Recommends XML tag structuring, explicit role/audience context, few-shot examples, and verification criteria to avoid generic outputs. | Model-agnostic best practices validated on Claude models. |
| `SRC-023` | [Context windows - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Larger context windows do not guarantee uniform recall; dumping unindexed guidelines and noisy history degrades instruction adherence. | Supports modular context curation over monolithic prompt stuffing. |
| `SRC-023` | [Context windows - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/context-windows) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Anthropic documentation notes that as context length grows with unindexed or conflicting material, instruction adherence can degrade; XML tags (`<brand_constitution>`) and clean few-shot examples preserve precision. | Fallback: Keep the active style prompt under 1,000 tokens and generate long Arabic documents in modular sections. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Content Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not paste contradictory historical examples (e.g., old MSA press releases + old Egyptian Ammiya posts) into the same prompt when asking for a new Saudi Khaleeji campaign. / لا تقم بلصق أمثلة سابقة متناقضة اللهجة (مثل بيانات صحفية بالفصحى مع منشورات مصرية قديمة) داخل نفس البرومبت عند طلب حملة جديدة باللهجة الخليجية.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Content Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
