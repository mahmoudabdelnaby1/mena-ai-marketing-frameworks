# FW-030: MENA Social Crisis-Response & Anti-Hallucination Escalation Playbook (X, Facebook & TikTok)
## دليل التشغيل للرد على الأزمات والشكاوى العلنية على إكس وفيسبوك وتيك توك (منع اعتراف الذكاء الاصطناعي بالمسؤولية أو اختلاق التعويضات)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-138`, `AMP-148`, `AMP-158`, `AMP-168`
- **Selected Artifact Type**: `PLAYBOOK`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent AI social media responders from admitting legal liability, inventing unauthorized refund/compensation policies, or arguing with viral complainants on X (Twitter), Facebook, and TikTok.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع أدوات الرد بالذكاء الاصطناعي من الإقرار بمسؤولية قانونية غير محققة أو اختلاق وعود تعويض غير معتمدة أو الدخول في جدال علني مع الشكاوى المتداولة على إكس وفيسبوك وتيك توك.
- **Why `PLAYBOOK` Fits This User Job (EN)**: During a public complaint or viral thread in KSA (on X) or Egypt (on Facebook/TikTok), unguided LLMs default to Western crisis templates that either admit fault prematurely or invent fake compensation promises (`'سنعوضك بمبلغ 500 ريال فوراً'`); a human-in-the-loop PLAYBOOK enforces safe de-escalation.
- **لماذا يناسب شكل `PLAYBOOK` هذه المهمة (AR)**: عند ظهور شكوى علنية متداولة في السعودية (عبر إكس) أو مصر (عبر فيسبوك/تيك توك)، تميل النماذج اللغوية غير المقيدة إلى الاعتراف بالخطأ القانوني أو اختلاق تعويضات وهمية؛ لذا يضبط دليل التشغيل هذا مسار الاحتواء الآمن.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when managing public social media comments, viral complaints, delivery delays, or product quality allegations on X, Facebook, Instagram, or TikTok in MENA.
- **متى تستخدم هذه الأداة (AR)**: يُستخدم عند التعامل مع الشكاوى العلنية أو التغريدات والمنشورات الغاضبة المتعلقة بتأخر الشحن أو جودة المنتج على إكس وفيسبوك وإنستغرام وتيك توك.
- **When NOT to Use It (EN)**: Never allow an autonomous AI agent to publish public replies to crisis threads, regulatory tags (`@Mcgovsa`, `@SFDA`, `@CPA`), or influencer complaints without human sign-off (`AMP-450`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تسمح أبداً لأي وكيل ذكاء اصطناعي بنشر رد علني تلقائي على تغريدات الأزمات أو المنشورات التي تتضمن إشارة للجهات الرقابية (`@Mcgovsa`، `@SFDA`، جهاز حماية المستهلك) دون اعتماد بشري (`AMP-450`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Approved Company Return, Refund & SLA Compensation Policy Document (the ONLY allowed source of truth)
2. Escalation Severity Matrix (Tier 1 Routine Shipping Delay vs. Tier 2 Viral Post vs. Tier 3 Regulatory/Health/Safety Mention)
3. Direct Private Escalation Channel (Dedicated VIP Support WhatsApp or Direct Message link)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Public Social Complaint Triage & De-Escalation Playbook

#### 1. Severity Tier Routing Matrix (Zero Autonomous Publishing on Tier 2 & Tier 3)
| Tier | Trigger Conditions | AI Role | Mandatory Response Rule |
| :--- | :--- | :--- | :--- |
| **Tier 1: Routine Individual Inquiry / Order Delay** | Single comment (`"طلبي متأخر رقم #1234"`, `"فين الأوردر؟"`), `< 5` likes/replies, no regulatory/health allegations. | Drafts polite public bridge reply for 1-click human approval. | Acknowledge politely in 1 sentence + move immediately to DM/WhatsApp to protect customer data (`PDPL`). Never post tracking links or customer names publicly! |
| **Tier 2: High-Velocity / Creator Thread** | Post/Tweet with `> 20` engagements, creator complaint, or repeated comment storm during White Friday/Ramadan. | Summarizes timeline + order history internally for Crisis Lead; **PUBLIC AUTO-REPLY BLOCKED**. | Human Community Lead posts a calm, non-defensive empathy bridge within 15 minutes and resolves via phone call before posting a brief public resolution update. |
| **Tier 3: Regulatory, Health/Safety, Fraud, or Legal Tag** | Mentions `@Mcgovsa` (KSA Commerce), `@SFDA`, `@GAMR_SA`, Egypt CPA, food poisoning, allergic reaction, data breach, or legal threat. | **100% LOCKED (Zero AI Drafting Without Legal/PR Input)**. | Immediate alert to Legal + Executive Operations; verify internal logs before issuing any statement. |

#### 2. Copy-Ready Grounded De-Escalation Prompt (For Tier 1 & Tier 2 Human Review)
```xml
<system_role>
You are a MENA Customer Care Communications Specialist.
Draft a concise, respectful public reply to move a customer complaint to private DM/WhatsApp for immediate resolution.
STRICT GUARDRAILS:
1. NEVER admit legal fault, product defect, or systemic failure before the operations team inspects the order.
2. NEVER invent or promise any discount code, cash refund, gift, or compensation not explicitly provided in <approved_policy>.
3. NEVER post any personal customer data (full name, phone, address, or courier tracking link) in a public comment (Saudi/UAE/Egypt PDPL violation!).
4. Use respectful White Saudi/Gulf Arabic (for KSA/GCC) or Polite Egyptian White Arabic (for Egypt).
</system_role>
<approved_policy>{{EXACT_APPROVED_POLICY_TEXT}}</approved_policy>
<customer_public_comment>{{RAW_PUBLIC_COMMENT}}</customer_public_comment>
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic Claude Guardrails — Reducing Hallucinations & Policy Grounding** | `supported` | [Official Reference](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) (`2026-10-25`) | Anthropic's official hallucination-reduction guidance recommends restricting the model strictly to supplied policy documents and explicitly forbidding extrapolation beyond the text. | Keep all public complaint replies in 'Draft for Human Approval' mode. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-138`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Pre-approved legal escalation decision trees with locked response templates.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-148`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Pre-approved legal escalation decision trees with locked response templates.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-158`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Pre-approved legal escalation decision trees with locked response templates.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-168`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Pre-approved legal escalation decision trees with locked response templates.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Platform**: X (Twitter) in Saudi Arabia.
- **Public Tweet by Customer**: `"طلبت من متجركم قبل 4 أيام للرياض وللحين ما وصلت الشحنة ولا أحد يرد! أسوأ تجربة، تواصلت معكم وما في فايدة!"`
- **Unsafe Raw AI Reply (Before Playbook)**: `"نعتذر بشدة عن فشل نظام الشحن لدينا وضياع شحنتك! سنقوم فوراً بإرجاع كامل المبلغ لحسابك مع قسيمة تعويض بقيمة 200 ريال هدية منا!"` *(Hallucinated a lost shipment, admitted systemic failure, and invented an unauthorized 200 SAR gift voucher!)*
- **Human Review & Key Edits Applied**: 1. **Verified Operations Action First**: Human agent checked the order in the dashboard, saw it was out for delivery with SMSA in North Riyadh, called the customer within 6 minutes, and confirmed delivery that evening.
2. **Customer Follow-Up Tweet**: Customer voluntarily replied under the thread: `"تواصلوا معي وما قصروا، وصلت الطلبية نفس اليوم شكراً لكم"`.
- **Final Usable Output**: - Public thread de-escalated in `<10` minutes with zero unauthorized financial promises, zero PDPL privacy leaks, and documented public resolution.
- **What Can Go Wrong**: An automated comment responder replies to a customer complaining about an allergic skin reaction with `'منتجاتنا آمنة 100% ومستحيل تسبب حساسية، المشكلة من طريقة استخدامك!'`, igniting a viral backlash and SFDA scrutiny.
- **Correction & Fallback**: Hard-code a keyword kill-switch on all social auto-responders: any comment containing health/safety/regulatory tokens (`حساسية، تسمم، مستشفى، وزارة التجارة، بلاغ، نصب، احتيال، الغذاء والدواء، حماية المستهلك`) is routed silently to the Human Escalation Slack/WhatsApp channel with **zero automated public reply**.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero unauthorized AI compensation promises or public PDPL leaks, and First Human Response Time on Tier 1/2 escalations (`Target: <15 minutes`).
- **Baseline Definition**: Historical complaint resolution SLA and escalation audit.
- **Observation Window**: Monitored continuously across all active social profiles. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Polite public de-escalation protects brand reputation, while actual operational resolution (courier dispatch / refund processing) determines customer retention.
