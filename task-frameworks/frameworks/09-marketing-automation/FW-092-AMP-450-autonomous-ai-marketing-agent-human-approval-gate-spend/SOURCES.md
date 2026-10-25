# Evidence Register & Source Boundaries — `FW-092` (`AMP-450`)

- **Framework Title (EN)**: Autonomous AI Marketing Agent Human-Approval Gate & Spend-Circuit-Breaker Governance Framework
- **عنوان الأصل (AR)**: الإطار التشغيلي لبوابات الاعتماد البشري (`Human-in-the-Loop`) وقواطع الأمان المالية لوكلاء التسويق المستقلين (`Autonomous AI Agents`)
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-056` | [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) | Grower AI | `2026-10-12` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Secondary regional reach material; its localization discussion is not treated as a universal quota or wage rule. | Check current activity- and workforce-specific requirements with the official HRSD calculator. |
| `SRC-069` | [Meta Advantage+ Mistakes: Common Errors and How Agencies Avoid Them](https://alienroad.com/meta-advantage-mistakes-common-errors-and-how-agencies-avoid-them/) | Alien Road | `2026-03-19` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Identifies 7 Advantage+ failures: weak conversion signals, low creative variety, premature edits during learning, paying for existing customers, trusting in-platform numbers without holdouts, ignoring brand safety, and unhealthy product feeds. | Meta Advantage+ campaigns. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-021` | [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Recommends XML tag structuring, explicit role/audience context, few-shot examples, and verification criteria to avoid generic outputs. | Model-agnostic best practices validated on Claude models. |
| `SRC-021` | [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Anthropic | `2026-08-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | All major ad and e-commerce APIs support creating entities in `PAUSED` or `DRAFT` state and scoping OAuth tokens to read-only or draft-only permissions. | Fallback: Enforce `validate_agent_mutation_request()` in your middleware so no agent tool call can set `status: ACTIVE` or mutate budgets `>20%` without a verified `human_approver_signature`. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never grant an autonomous AI agent unthrottled `ads_management` write permissions to increase campaign budgets or publish live ad creatives without a human-in-the-loop approval step! / يُحظر تماماً منح أي وكيل ذكاء اصطناعي صلاحية مفتوحة لرفع الميزانيات الإعلانية أو نشر إعلانات جديدة مباشرة للجمهور دون خطوة اعتماد بشري!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
