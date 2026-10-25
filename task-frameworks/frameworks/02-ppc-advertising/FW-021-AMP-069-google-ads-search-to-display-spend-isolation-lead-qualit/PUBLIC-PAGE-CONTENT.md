# Google Ads Search Campaign Channel Allocation & Lead Quality Review
## <span dir="rtl">مراجعة توزيع القنوات وجودة العملاء المحتملين في حملات البحث على Google Ads</span>

> **Asset ID**: `FW-021` (`AMP-069`) | **Artifact Type**: `DECISION_AID` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Review Search campaign channel settings, allocation controls, and lead-quality signals as Google rolls out channel-prioritization changes.
- **AR**: <span dir="rtl">مراجعة توزيع القنوات وجودة العملاء المحتملين باستخدام إعدادات الحساب الحالية وبيانات العملاء المؤهلين، مع إعادة التحقق من التغييرات التي تطرحها Google تدريجياً.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when auditing or launching Google Search campaigns in KSA, UAE, or Egypt—especially for lead generation (real estate, clinics, B2B, education, automotive).
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تدقيق أو إطلاق حملات بحث جوجل (`Google Search`) في السعودية أو الإمارات أو مصر، خاصة في قطاعات توليد العملاء المحتملين (العقارات، العيادات، الشركات B2B، التعليم).</span>
- **When NOT to Use It (EN)**: Review network and channel settings against the campaign objective, current account controls, and qualified outcome data; avoid universal setting rules.
- **متى لا تستخدمها (AR)**: <span dir="rtl">راجع إعدادات الشبكة والقنوات وفق هدف الحملة والخيارات المتاحة وبيانات النتائج المؤهلة، وتجنب القواعد العامة.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Google Ads Campaign Settings -> `Networks` (`الشبكات`) status across all active Search campaigns
- Search Campaign Spend Breakdown by Network (`Search` vs. `Search Partners` vs. `Display Expansion`)
- Primary Conversion Action configuration (`Page View / Raw Form Submit` vs. `Qualified Lead / CRM SQL`)

## 2. The Working `DECISION_AID` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Search-to-Display Spend Protection Decision Aid

#### 1. Network Isolation Decision Tree
1. **Check `Campaign Settings -> Networks -> Display Network`**:
   - **IF `Include Google Display Network` is checked**:
     - Review current channel priorities, budget allocation controls, conversion definitions, and lead-quality evidence. Choose settings based on the campaign goal and observed outcomes; do not apply a universal setting.
2. **Check `Campaign Settings -> Networks -> Google Search Partners`**:
   - Segment your campaign report by **`Network (with search partners)`** over the last 30 days:
   - **IF Search Partners CPA on *CRM-Qualified Leads* is `> 1.3x` Google Search CPA** (or if you only track raw front-end form submits without CRM feedback):
     - Review whether Search Partners fit the campaign objective and qualified-lead evidence; change the setting only after account-level review.
3. **Upgrade the Primary Conversion Signal (So Automated Bidding Cannot Game Display/Partner Clicks)**:
   - Replace raw front-end `Thank You Page View` or unverified `WhatsApp Button Click` (`AMP-126`) as the Primary Conversion Action with **OTP-Verified Lead** or **Offline CRM Qualified Lead (`MQL/SQL`)** via Enhanced Conversions for Leads (`AMP-446`).

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Advertiser**: Dubai & Riyadh Luxury Off-Plan Real Estate Brokerage (`$15,000/month` Google Search budget).
- **Problem**: Campaign had `Include Google Display Network` enabled under `Maximize Conversions`. After adding a simple 2-field lead form, Display Expansion consumed `44%` of the Search budget (`$6,600`), generating `310` spam/accidental mobile-game leads (`0` actual property buyers).

### Step B: Initial Output (`المخرج الأولي`)
- **Audit & Action Plan**:
  1. Unchecked `Include Google Display Network` and `Include Google Search Partners` across all 6 Arabic and English Search campaigns.
  2. Demoted raw `Form_Submit` to `Secondary (Observation Only)` and promoted `CRM_Verified_Phone_Qualified_Lead` (via HubSpot/GCLID offline import) to `Primary Conversion Action`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added Negative Placement Exclusion**: Added mobile app category exclusions at the Account level (`Content Suitability -> Excluded placements -> All Mobile Apps`) as a second firewall for PMax campaigns.
2. **Phone Input Validation**: Added Saudi/UAE mobile OTP verification (`+966 5...` / `+971 5...` normalized per `AMP-388`) before firing the primary lead event.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Document the selected channel settings and compare subsequent qualified outcomes with the prior baseline; this illustrative example does not establish a guaranteed allocation or result.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A practitioner accepts Google Ads' inline 'Recommendations (`التوصيات`)' auto-apply suggestion `'Add Display Expansion to get more conversions at a similar CPA'`, which silently re-enables Display Network on Search campaigns.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Open `Recommendations -> Auto-apply` in Google Ads and **uncheck all automatic network/expansion recommendations** so Display Expansion can never be turned back on automatically.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Google Ads channel settings and staged channel-prioritization changes** | `supported` | [Official Docs](https://support.google.com/google-ads/faq/10286469?hl=en) (`2026-10-25`) | Google Ads documents the channel-prioritization rollout and the February 2027 Display Expansion migration. Check the current account interface and set channel priorities and any best-effort budget allocations according to campaign objectives; these controls do not guarantee a fixed allocation. | Review current network and channel settings in the account. Choose priorities and allocation based on campaign goals and observed qualified outcomes; confirm changes with the account owner. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Share of Search campaign spend on `Google Search` (`Target: 100%`) and Cost per CRM-Qualified Lead (`Cost / SQL`).
- **Baseline**: Prior 30-day spend split (`Google Search` vs. `Display Expansion` / `Search Partners`) and lead-to-SQL qualification rate.
- **Observation Window**: 14–28 days post-change.
- **Interpretation Boundary**: Eliminating Display Expansion stops low-intent spend leakage; total raw lead count may drop while qualified sales pipeline rate increases.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Google Ads Channel Priority, Lead Scoring and a February 2027 Display Change: A Checklist for Arab Advertisers](https://support.google.com/google-ads/faq/10286469?hl=en) — *VOCTOS* (Published `2026-10-16`, Accessed `2026-10-25`): Documents Google Ads Oct 2026 channel priority changes, offline lead-scoring requirements, and the Feb 2027 removal of current Display spend allocation controls on Search campaigns.
