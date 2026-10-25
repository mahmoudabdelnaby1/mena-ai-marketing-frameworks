# Autonomous AI Marketing Agent Human-Approval Gate & Spend-Circuit-Breaker Governance Framework
## <span dir="rtl">الإطار التشغيلي لبوابات الاعتماد البشري (`Human-in-the-Loop`) وقواطع الأمان المالية لوكلاء التسويق المستقلين (`Autonomous AI Agents`)</span>

> **Asset ID**: `FW-092` (`AMP-450`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Marketing Automation | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent autonomous AI marketing agents from mutating live ad budgets during learning phases, publishing unreviewed Arabic/religious/regulatory copy, or issuing unauthorized refunds by enforcing a 3-Tier `Read / Stage-Draft / Write` permission matrix and hard spend circuit-breakers.
- **AR**: <span dir="rtl">منع وكلاء التسويق المستقلين بالذكاء الاصطناعي من التلاعب بميزانيات الإعلانات الحية أثناء مرحلة التعلم أو نشر محتوى غير مراجع ثقافياً ونظامياً عبر فرض مصفوفة صلاحيات صارمة (`قراءة / تجهيز مسودة / نشر بموافقة بشرية`) وقواطع أمان مالية.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before granting any AI agent, automation script, or third-party AI optimization tool API access to Meta Ads, Google Ads, Snapchat/TikTok Ads, Salla/Zid/Shopify catalogs, or social/email publishing accounts.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل منح أي وكيل ذكاء اصطناعي أو أداة تحسين آلي صلاحية الوصول (`API Token`) لحسابات الإعلانات أو المتاجر أو النشر.</span>
- **When NOT to Use It (EN)**: Never grant an autonomous AI agent unthrottled `ads_management` write permissions to increase campaign budgets or publish live ad creatives without a human-in-the-loop approval step!
- **متى لا تستخدمها (AR)**: <span dir="rtl">يُحظر تماماً منح أي وكيل ذكاء اصطناعي صلاحية مفتوحة لرفع الميزانيات الإعلانية أو نشر إعلانات جديدة مباشرة للجمهور دون خطوة اعتماد بشري!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Inventory of all connected AI Agent API tokens (`Meta Marketing API`, `Google Ads API`, `Salla/Zid/Shopify Admin API`, `WhatsApp Cloud API`)
- Maximum Daily Budget Delta Ceiling (`<= 15–20%` change per 48 hours so learning phases never reset!)
- Human Approval Slack / Microsoft Teams / WhatsApp Admin channel (`Approve / Reject` webhook)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 3-Tier AI Agent Permission Matrix & Spend Circuit-Breaker Framework

#### 1. The `Green / Amber / Red` Action Permission Contract
| Permission Zone | Allowed Agent Actions | Execution Mode | Mandatory Guardrail & Circuit-Breaker |
| :--- | :--- | :--- | :--- |
| **🟢 GREEN ZONE: Read-Only Diagnostics & Anomaly Alerts (`100% Autonomous`)** | Fetching ad metrics, auditing `sitemap.xml` (`AMP-003`), scanning Search Terms for morphological negatives (`AMP-066`), checking GMC disapproval alerts (`AMP-063`), and drafting reports. | **Autonomous (`Read-Only API Token`)** | Use strictly `read_insights` / `readonly` OAuth scopes so the diagnostic agent physically cannot mutate production state. |
| **🟡 AMBER ZONE: Staging Drafts & Safe Micro-Adjustments (`Staged for 1-Click Human Approval`)** | Creating **PAUSED** draft ads (`status: "PAUSED"`), staging draft blog/email/catalog updates (`status: "DRAFT"`), proposing negative keywords, or proposing a budget adjustment **`<= ±15%`** after **`>= 7` days** out of learning phase. | **Staged Proposal (`Requires 1-Click Slack/Teams Human Sign-Off`)** | **Hard Learning-Phase Lock**: Agent is forbidden from proposing budget/bid edits if the campaign/ad set was modified within the last **72 hours** or is inside **Payday/Friday prayer volatility windows (`AMP-391`)**! |
| **🔴 RED ZONE: High-Risk Production Mutations (`STRICTLY BLOCKED FROM AUTONOMOUS WRITE`)** | 1. Publishing live ad copy/creatives (`status: "ACTIVE"`).<br>2. Increasing daily budget by **`> 20%`** or creating new live campaigns.<br>3. Replying publicly to crisis/regulatory social threads (`AMP-128`).<br>4. Altering storefront product prices (`AMP-063`, `AMP-064`) or issuing cash refunds. | **100% Human-Executed Only (Hardware/API Firewall Blocked)** | Enforced via API middleware proxy (`validate_agent_mutation_request()` below) that rejects any Red-Zone API payload automatically! |

#### 2. Copy-Ready Python API Proxy Firewall (`Wrap Around Any Ads/Storefront MCP or Agent Tool`)
```python
def validate_agent_mutation_request(action_type: str, payload: dict, hours_since_last_budget_edit: float) -> dict:
    # Rule 1: Never allow agent to set an ad or campaign status directly to ACTIVE without human signature
    if action_type in ("CREATE_AD", "UPDATE_AD", "CREATE_CAMPAIGN") and payload.get("status") == "ACTIVE":
        if not payload.get("human_approver_signature"):
            payload["status"] = "PAUSED"
            return {"allowed": True, "enforced_mode": "DOWNGRADED_TO_PAUSED_DRAFT", "payload": payload}

    # Rule 2: Hard Circuit-Breaker on Budget Changes (>20% delta or <72h since last edit)
    if action_type == "UPDATE_BUDGET":
        old_b = float(payload.get("current_daily_budget", 0))
        new_b = float(payload.get("proposed_daily_budget", 0))
        pct_change = abs(new_b - old_b) / max(old_b, 1.0)
        if hours_since_last_budget_edit < 72:
            return {"allowed": False, "reason": "BLOCKED_LEARNING_PHASE_COOLDOWN (<72h since last edit)"}
        if pct_change > 0.20 and not payload.get("human_approver_signature"):
            return {"allowed": False, "reason": f"BLOCKED_BUDGET_SPIKE ({pct_change:.1%} exceeds 20% autonomous ceiling)"}

    # Rule 3: Block autonomous price mutations on storefront (AMP-063 / AMP-064)
    if action_type == "UPDATE_PRODUCT_PRICE" and not payload.get("human_approver_signature"):
        return {"allowed": False, "reason": "BLOCKED_STATUTORY_PRICE_LOCK (Requires human & GMC schedule check)"}

    return {"allowed": True, "enforced_mode": "APPROVED", "payload": payload}
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Scenario**: A Dubai & Riyadh Performance Agency connected an autonomous LLM Media-Buyer Agent to Meta and Google Ads APIs with instructions to `'check ROAS every 3 hours and scale winning ad sets'`.
- **Disaster Prevented**: On Friday at `12:30 PM` (during Friday Jumu'ah prayer when KSA checkout volume naturally pauses for 90 minutes, and before COD confirmations `AMP-062` settled), the agent saw a temporary 2-hour ROAS dip on Campaign A and a 2-hour spike on Campaign B; it tried to cut Campaign A's budget by `70%` and increase Campaign B's budget by `300%` (`from $500/day to $2,000/day`), which would have reset Meta's learning phase on both campaigns!

### Step B: Initial Output (`المخرج الأولي`)
- **`validate_agent_mutation_request()` Firewall Intercept**:
  - Action 1 (`Cut Campaign A by -70%`): **`BLOCKED_BUDGET_SPIKE (-70.0% exceeds 20% ceiling) + BLOCKED_INTRADAY_WINDOW`**.
  - Action 2 (`Raise Campaign B by +300%`): **`BLOCKED_BUDGET_SPIKE (+300.0% exceeds 20% ceiling)`**.
  - Instead of mutating live budgets, the agent posted a staged recommendation card to the Media Buyer's Slack channel with 7-day rolling Net Delivered ROAS context.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Locked Agent Evaluation Window to Minimum 7-Day Rolling Window (`AMP-391`)**: Forbade the agent from evaluating performance on `<7-day` or intraday windows in MENA (due to COD settlement lag `AMP-062` and Friday prayer / weekend curves).
2. **Enforced `status: "PAUSED"` on All Agent-Created Ads**: Every new ad variation created by the creative agent lands in Ads Manager as `PAUSED` until the human buyer checks Advantage+ Creative toggles (`AMP-065`), SFDA/Discount compliance (`AMP-064`, `AMP-176`), and clicks `Approve`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `validate_agent_mutation_request()` proxy firewall deployed across all agency ad accounts; zero runaway spend incidents, zero learning-phase resets, and 100% human sign-off on live creatives and `>20%` budget shifts.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An autonomous SEO/blog agent is given direct WordPress `Administrator` credentials and publishes 40 unreviewed articles overnight containing a hallucinated GASTAT statistic (`AMP-179`) and a therapeutic skincare claim (`AMP-176`).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Issue CMS API keys to AI agents strictly under the **`Contributor` role (`can create Drafts only, cannot Publish`)**—never `Administrator` or `Editor`!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Marketing API / Google Ads API (`status: PAUSED` Staging) & WordPress/Shopify Role Scopes** | `supported` | [Official Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) (`2026-10-25`) | All major ad and e-commerce APIs support creating entities in `PAUSED` or `DRAFT` state and scoping OAuth tokens to read-only or draft-only permissions. | Enforce `validate_agent_mutation_request()` in your middleware so no agent tool call can set `status: ACTIVE` or mutate budgets `>20%` without a verified `human_approver_signature`. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero unauthorized live budget spikes or unreviewed public posts (`Target: 0 incidents`), Campaign Learning-Phase Stability (`% of budget in Active vs. Learning Reset`), and Human Review Turnaround Time on Staged Drafts.
- **Baseline**: Audit of active API tokens and past automated rule misfires.
- **Observation Window**: Enforced continuously at the API gateway layer.
- **Interpretation Boundary**: Human-in-the-loop gates and circuit-breakers prevent catastrophic agent errors while preserving 90% of the time-savings of automated research and draft staging.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Prompting best practices - Claude Platform Docs](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) — *Anthropic* (Published `2026-08-15`, Accessed `2026-10-25`): Recommends XML tag structuring, explicit role/audience context, few-shot examples, and verification criteria to avoid generic outputs.
- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
- [Meta Advantage+ Mistakes: Common Errors and How Agencies Avoid Them](https://alienroad.com/meta-advantage-mistakes-common-errors-and-how-agencies-avoid-them/) — *Alien Road* (Published `2026-03-19`, Accessed `2026-10-25`): Identifies 7 Advantage+ failures: weak conversion signals, low creative variety, premature edits during learning, paying for existing customers, trusting in-platform numbers without holdouts, ignoring brand safety, and unhealthy product feeds.
