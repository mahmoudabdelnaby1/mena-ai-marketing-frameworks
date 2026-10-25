# UAE TDRA Marketing SMS Curfew (`9:00 PM – 7:00 AM` Block), `AD-` Sender Prefix & Opt-Out Compliance Checklist
## <span dir="rtl">قائمة فحص الامتثال للوائح هيئة تنظيم الاتصالات الإماراتية (`TDRA` — حظر الرسائل الترويجية من `9 مساءً حتى 7 صباحاً` وبادئة `AD-`)</span>

> **Asset ID**: `FW-084` (`AMP-442`) | **Artifact Type**: `CHECKLIST` | **Channel**: Marketing Automation | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Configure UAE SMS and automated marketing pipelines to strictly enforce TDRA's `9:00 PM to 7:00 AM` Gulf Standard Time (`UTC+4`) promotional curfew, mandatory `AD-` Sender ID prefix, and free opt-out mechanism.
- **AR**: <span dir="rtl">ضبط أنظمة أتمتة الرسائل النصية (`SMS`) الموجهة للإمارات للالتزام الصارم بحظر الإرسال الليلي من `9:00 مساءً حتى 7:00 صباحاً` بتوقيت الإمارات (`UTC+4`)، وإضافة بادئة `AD-` لاسم المرسل، وتفعيل آلية الإلغاء المجانية.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever configuring SMS marketing broadcasts or automated behavioral triggers (abandoned cart, win-back, flash sale) targeting UAE mobile numbers (`+971 5...`).
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد أي حملة رسائل نصية (`SMS`) أو رسائل آلية (مثل تذكير السلة المتروكة) تستهدف أرقام الهواتف الإماراتية (`+971`).</span>
- **When NOT to Use It (EN)**: Never allow an automated `'Wait 1 Hour -> Send Abandoned Cart SMS'` workflow to fire at `10:15 PM` Dubai time when a shopper abandons their cart at `9:15 PM`—queue it until `7:15 AM` (or `9:00 AM`) the next morning!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تسمح أبداً لتدفق آلي («انتظر ساعة واحدة ثم أرسل SMS للسلة المتروكة») بالإرسال في الساعة `10:15 مساءً` بتوقيت دبي؛ بل اضبط النظام لتأجيل الإرسال تلقائياً إلى الصباح التالي بعد الساعة `7:00 صباحاً`!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- SMS Gateway Configuration (`Etisalat by e& / du` registered `AD-BrandName` Sender ID via Unifonic, Twilio, Infobip, or CEQUENS)
- Automation Workflow Quiet-Hours / Send-Window settings locked to `Asia/Dubai (UTC+4)`
- Verified Opt-In Consent & Master DND Suppression List (`AMP-232`, `AMP-233`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### UAE TDRA Promotional SMS Compliance Checklist & Quiet-Hours Gate (`Verified 2026-10-25`)

#### 1. The 5 Mandatory UAE TDRA Rules (`Policy v1.1 s. 8.3, 8.8, 9.2.4, 9.2.5`)
- [ ] **Rule 1 — Strict `9:00 PM to 7:00 AM` (`Asia/Dubai UTC+4`) Curfew Gate**:
  - **Allowed Sending Window**: Strictly **`07:00:00` to `20:59:59` UAE Local Time (`UTC+4`)** (Recommended practical window: `08:30 AM – 08:30 PM` to leave a 30-minute safety buffer for carrier queue latency!).
  - **Prohibited Window**: **`21:00:00` (`9:00 PM`) to `06:59:59` (`7:00 AM`) UAE time** — applies to BOTH batch broadcasts AND automated triggers (abandoned cart, browse abandonment, win-back)!
- [ ] **Rule 2 — Mandatory `AD-` Alphanumeric Sender ID Prefix**:
  - Every promotional SMS sent to `+971` numbers MUST use an Etisalat (`e&`) / `du` registered promotional Sender ID prefixed with **`AD-`** (e.g., `AD-MyBrand`), NEVER a transactional sender ID (`MyBrand` without `AD-`, which is reserved strictly for OTPs and bank/order receipts!).
- [ ] **Rule 3 — Prior Consent & Physical Address / Identity Record (`AMP-232`)**:
  - Send only to recipients with documented prior opt-in consent (`TDRA s. 8.3`).
- [ ] **Rule 4 — Clear, Free Opt-Out Instruction in Every Message (`s. 8.8 & 9.2.4`)**:
  - Include a clear Arabic/English opt-out suffix (e.g., `"للإلغاء أرسل STOP إلى XXXX"` / `"لإيقاف الرسائل: [Opt-out link/code]"`).
- [ ] **Rule 5 — Never Re-Prompt Users to 'Confirm Opt-Out' (`s. 9.2.5`)**:
  - Once a user sends `STOP` / `قف` / clicks opt-out, suppress them immediately (`AMP-233`); sending follow-up messages asking them to 'confirm' or 're-subscribe' is prohibited.

#### 2. Copy-Ready Python / Node Quiet-Hours Queue Gate for `+971` Numbers
```python
from datetime import datetime, time, timedelta
from zoneinfo import ZoneInfo

UAE_TZ = ZoneInfo("Asia/Dubai")

def get_tdra_safe_send_timestamp(phone_e164: str, now_utc: datetime = None) -> datetime:
    now_utc = now_utc or datetime.now(ZoneInfo("UTC"))
    # Apply strict 08:30 to 20:30 Dubai window (with 30-min carrier buffer inside 07:00-21:00 TDRA law)
    if str(phone_e164).lstrip("+").startswith("971"):
        dubai_now = now_utc.astimezone(UAE_TZ)
        t = dubai_now.time()
        if t >= time(20, 30):
            # Queue for 08:30 AM next morning Dubai time
            next_morning = (dubai_now + timedelta(days=1)).replace(hour=8, minute=30, second=0, microsecond=0)
            return next_morning
        elif t < time(8, 30):
            # Queue for 08:30 AM today Dubai time
            same_morning = dubai_now.replace(hour=8, minute=30, second=0, microsecond=0)
            return same_morning
    return now_utc
```

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Brand**: Dubai & Riyadh D2C Fashion Brand running Klaviyo / Braze SMS automations.
- **Violations Detected**:
  1. The `'1-Hour Abandoned Cart SMS'` fired at `11:40 PM` Dubai time whenever late-night shoppers abandoned carts at `10:40 PM`.
  2. Marketing team sent a flash-sale blast over the transactional `BrandOTP` sender ID (missing the `AD-` prefix) to avoid promotional filtering.

### Step B: Initial Output (`المخرج الأولي`)
- **Compliance Remediation**:
  1. Enabled `get_tdra_safe_send_timestamp()` / Smart Quiet Hours (`20:30 to 08:30 Asia/Dubai`) on all automated flows targeting `+971` numbers so late-night triggers hold safely until `08:30 AM` GST.
  2. Locked all promotional flows strictly to the registered `AD-BrandName` Sender ID and reserved `BrandOTP` exclusively for `AUTHENTICATION` / transactional delivery notices (`AMP-237`).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added 30-Minute Carrier Buffer (`20:30` Cutoff Instead of `20:59`)**: Because bulk SMS batches of 50,000 messages can take 15–25 minutes to drain through telecom SMPP queues, stopped initiating UAE promotional batches after **`8:30 PM` Dubai time** so no trailing message ever lands on a phone at `9:02 PM`!
2. **Extended Similar Respectful Quiet Hours to KSA (`CST`) & Egypt (`NTRA`)**: Applied evening quiet hours (`9:30 PM – 8:30 AM` local time) across KSA and Egypt promotional SMS as well.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `100%` of UAE promotional SMS traffic locked to `AD-` Sender ID within the `08:30 AM – 08:30 PM` (`Asia/Dubai`) safe window, with zero night-curfew violations.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An international marketing team in London (`UTC+0`) schedules a UAE SMS broadcast for `'6:00 PM London Time'`, forgetting that Dubai (`UTC+4`) is 4 hours ahead—delivering the promotional SMS to 40,000 Emirati phones at **`10:00 PM` Dubai time** (1 hour into the TDRA illegal curfew window!).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always configure SMS campaign schedulers to use **`Recipient Local Timezone (Asia/Dubai UTC+4)`**, NEVER the marketer's browser/headquarters timezone!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **UAE TDRA Unsolicited Electronic Communications Regulatory Policy v1.1 & e&/du SMPP Filtering** | `supported` | [Official Docs](https://kaeloglobal.com/digital-marketing/uae-data-protection-marketing/) (`2026-10-25`) | Kaelo Global Oct 2026 review confirms TDRA's 9:00 PM – 7:00 AM marketing SMS curfew (s. 8.8), `AD-` prefix mandate, prior consent requirement (s. 8.3), and ban on re-prompting unsubscribed users (s. 9.2.5). | Enforce `get_tdra_safe_send_timestamp()` at the SMS gateway wrapper level so no upstream tool can accidentally fire a promotional SMS to `+971` during curfew hours. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero promotional SMS dispatches to `+971` numbers between `21:00 and 07:00 Asia/Dubai`, `100%` `AD-` Sender ID compliance, and Zero carrier Sender-ID blocks.
- **Baseline**: Audit of last 30 days of SMS gateway delivery timestamps in `Asia/Dubai` time.
- **Observation Window**: Monitored continuously in SMS gateway logs.
- **Interpretation Boundary**: Curfew and `AD-` compliance prevent telecom blacklisting and TDRA fines, while offer relevance drives SMS click conversion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Data protection laws | The Official Portal of the UAE Government](https://u.ae/en/about-the-uae/digital-uae/data/data-protection-laws) — *UAE Government Portal* (Published `2025-12-04`, Accessed `2026-10-25`): UAE Federal Decree-Law No. 45 of 2021 (PDPL) prohibits personal data processing without owner consent and grants the right to object to direct marketing.
- [UAE PDPL Marketing Rules for Email and SMS | Kaelo Global](https://kaeloglobal.com/digital-marketing/uae-data-protection-marketing/) — *Kaelo Global* (Published `2026-10-22`, Accessed `2026-10-25`): UAE PDPL (Decree-Law 45/2021 Art. 4 & 17) has no general legitimate-interest exception for direct marketing; TDRA Spam Policy v1.1 mandates opt-in, 'AD-' sender prefix, free opt-out, a strict 9:00 PM to 7:00 AM curfew on marketing SMS, and 2-year consent record retention.
