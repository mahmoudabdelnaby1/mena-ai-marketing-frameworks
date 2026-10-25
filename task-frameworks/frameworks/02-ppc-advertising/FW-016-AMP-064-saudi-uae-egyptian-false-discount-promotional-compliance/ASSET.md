# FW-016: Saudi, UAE & Egyptian False-Discount & Promotional Compliance Checklist
## قائمة فحص الامتثال لقوانين التخفيضات والعروض الترويجية في السعودية والإمارات ومصر (منع غرامات التخفيضات الوهمية)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-074`, `AMP-084`, `AMP-094`, `AMP-104`, `AMP-114`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Audit AI-generated promotional ad copy and strike-through prices against Saudi Ministry of Commerce, UAE Federal Consumer Protection, and Egyptian CPA Law 181/2018 rules before launching sales.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تدقيق نصوص الإعلانات الترويجية والأسعار المشطوبة المولدة بالذكاء الاصطناعي وفق أنظمة وزارة التجارة السعودية وقانون حماية المستهلك الإماراتي والمصري (قانون 181/2018) قبل الإطلاق.
- **Why `CHECKLIST` Fits This User Job (EN)**: AI ad generators routinely invent fake strike-through discounts (`'خصم 80% اليوم فقط!'`) without verifying permits or prior baseline prices—exposing merchants to fines up to SAR 1,000,000 in KSA, EGP 2,000,000 in Egypt, and AED 2,000,000 in UAE; a pre-launch CHECKLIST stops illegal claims before publication.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تختلق أدوات الذكاء الاصطناعي نسب خصم وهمية («خصم 80% اليوم فقط!») دون التحقق من ترخيص التخفيضات أو السعر الحقيقي السابق، مما يعرض المتجر لغرامات تصل إلى مليون ريال في السعودية و2 مليون جنيه في مصر و2 مليون درهم في الإمارات؛ وتمنع قائمة الفحص هذه النشر غير النظامي.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before publishing any discount, clearance, bundle, or White Friday / Ramadan promotional campaign in Saudi Arabia, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل نشر أي إعلان يتضمن نسبة خصم أو تصفية أو عرضاً ترويجياً في السعودية أو الإمارات أو مصر.
- **When NOT to Use It (EN)**: Do not treat this operational checklist as formal legal representation—verify permit classifications with your Ministry of Commerce / CPA portal account.
- **متى لا تستخدم هذه الأداة (AR)**: لا تُغني قائمة الفحص التشغيلية عن مراجعة البوابة الرسمية لوزارة التجارة أو جهاز حماية المستهلك لإصدار التراخيص السارية.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. SKU 30-day Historical Price Ledger (lowest actual selling price prior to the promotion)
2. Electronic Discount License Number (ترخيص التخفيضات الإلكتروني من وزارة التجارة السعودية / التصريح المحلي)
3. Draft AI Promotional Copy (Headlines, Banners, Social Captions, Terms)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi Ministry of Commerce Discount Permit & Egypt CPA Law 181/2018** | `supported` | [Official Reference](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) (`2026-10-25`) | VOCTOS Oct 2026 legal review documents KSA fines up to SAR 1M and Egypt Law 181/2018 fines up to EGP 2M for fictitious baseline prices and unlicensed discount claims. | Verify current permit requirements with qualified local counsel or the official Ministry of Commerce (`mc.gov.sa`) / CPA (`cpa.gov.eg`) portal. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-074`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Documented promotions backed by a 30-day ERP price history ledger and active municipal/ministry discount license.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-084`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Documented promotions backed by a 30-day ERP price history ledger and active municipal/ministry discount license.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-094`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Documented promotions backed by a 30-day ERP price history ledger and active municipal/ministry discount license.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-104`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Documented promotions backed by a 30-day ERP price history ledger and active municipal/ministry discount license.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-114`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Documented promotions backed by a 30-day ERP price history ledger and active municipal/ministry discount license.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: Riyadh & Cairo Electronics Store White Friday Meta + Google Ad Copy.
- **Draft AI Copy**: `"🔥 جنون الجمعة البيضاء! خصم 75% على كل الموقع لمدة ساعتين فقط! السعر قبل: 2000 ريال — الآن: 499 ريال فقط! الكمية على وشك النفاد!"`
- **Actual Store Ledger**: The item sold for `599 SAR` all of October (never `2,000 SAR`), store-wide discounts range from `10% to 30%`, and the Saudi Ministry of Commerce discount permit number was omitted.
- **Human Review & Key Edits Applied**: 1. **Corrected Price Maths**: Set `السعر السابق: 599 ر.س` and `السعر بعد الخصم: 499 ر.س (شامل الضريبة)` (an honest `16.7%` saving).
2. **Added Permit & Window**: Added `"مثال افتراضي: [مرجع التصريح الذي يقدمه العميل] — تُراجع فترة العرض كما تظهر في المصدر الرسمي الحالي"`.
- **Final Usable Output**: - **Compliant KSA Ad Copy**:
  `"عروض الجمعة البيضاء المعتمدة! خصومات من 10% حتى 30% على الأجهزة المختارة. السعر قبل الخصم: 599 ر.س | السعر الآن: 499 ر.س (شامل الضريبة). متاح التقسيط عبر تابي وتمارا. مرجع التصريح: [رقم مطابق للوثيقة الرسمية]، وفترة العرض: [حسب التصريح]."`
- **What Can Go Wrong**: An automated Shopify/Salla AI compare-at-price script bulk-multiplies all current prices by `1.5x` and pastes that figure into the `Compare-at Price` (`السعر قبل الخصم`) field the night before White Friday.
- **Correction & Fallback**: Lock `Compare-at Price` to the immutable 30-day historical price snapshot stored in your ERP/warehouse log, and disable any plugin that calculates `Compare-at Price` as a formula of `Current_Price * 1.X`.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% SKU pass rate on 30-day baseline price audit and zero regulatory complaints or ad account policy flags.
- **Baseline Definition**: Pre-launch audit of all `Compare-at Price` fields in the product catalog.
- **Observation Window**: Checked 48 hours prior to every promotional campaign. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: This checklist enforces operational truthfulness and statutory hygiene; consult qualified local legal counsel for complex cross-border prize draws or sweepstakes.
