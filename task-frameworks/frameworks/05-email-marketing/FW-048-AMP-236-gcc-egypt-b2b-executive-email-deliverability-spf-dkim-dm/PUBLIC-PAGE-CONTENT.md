# GCC & Egypt B2B Executive Email Deliverability (SPF/DKIM/DMARC) & Bilingual Conciseness Checklist
## <span dir="rtl">قائمة فحص موثوقية نطاق البريد (`SPF/DKIM/DMARC`) وهيكلة رسائل الشركات (`B2B`) ثنائية اللغة في الخليج ومصر</span>

> **Asset ID**: `FW-048` (`AMP-236`) | **Artifact Type**: `CHECKLIST` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Authenticate sending domains (`SPF`, `DKIM`, `DMARC`, `List-Unsubscribe`) and format B2B executive emails under 90 words per language block so messages land in Primary corporate inboxes in Riyadh, Dubai, Doha, and Cairo.
- **AR**: <span dir="rtl">توثيق نطاقات الإرسال البريدي (`SPF`, `DKIM`, `DMARC`, `List-Unsubscribe`) وصياغة رسائل الشركات التنفيذية (`B2B`) في أقل من 90 كلمة لكل لغة لضمان وصولها لصندوق الوارد الرئيسي في الرياض ودبي والدوحة والقاهرة.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before launching B2B lifecycle, event invitation, webinar follow-up, or account-based marketing emails to corporate domains (`.sa`, `.ae`, `.qa`, `.eg`, `.com`) in MENA.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل إرسال رسائل الشركات (`B2B`) أو دعوات المؤتمرات أو متابعات المبيعات للنطاقات المؤسسية في الخليج ومصر.</span>
- **When NOT to Use It (EN)**: Do not send bulk marketing sequences to unconsented scraped lists (`AMP-232`) or from your primary corporate root domain without subdomain isolation.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا ترسل حملات تسويقية لقوائم مجمعة بدون موافقة (`AMP-232`) ولا تستخدم النطاق الرئيسي للشركة في الحملات الجماعية دون عزل النطاق الفرعي.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Sending Domain DNS records (`TXT` records for `SPF`, `DKIM`, `DMARC`)
- Opt-in B2B Contact Segment (`Role`, `City`, `Language Preference: AR / EN / Bilingual`)
- Single concrete value hook + 1 low-friction CTA

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 1. Technical DNS & Header Deliverability Checklist (Run Before First Send)
- [ ] **Check 1 — SPF Alignment (`TXT @`)**: Single `v=spf1` record authorizing your ESP (`include:... -all` or `~all`) with `<= 10` DNS lookups total.
- [ ] **Check 2 — 2048-Bit DKIM Signature**: Active DKIM selector (`s1._domainkey.yourdomain.sa`) signing `From`, `Subject`, and `To` headers.
- [ ] **Check 3 — DMARC Policy (`TXT _dmarc`)**: At minimum `v=DMARC1; p=quarantine; pct=100; rua=mailto:dmarc@yourdomain.sa; adkim=r; aspf=r;` (mandatory for Gmail/Yahoo/Microsoft enterprise gateways).
- [ ] **Check 4 — RFC 8058 One-Click `List-Unsubscribe` Header**: Enabled in ESP headers (`List-Unsubscribe-Post: List-Unsubscribe=One-Click`).

### 2. The `<90-Word` GCC/Egypt Executive Bilingual Email Template
In Riyadh, Dubai, and Cairo corporate environments, executives read emails on mobile between meetings, and decision committees often include both native Arab leaders and international/expat VPs:
```text
Subject: [أقل من 38 حرفاً بالعربية | Or Crisp 6-Word English Subject]

أهلاً [الاسم الأول]،

لاحظنا خلال مشاركتكم في [اسم الفعالية / تحميلكم لتقرير قطاع X] اهتمام فريقكم في [اسم الشركة] بتقليص وقت [المشكلة المحددة، مثلاً: مطابقة فواتير الموردين مع المرحلة الثانية من فاتورة ZATCA].

في [اسم شركتنا]، ساعدنا فرق المالية في [مثال حقيقي بالرياض/دبي] على خفض وقت المطابقة الشهرية من 5 أيام إلى 4 ساعات دون تغيير نظام الـ ERP الحالي.

هل يناسبكم اتصال سريع لمدة 12 دقيقة يوم الثلاثاء أو الأربعاء القادم لاستعراض آلية الربط؟

خالص التحية،
[الاسم والمنصب]
---
Hi [First Name],

Following your download of our [Report / Event Check-in], here is a quick 1-page breakdown of how finance teams in [Riyadh/Dubai/Cairo] cut monthly reconciliation from 5 days to 4 hours without replacing their existing ERP.

Would a brief 12-minute call this Tuesday or Wednesday work to walk through the architecture?

Best regards,
[Name & Title] | [1-Click Unsubscribe Link]
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Sender**: Riyadh & Dubai Enterprise Cybersecurity & Cloud Compliance Provider sending follow-ups to 450 opted-in LEAP / GITEX booth visitors.
- **Problem**: Previous AI sequence sent a 420-word English-only essay with 6 links and 2 PDF attachments from a domain missing `_dmarc`; Microsoft Defender 365 routed `71%` of emails to Quarantine/Junk at Saudi & Emirati enterprise banks.

### Step B: Initial Output (`المخرج الأولي`)
- **DNS Audit & Fix**: Published 2048-bit DKIM + `_dmarc` (`p=quarantine`) on dedicated sending subdomain `updates.cyber-example.sa`, removed PDF attachments (replaced with 1 tracked first-party link), and compressed the message into a `68-word` Arabic + `54-word` English executive note.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Workweek Timing Check (`AMP-391`)**: Scheduled sends for **Monday–Wednesday at `10:00 AM` local Riyadh/Dubai time** (avoiding Friday/Saturday weekend and Sunday morning inbox backlog).
2. **RTL Alignment on Bilingual Block**: Wrapped the top Arabic paragraph in `<div dir="rtl" style="direction:rtl; text-align:right;">` and the bottom English summary in `<div dir="ltr" style="direction:ltr; text-align:left;">` (`AMP-231`).

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Enterprise inbox placement rose from `29%` to `96.4%`, with positive executive reply rate increasing across both Arabic-first (KSA government/enterprise) and English-first (UAE multinational) recipients.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An AI outreach tool inserts 4 different tracking links, a Calendly iframe, and an external image signature into a B2B follow-up email; corporate Barracuda/Mimecast gateways at Saudi and Emirati enterprises block the email for high link-to-text ratio.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Keep executive B2B follow-up emails to **plain-text-style minimal HTML (`<= 1` link total, `0` heavy image banners, `< 90` words per language)** and ask for a direct calendar reply (`'هل يناسبكم يوم الثلاثاء الساعة 11 صباحاً؟'`).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Google / Yahoo / Microsoft 365 Bulk Sender Requirements (SPF, DKIM, DMARC & RFC 8058)** | `supported` | [Official Docs](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) (`2026-10-25`) | Enterprise mail gateways strictly enforce SPF/DKIM alignment, DMARC policies, and low link-to-text ratios on inbound B2B emails. | Verify DNS records via `dig TXT _dmarc.yourdomain.com` before launching any B2B sequence. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: DMARC Alignment Pass Rate (`Target: 100%`), Bounce/Quarantine Rate (`Target: <1.5%`), and Positive Reply / Meeting Booked Rate.
- **Baseline**: Prior campaign bounce and reply rates.
- **Observation Window**: 7–14 days per campaign cohort.
- **Interpretation Boundary**: Authentication and concise bilingual formatting ensure the executive reads your message, while offer relevance and event context drive meeting conversion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Gulf Arabic Dialects: Why Generic AI Agents Fail Khaleeji Customers](https://www.aisyncso.com/en/blog/gulf-arabic-dialects-enterprise-ai-agents) — *AISyncSo* (Published `2026-09-24`, Accessed `2026-10-25`): Shows why customer-facing AI agents trained on MSA fail to parse everyday Khaleeji phrasing, politeness formulas, and intent in Riyadh, Dubai, and Doha.
- [Common Mistakes When Using AI in B2B Sales and Marketing](https://founderz.com/blog/common-mistakes-ai-b2b-sales-marketing/) — *Founderz* (Published `2026-08-15`, Accessed `2026-10-25`): Automating B2B outreach and lead generation on top of uncleaned CRM data or without sales-marketing ICP alignment amplifies errors and lengthens the sales cycle.
