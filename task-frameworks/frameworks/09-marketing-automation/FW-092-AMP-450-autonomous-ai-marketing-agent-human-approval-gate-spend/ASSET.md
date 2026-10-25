# FW-092: Autonomous AI Marketing Agent Human-Approval Gate & Spend-Circuit-Breaker Governance Framework
## الإطار التشغيلي لبوابات الاعتماد البشري (`Human-in-the-Loop`) وقواطع الأمان المالية لوكلاء التسويق المستقلين (`Autonomous AI Agents`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-460`, `AMP-470`, `AMP-480`, `AMP-490`, `AMP-500`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent autonomous AI marketing agents from mutating live ad budgets during learning phases, publishing unreviewed Arabic/religious/regulatory copy, or issuing unauthorized refunds by enforcing a 3-Tier `Read / Stage-Draft / Write` permission matrix and hard spend circuit-breakers.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع وكلاء التسويق المستقلين بالذكاء الاصطناعي من التلاعب بميزانيات الإعلانات الحية أثناء مرحلة التعلم أو نشر محتوى غير مراجع ثقافياً ونظامياً عبر فرض مصفوفة صلاحيات صارمة (`قراءة / تجهيز مسودة / نشر بموافقة بشرية`) وقواطع أمان مالية.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Agencies and growth teams connecting autonomous AI agents (`MCP servers`, `AutoGPT/LangGraph agents`, `Meta/Google Ads API scripts`) directly to live production ad accounts and social publishing endpoints risk catastrophic overnight budget spikes (e.g., an agent misreading a delayed COD conversion drop at 11 PM and hiking bids by 400%, or auto-publishing an unreviewed post during a national/religious occasion); a governance OPERATING_FRAMEWORK locks write-access behind cryptographic/human approval gates.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: إن منح وكلاء الذكاء الاصطناعي المستقلين صلاحية الكتابة المباشرة (`Write Access`) على حسابات الإعلانات الحية أو النشر الفوري يعرض المنشأة لكوارث مالية ونظامية (مثل مضاعفة الميزانية ليلاً بسبب تأخر بيانات الدفع عند الاستلام، أو نشر ادعاء غير مرخص من الغذاء والدواء)؛ لذا يفرض هذا الإطار التشغيلي بوابات اعتماد بشرية وقواطع أمان برمجية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before granting any AI agent, automation script, or third-party AI optimization tool API access to Meta Ads, Google Ads, Snapchat/TikTok Ads, Salla/Zid/Shopify catalogs, or social/email publishing accounts.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل منح أي وكيل ذكاء اصطناعي أو أداة تحسين آلي صلاحية الوصول (`API Token`) لحسابات الإعلانات أو المتاجر أو النشر.
- **When NOT to Use It (EN)**: Never grant an autonomous AI agent unthrottled `ads_management` write permissions to increase campaign budgets or publish live ad creatives without a human-in-the-loop approval step!
- **متى لا تستخدم هذه الأداة (AR)**: يُحظر تماماً منح أي وكيل ذكاء اصطناعي صلاحية مفتوحة لرفع الميزانيات الإعلانية أو نشر إعلانات جديدة مباشرة للجمهور دون خطوة اعتماد بشري!

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Inventory of all connected AI Agent API tokens (`Meta Marketing API`, `Google Ads API`, `Salla/Zid/Shopify Admin API`, `WhatsApp Cloud API`)
2. Maximum Daily Budget Delta Ceiling (`<= 15–20%` change per 48 hours so learning phases never reset!)
3. Human Approval Slack / Microsoft Teams / WhatsApp Admin channel (`Approve / Reject` webhook)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Marketing API / Google Ads API (`status: PAUSED` Staging) & WordPress/Shopify Role Scopes** | `supported` | [Official Reference](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) (`2026-10-25`) | All major ad and e-commerce APIs support creating entities in `PAUSED` or `DRAFT` state and scoping OAuth tokens to read-only or draft-only permissions. | Enforce `validate_agent_mutation_request()` in your middleware so no agent tool call can set `status: ACTIVE` or mutate budgets `>20%` without a verified `human_approver_signature`. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-460`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Mandatory human approval gate logging evidence, risk level, and rollback state before any API mutation executes.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-470`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Mandatory human approval gate logging evidence, risk level, and rollback state before any API mutation executes.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-480`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Mandatory human approval gate logging evidence, risk level, and rollback state before any API mutation executes.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-490`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Mandatory human approval gate logging evidence, risk level, and rollback state before any API mutation executes.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-500`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Mandatory human approval gate logging evidence, risk level, and rollback state before any API mutation executes.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Scenario**: A Dubai & Riyadh Performance Agency connected an autonomous LLM Media-Buyer Agent to Meta and Google Ads APIs with instructions to `'check ROAS every 3 hours and scale winning ad sets'`.
- **Disaster Prevented**: On Friday at `12:30 PM` (during Friday Jumu'ah prayer when KSA checkout volume naturally pauses for 90 minutes, and before COD confirmations `AMP-062` settled), the agent saw a temporary 2-hour ROAS dip on Campaign A and a 2-hour spike on Campaign B; it tried to cut Campaign A's budget by `70%` and increase Campaign B's budget by `300%` (`from $500/day to $2,000/day`), which would have reset Meta's learning phase on both campaigns!
- **Human Review & Key Edits Applied**: 1. **Locked Agent Evaluation Window to Minimum 7-Day Rolling Window (`AMP-391`)**: Forbade the agent from evaluating performance on `<7-day` or intraday windows in MENA (due to COD settlement lag `AMP-062` and Friday prayer / weekend curves).
2. **Enforced `status: "PAUSED"` on All Agent-Created Ads**: Every new ad variation created by the creative agent lands in Ads Manager as `PAUSED` until the human buyer checks Advantage+ Creative toggles (`AMP-065`), SFDA/Discount compliance (`AMP-064`, `AMP-176`), and clicks `Approve`.
- **Final Usable Output**: - `validate_agent_mutation_request()` proxy firewall deployed across all agency ad accounts; zero runaway spend incidents, zero learning-phase resets, and 100% human sign-off on live creatives and `>20%` budget shifts.
- **What Can Go Wrong**: An autonomous SEO/blog agent is given direct WordPress `Administrator` credentials and publishes 40 unreviewed articles overnight containing a hallucinated GASTAT statistic (`AMP-179`) and a therapeutic skincare claim (`AMP-176`).
- **Correction & Fallback**: Issue CMS API keys to AI agents strictly under the **`Contributor` role (`can create Drafts only, cannot Publish`)**—never `Administrator` or `Editor`!

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero unauthorized live budget spikes or unreviewed public posts (`Target: 0 incidents`), Campaign Learning-Phase Stability (`% of budget in Active vs. Learning Reset`), and Human Review Turnaround Time on Staged Drafts.
- **Baseline Definition**: Audit of active API tokens and past automated rule misfires.
- **Observation Window**: Enforced continuously at the API gateway layer. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Human-in-the-loop gates and circuit-breakers prevent catastrophic agent errors while preserving 90% of the time-savings of automated research and draft staging.
