# Saudi, UAE & Egyptian False-Discount & Promotional Compliance Checklist
## <span dir="rtl">قائمة فحص الامتثال لقوانين التخفيضات والعروض الترويجية في السعودية والإمارات ومصر (منع غرامات التخفيضات الوهمية)</span>

> **Asset ID**: `FW-016` (`AMP-064`) | **Artifact Type**: `CHECKLIST` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Audit AI-generated promotional ad copy and strike-through prices against Saudi Ministry of Commerce, UAE Federal Consumer Protection, and Egyptian CPA Law 181/2018 rules before launching sales.
- **AR**: <span dir="rtl">تدقيق نصوص الإعلانات الترويجية والأسعار المشطوبة المولدة بالذكاء الاصطناعي وفق أنظمة وزارة التجارة السعودية وقانون حماية المستهلك الإماراتي والمصري (قانون 181/2018) قبل الإطلاق.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before publishing any discount, clearance, bundle, or White Friday / Ramadan promotional campaign in Saudi Arabia, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل نشر أي إعلان يتضمن نسبة خصم أو تصفية أو عرضاً ترويجياً في السعودية أو الإمارات أو مصر.</span>
- **When NOT to Use It (EN)**: Do not treat this operational checklist as formal legal representation—verify permit classifications with your Ministry of Commerce / CPA portal account.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تُغني قائمة الفحص التشغيلية عن مراجعة البوابة الرسمية لوزارة التجارة أو جهاز حماية المستهلك لإصدار التراخيص السارية.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- SKU 30-day Historical Price Ledger (lowest actual selling price prior to the promotion)
- Electronic Discount License Number (ترخيص التخفيضات الإلكتروني من وزارة التجارة السعودية / التصريح المحلي)
- Draft AI Promotional Copy (Headlines, Banners, Social Captions, Terms)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Statutory Promotional & Discount Compliance Checklist (KSA, UAE & Egypt)

#### 1. Jurisdictional Statutory Requirements Matrix (Verified 2026-10-25)
| Jurisdiction | Governing Authority & Law | Mandatory Pre-Launch Requirements | Statutory Penalty Ceiling |
| :--- | :--- | :--- | :--- |
| **Saudi Arabia (KSA)** | Ministry of Commerce (E-Commerce Law & Promotional Regulations) | 1. Valid electronic **Discount License (`ترخيص التخفيضات`)** displayed clearly on the store.<br>2. Visible **Before Price** and **After Price** (`السعر قبل وبعد التخفيض`) in SAR (incl. 15% VAT).<br>3. Strict ban on raising the baseline price before a sale to fake a larger `%` discount. | Up to **SAR 1,000,000**, store blocking, and public naming (`التشهير`). |
| **Egypt** | Consumer Protection Agency (`CPA` — Law No. 181 of 2018, Art. 9, 15, 66) | 1. Must state the **actual previous selling price** from the preceding month alongside the discounted price in EGP.<br>2. Supply license number where applicable (`رقم ترخيص الأوكازيون`).<br>3. Ban on deceptive "Up to 90% Off" headlines if no meaningful inventory is discounted at that tier. | Fines from **EGP 50,000 up to EGP 2,000,000** (doubled for repeat offenses). |
| **United Arab Emirates (UAE)** | Ministry of Economy / DED (Federal Law No. 15 of 2020 & Executive Regulations) | 1. Promotional permit from local DED (e.g., Dubai DET) where required.<br>2. Genuine prior price baseline and explicit start/end dates in AED (incl. 5% VAT). | Fines up to **AED 2,000,000** and license suspension. |

#### 2. Pre-Launch AI Ad Copy & Price Gate Checklist
- [ ] **Check 1 — Baseline Price Integrity (`No Pre-Sale Price Inflation`)**: Confirm that for every discounted SKU, `Before_Price <= Lowest_Actual_Selling_Price_In_Last_30_Days`.
- [ ] **Check 2 — Replace Unverified `'Up to X%'` AI Hyperbole**: If the LLM writes `"خصم يصل إلى 70% على جميع المنتجات"`, replace with the exact verified range and attach the qualifying SKU count (e.g., `"خصم من 15% إلى 40% على مختارات القهوة المختصة — ترخيص وزارة التجارة رقم [XXXX]"`).
- [ ] **Check 3 — Fake Urgency / Fake Stock Countdown Ban**: Remove AI-generated fake scarcity scripts (`"باقي قطعتين فقط!"` when stock is `500` units, or resetting 15-minute countdown timers).
- [ ] **Check 4 — Clear Return/Exchange Policy Disclosure**: Confirm the landing page states the statutory return window (7 days in KSA E-Commerce Law / 14 days in Egypt CPA Law 181/2018 for non-exempt items).

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Campaign**: Riyadh & Cairo Electronics Store White Friday Meta + Google Ad Copy.
- **Draft AI Copy**: `"🔥 جنون الجمعة البيضاء! خصم 75% على كل الموقع لمدة ساعتين فقط! السعر قبل: 2000 ريال — الآن: 499 ريال فقط! الكمية على وشك النفاد!"`
- **Actual Store Ledger**: The item sold for `599 SAR` all of October (never `2,000 SAR`), store-wide discounts range from `10% to 30%`, and the Saudi Ministry of Commerce discount permit number was omitted.

### Step B: Initial Output (`المخرج الأولي`)
- **Audit Verdict**: **`BLOCKED — CRITICAL STATUTORY VIOLATION (KSA & EGYPT)`**
  1. Fake baseline price (`2,000 SAR` vs actual 30-day price `599 SAR`) violates Saudi E-Commerce Law and Egypt Law 181/2018 (`غرامة تصل لمليون ريال / 2 مليون جنيه`).
  2. False `"75% على كل الموقع"` claim when actual range is `10%–30%`.
  3. Missing Saudi Ministry of Commerce Discount License display.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Corrected Price Maths**: Set `السعر السابق: 599 ر.س` and `السعر بعد الخصم: 499 ر.س (شامل الضريبة)` (an honest `16.7%` saving).
2. **Added Permit & Window**: Added `"مثال افتراضي: [مرجع التصريح الذي يقدمه العميل] — تُراجع فترة العرض كما تظهر في المصدر الرسمي الحالي"`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- **Compliant KSA Ad Copy**:
  `"عروض الجمعة البيضاء المعتمدة! خصومات من 10% حتى 30% على الأجهزة المختارة. السعر قبل الخصم: 599 ر.س | السعر الآن: 499 ر.س (شامل الضريبة). متاح التقسيط عبر تابي وتمارا. مرجع التصريح: [رقم مطابق للوثيقة الرسمية]، وفترة العرض: [حسب التصريح]."`

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An automated Shopify/Salla AI compare-at-price script bulk-multiplies all current prices by `1.5x` and pastes that figure into the `Compare-at Price` (`السعر قبل الخصم`) field the night before White Friday.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Lock `Compare-at Price` to the immutable 30-day historical price snapshot stored in your ERP/warehouse log, and disable any plugin that calculates `Compare-at Price` as a formula of `Current_Price * 1.X`.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi Ministry of Commerce Discount Permit & Egypt CPA Law 181/2018** | `supported` | [Official Docs](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) (`2026-10-25`) | VOCTOS Oct 2026 legal review documents KSA fines up to SAR 1M and Egypt Law 181/2018 fines up to EGP 2M for fictitious baseline prices and unlicensed discount claims. | Verify current permit requirements with qualified local counsel or the official Ministry of Commerce (`mc.gov.sa`) / CPA (`cpa.gov.eg`) portal. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% SKU pass rate on 30-day baseline price audit and zero regulatory complaints or ad account policy flags.
- **Baseline**: Pre-launch audit of all `Compare-at Price` fields in the product catalog.
- **Observation Window**: Checked 48 hours prior to every promotional campaign.
- **Interpretation Boundary**: This checklist enforces operational truthfulness and statutory hygiene; consult qualified local legal counsel for complex cross-border prize draws or sweepstakes.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) — *VOCTOS* (Published `2026-10-22`, Accessed `2026-10-25`): Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000.
- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
