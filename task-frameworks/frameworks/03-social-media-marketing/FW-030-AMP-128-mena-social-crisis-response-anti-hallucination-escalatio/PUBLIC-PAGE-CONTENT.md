# MENA Social Crisis-Response & Anti-Hallucination Escalation Playbook (X, Facebook & TikTok)
## <span dir="rtl">دليل التشغيل للرد على الأزمات والشكاوى العلنية على إكس وفيسبوك وتيك توك (منع اعتراف الذكاء الاصطناعي بالمسؤولية أو اختلاق التعويضات)</span>

> **Asset ID**: `FW-030` (`AMP-128`) | **Artifact Type**: `PLAYBOOK` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent AI social media responders from admitting legal liability, inventing unauthorized refund/compensation policies, or arguing with viral complainants on X (Twitter), Facebook, and TikTok.
- **AR**: <span dir="rtl">منع أدوات الرد بالذكاء الاصطناعي من الإقرار بمسؤولية قانونية غير محققة أو اختلاق وعود تعويض غير معتمدة أو الدخول في جدال علني مع الشكاوى المتداولة على إكس وفيسبوك وتيك توك.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when managing public social media comments, viral complaints, delivery delays, or product quality allegations on X, Facebook, Instagram, or TikTok in MENA.
- **متى تستخدمها (AR)**: <span dir="rtl">يُستخدم عند التعامل مع الشكاوى العلنية أو التغريدات والمنشورات الغاضبة المتعلقة بتأخر الشحن أو جودة المنتج على إكس وفيسبوك وإنستغرام وتيك توك.</span>
- **When NOT to Use It (EN)**: Never allow an autonomous AI agent to publish public replies to crisis threads, regulatory tags (`@Mcgovsa`, `@SFDA`, `@CPA`), or influencer complaints without human sign-off (`AMP-450`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تسمح أبداً لأي وكيل ذكاء اصطناعي بنشر رد علني تلقائي على تغريدات الأزمات أو المنشورات التي تتضمن إشارة للجهات الرقابية (`@Mcgovsa`، `@SFDA`، جهاز حماية المستهلك) دون اعتماد بشري (`AMP-450`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Approved Company Return, Refund & SLA Compensation Policy Document (the ONLY allowed source of truth)
- Escalation Severity Matrix (Tier 1 Routine Shipping Delay vs. Tier 2 Viral Post vs. Tier 3 Regulatory/Health/Safety Mention)
- Direct Private Escalation Channel (Dedicated VIP Support WhatsApp or Direct Message link)

## 2. The Working `PLAYBOOK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Platform**: X (Twitter) in Saudi Arabia.
- **Public Tweet by Customer**: `"طلبت من متجركم قبل 4 أيام للرياض وللحين ما وصلت الشحنة ولا أحد يرد! أسوأ تجربة، تواصلت معكم وما في فايدة!"`
- **Unsafe Raw AI Reply (Before Playbook)**: `"نعتذر بشدة عن فشل نظام الشحن لدينا وضياع شحنتك! سنقوم فوراً بإرجاع كامل المبلغ لحسابك مع قسيمة تعويض بقيمة 200 ريال هدية منا!"` *(Hallucinated a lost shipment, admitted systemic failure, and invented an unauthorized 200 SAR gift voucher!)*

### Step B: Initial Output (`المخرج الأولي`)
- **Playbook-Compliant Draft (Reviewed & Sent by Human Agent in 4 Minutes)**:
  `"أهلاً بك أخي الكريم، حقك علينا ويهمنا جداً وصول طلبك بأسرع وقت. تفضل بتزويدنا برقم الطلب عبر الرسائل الخاصة الآن، وسيتابع فريق العمليات شحنتك فوراً ويتواصل معك هاتفياً خلال دقائق. أبشر بالخير."`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified Operations Action First**: Human agent checked the order in the dashboard, saw it was out for delivery with SMSA in North Riyadh, called the customer within 6 minutes, and confirmed delivery that evening.
2. **Customer Follow-Up Tweet**: Customer voluntarily replied under the thread: `"تواصلوا معي وما قصروا، وصلت الطلبية نفس اليوم شكراً لكم"`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Public thread de-escalated in `<10` minutes with zero unauthorized financial promises, zero PDPL privacy leaks, and documented public resolution.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An automated comment responder replies to a customer complaining about an allergic skin reaction with `'منتجاتنا آمنة 100% ومستحيل تسبب حساسية، المشكلة من طريقة استخدامك!'`, igniting a viral backlash and SFDA scrutiny.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Hard-code a keyword kill-switch on all social auto-responders: any comment containing health/safety/regulatory tokens (`حساسية، تسمم، مستشفى، وزارة التجارة، بلاغ، نصب، احتيال، الغذاء والدواء، حماية المستهلك`) is routed silently to the Human Escalation Slack/WhatsApp channel with **zero automated public reply**.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic Claude Guardrails — Reducing Hallucinations & Policy Grounding** | `supported` | [Official Docs](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) (`2026-10-25`) | Anthropic's official hallucination-reduction guidance recommends restricting the model strictly to supplied policy documents and explicitly forbidding extrapolation beyond the text. | Keep all public complaint replies in 'Draft for Human Approval' mode. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero unauthorized AI compensation promises or public PDPL leaks, and First Human Response Time on Tier 1/2 escalations (`Target: <15 minutes`).
- **Baseline**: Historical complaint resolution SLA and escalation audit.
- **Observation Window**: Monitored continuously across all active social profiles.
- **Interpretation Boundary**: Polite public de-escalation protects brand reputation, while actual operational resolution (courier dispatch / refund processing) determines customer retention.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Reduce hallucinations - Claude Platform Docs](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) — *Anthropic* (Published `2026-08-15`, Accessed `2026-10-25`): Instructing the model to allow 'I do not know', extract verbatim quotes first, and restrict claims to supplied documents measurably reduces hallucinated facts.
- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
