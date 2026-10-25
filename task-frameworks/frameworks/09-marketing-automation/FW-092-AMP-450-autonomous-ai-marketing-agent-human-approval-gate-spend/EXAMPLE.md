# End-to-End Worked Example & Failure Recovery — `FW-092` (`AMP-450`)

- **Framework**: Autonomous AI Marketing Agent Human-Approval Gate & Spend-Circuit-Breaker Governance Framework
- **العنوان بالعربية**: الإطار التشغيلي لبوابات الاعتماد البشري (`Human-in-the-Loop`) وقواطع الأمان المالية لوكلاء التسويق المستقلين (`Autonomous AI Agents`)
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Scenario**: A Dubai & Riyadh Performance Agency connected an autonomous LLM Media-Buyer Agent to Meta and Google Ads APIs with instructions to `'check ROAS every 3 hours and scale winning ad sets'`.
- **Disaster Prevented**: On Friday at `12:30 PM` (during Friday Jumu'ah prayer when KSA checkout volume naturally pauses for 90 minutes, and before COD confirmations `AMP-062` settled), the agent saw a temporary 2-hour ROAS dip on Campaign A and a 2-hour spike on Campaign B; it tried to cut Campaign A's budget by `70%` and increase Campaign B's budget by `300%` (`from $500/day to $2,000/day`), which would have reset Meta's learning phase on both campaigns!

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **`validate_agent_mutation_request()` Firewall Intercept**:
  - Action 1 (`Cut Campaign A by -70%`): **`BLOCKED_BUDGET_SPIKE (-70.0% exceeds 20% ceiling) + BLOCKED_INTRADAY_WINDOW`**.
  - Action 2 (`Raise Campaign B by +300%`): **`BLOCKED_BUDGET_SPIKE (+300.0% exceeds 20% ceiling)`**.
  - Instead of mutating live budgets, the agent posted a staged recommendation card to the Media Buyer's Slack channel with 7-day rolling Net Delivered ROAS context.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Locked Agent Evaluation Window to Minimum 7-Day Rolling Window (`AMP-391`)**: Forbade the agent from evaluating performance on `<7-day` or intraday windows in MENA (due to COD settlement lag `AMP-062` and Friday prayer / weekend curves).
2. **Enforced `status: "PAUSED"` on All Agent-Created Ads**: Every new ad variation created by the creative agent lands in Ads Manager as `PAUSED` until the human buyer checks Advantage+ Creative toggles (`AMP-065`), SFDA/Discount compliance (`AMP-064`, `AMP-176`), and clicks `Approve`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `validate_agent_mutation_request()` proxy firewall deployed across all agency ad accounts; zero runaway spend incidents, zero learning-phase resets, and 100% human sign-off on live creatives and `>20%` budget shifts.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An autonomous SEO/blog agent is given direct WordPress `Administrator` credentials and publishes 40 unreviewed articles overnight containing a hallucinated GASTAT statistic (`AMP-179`) and a therapeutic skincare claim (`AMP-176`).
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Issue CMS API keys to AI agents strictly under the **`Contributor` role (`can create Drafts only, cannot Publish`)**—never `Administrator` or `Editor`!
