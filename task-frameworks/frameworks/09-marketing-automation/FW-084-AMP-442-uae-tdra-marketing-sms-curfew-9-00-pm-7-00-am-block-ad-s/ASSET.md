# FW-084: UAE TDRA Marketing SMS Curfew (`9:00 PM – 7:00 AM` Block), `AD-` Sender Prefix & Opt-Out Compliance Checklist
## قائمة فحص الامتثال للوائح هيئة تنظيم الاتصالات الإماراتية (`TDRA` — حظر الرسائل الترويجية من `9 مساءً حتى 7 صباحاً` وبادئة `AD-`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-452`, `AMP-462`, `AMP-472`, `AMP-482`, `AMP-492`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Configure UAE SMS and automated marketing pipelines to strictly enforce TDRA's `9:00 PM to 7:00 AM` Gulf Standard Time (`UTC+4`) promotional curfew, mandatory `AD-` Sender ID prefix, and free opt-out mechanism.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: ضبط أنظمة أتمتة الرسائل النصية (`SMS`) الموجهة للإمارات للالتزام الصارم بحظر الإرسال الليلي من `9:00 مساءً حتى 7:00 صباحاً` بتوقيت الإمارات (`UTC+4`)، وإضافة بادئة `AD-` لاسم المرسل، وتفعيل آلية الإلغاء المجانية.
- **Why `CHECKLIST` Fits This User Job (EN)**: Kaelo Global's Oct 2026 legal analysis of the UAE Telecommunications and Digital Government Regulatory Authority (`TDRA`) Unsolicited Electronic Communications Regulatory Policy v1.1 (s. 8.3, 8.8, 9.2.4, 9.2.5) confirms that marketing texts in the UAE are strictly barred between `9:00 PM and 7:00 AM` local time, must carry the `AD-` sender prefix, require prior opt-in consent, and must cease immediately upon opt-out; global AI automation flows triggered at `10:30 PM` (e.g., an evening '1-hour abandoned cart SMS') violate TDRA curfew automatically unless gated!
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تؤكد اللائحة التنظيمية لهيئة تنظيم الاتصالات والحكومة الرقمية الإماراتية (`TDRA` — الأقسام 8.3 و8.8 و9.2.4 و9.2.5) الحظر الصارم لإرسال الرسائل النصية التسويقية في الإمارات بين الساعة `9:00 مساءً و7:00 صباحاً`، مع إلزامية بادئة `AD-` لاسم المرسل والموافقة المسبقة؛ لذا فإن تشغيل رسائل السلات المتروكة الآلية ليلاً دون قفل زمني يوقع المنشأة في مخالفة فورية!

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever configuring SMS marketing broadcasts or automated behavioral triggers (abandoned cart, win-back, flash sale) targeting UAE mobile numbers (`+971 5...`).
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إعداد أي حملة رسائل نصية (`SMS`) أو رسائل آلية (مثل تذكير السلة المتروكة) تستهدف أرقام الهواتف الإماراتية (`+971`).
- **When NOT to Use It (EN)**: Never allow an automated `'Wait 1 Hour -> Send Abandoned Cart SMS'` workflow to fire at `10:15 PM` Dubai time when a shopper abandons their cart at `9:15 PM`—queue it until `7:15 AM` (or `9:00 AM`) the next morning!
- **متى لا تستخدم هذه الأداة (AR)**: لا تسمح أبداً لتدفق آلي («انتظر ساعة واحدة ثم أرسل SMS للسلة المتروكة») بالإرسال في الساعة `10:15 مساءً` بتوقيت دبي؛ بل اضبط النظام لتأجيل الإرسال تلقائياً إلى الصباح التالي بعد الساعة `7:00 صباحاً`!

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. SMS Gateway Configuration (`Etisalat by e& / du` registered `AD-BrandName` Sender ID via Unifonic, Twilio, Infobip, or CEQUENS)
2. Automation Workflow Quiet-Hours / Send-Window settings locked to `Asia/Dubai (UTC+4)`
3. Verified Opt-In Consent & Master DND Suppression List (`AMP-232`, `AMP-233`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **UAE TDRA Unsolicited Electronic Communications Regulatory Policy v1.1 & e&/du SMPP Filtering** | `supported` | [Official Reference](https://kaeloglobal.com/digital-marketing/uae-data-protection-marketing/) (`2026-10-25`) | Kaelo Global Oct 2026 review confirms TDRA's 9:00 PM – 7:00 AM marketing SMS curfew (s. 8.8), `AD-` prefix mandate, prior consent requirement (s. 8.3), and ban on re-prompting unsubscribed users (s. 9.2.5). | Enforce `get_tdra_safe_send_timestamp()` at the SMS gateway wrapper level so no upstream tool can accidentally fire a promotional SMS to `+971` during curfew hours. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-452`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Hardcoding a 21:00–07:00 GST quiet-hours queue hold, `AD-` sender ID check, and free opt-out footer on all UAE SMS workflows.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-462`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Hardcoding a 21:00–07:00 GST quiet-hours queue hold, `AD-` sender ID check, and free opt-out footer on all UAE SMS workflows.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-472`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Hardcoding a 21:00–07:00 GST quiet-hours queue hold, `AD-` sender ID check, and free opt-out footer on all UAE SMS workflows.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-482`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Hardcoding a 21:00–07:00 GST quiet-hours queue hold, `AD-` sender ID check, and free opt-out footer on all UAE SMS workflows.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-492`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Hardcoding a 21:00–07:00 GST quiet-hours queue hold, `AD-` sender ID check, and free opt-out footer on all UAE SMS workflows.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-542`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-452 (Marketing Automation)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Brand**: Dubai & Riyadh D2C Fashion Brand running Klaviyo / Braze SMS automations.
- **Violations Detected**:
  1. The `'1-Hour Abandoned Cart SMS'` fired at `11:40 PM` Dubai time whenever late-night shoppers abandoned carts at `10:40 PM`.
  2. Marketing team sent a flash-sale blast over the transactional `BrandOTP` sender ID (missing the `AD-` prefix) to avoid promotional filtering.
- **Human Review & Key Edits Applied**: 1. **Added 30-Minute Carrier Buffer (`20:30` Cutoff Instead of `20:59`)**: Because bulk SMS batches of 50,000 messages can take 15–25 minutes to drain through telecom SMPP queues, stopped initiating UAE promotional batches after **`8:30 PM` Dubai time** so no trailing message ever lands on a phone at `9:02 PM`!
2. **Extended Similar Respectful Quiet Hours to KSA (`CST`) & Egypt (`NTRA`)**: Applied evening quiet hours (`9:30 PM – 8:30 AM` local time) across KSA and Egypt promotional SMS as well.
- **Final Usable Output**: - `100%` of UAE promotional SMS traffic locked to `AD-` Sender ID within the `08:30 AM – 08:30 PM` (`Asia/Dubai`) safe window, with zero night-curfew violations.
- **What Can Go Wrong**: An international marketing team in London (`UTC+0`) schedules a UAE SMS broadcast for `'6:00 PM London Time'`, forgetting that Dubai (`UTC+4`) is 4 hours ahead—delivering the promotional SMS to 40,000 Emirati phones at **`10:00 PM` Dubai time** (1 hour into the TDRA illegal curfew window!).
- **Correction & Fallback**: Always configure SMS campaign schedulers to use **`Recipient Local Timezone (Asia/Dubai UTC+4)`**, NEVER the marketer's browser/headquarters timezone!

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero promotional SMS dispatches to `+971` numbers between `21:00 and 07:00 Asia/Dubai`, `100%` `AD-` Sender ID compliance, and Zero carrier Sender-ID blocks.
- **Baseline Definition**: Audit of last 30 days of SMS gateway delivery timestamps in `Asia/Dubai` time.
- **Observation Window**: Monitored continuously in SMS gateway logs. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Curfew and `AD-` compliance prevent telecom blacklisting and TDRA fines, while offer relevance drives SMS click conversion.
