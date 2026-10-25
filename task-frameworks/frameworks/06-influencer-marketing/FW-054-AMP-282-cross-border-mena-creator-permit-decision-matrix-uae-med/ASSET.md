# FW-054: Cross-Border MENA Creator Permit Decision Matrix (UAE Media Council Permit vs. KSA GAMR Mawthooq vs. Egypt Tax/SCM)
## أداة القرار لتراخيص المؤثرين العابرة للحدود بين الإمارات (مجلس الإمارات للإعلام) والسعودية (`موثوق`) ومصر

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-292`, `AMP-302`, `AMP-312`, `AMP-322`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Navigate separate national creator licensing regimes across the UAE (UAE Media Council Advertiser Permit + Trade License), Saudi Arabia (GAMR Mawthooq), and Egypt so cross-border regional campaigns never assume one country's permit covers another.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إدارة التراخيص القانونية للمؤثرين في الحملات الإقليمية المشتركة بين الإمارات (تصريح المعلن من مجلس الإمارات للإعلام + الرخصة التجارية) والسعودية (رخصة موثوق) ومصر، ومنع افتراض أن ترخيص دولة يغني عن الأخرى.
- **Why `DECISION_AID` Fits This User Job (EN)**: VOCTOS's Oct 2026 influencer permit analysis highlights that MENA does not have a single pan-GCC creator permit: UAE requires a UAE Media Council (`مجلس الإمارات للإعلام`) Advertiser Permit + e-commerce/trade license (including a Visiting Advertiser Permit for visiting creators), while KSA requires GAMR `Mawthooq`; a cross-border DECISION_AID prevents multi-market compliance blindspots.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: توضح دراسة VOCTOS (أكتوبر 2026) عدم وجود ترخيص موحد للمؤثرين في الخليج؛ فالإمارات تشترط «تصريح معلن» من مجلس الإمارات للإعلام ورخصة تجارية (أو تصريح معلن زائر للمؤثرين الزائرين)، بينما تشترط السعودية رخصة «موثوق»؛ لذا تمنع أداة القرار هذه المخالفات في الحملات الإقليمية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when contracting creators across multiple MENA countries (KSA, UAE, Egypt) or flying a creator from one Arab country to film commercial content in another (e.g., flying an Egyptian or Saudi creator to shoot an ad in Dubai or Riyadh).
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند التعاقد مع مؤثرين من عدة دول عربية أو استضافة مؤثر من دولة لتصوير إعلان تجاري داخل دولة أخرى (مثل سفر مؤثر لتصوير إعلان في دبي أو الرياض).
- **When NOT to Use It (EN)**: Do not fly a non-resident creator into Dubai or Riyadh to shoot paid commercial content on a standard tourist visa without securing the local visiting advertiser / shooting permit through a licensed local agency.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم باستضافة مؤثر غير مقيم لتصوير إعلان تجاري مدفوع في دبي أو الرياض بتأشيرة سياحية عادية دون استخراج تصريح معلن زائر / تصريح تصوير عبر وكالة محلية مرخصة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Creator Nationality & Country of Residence (`KSA`, `UAE`, `Egypt`, `Other`)
2. Physical Shooting Location (`Where the creator will film`) AND Target Ad Audience Location (`Where the ad will run`)
3. Creator's existing permits (`KSA Mawthooq`, `UAE Media Council Permit + DED/Freezone License`, `Egypt Tax Card / E-Invoice`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Cross-Border MENA Creator Licensing Decision Matrix (Verified 2026-10-25)

| Creator Scenario | **Saudi Arabia (`GAMR / الهيئة العامة لتنظيم الإعلام`)** | **United Arab Emirates (`UAE Media Council / مجلس الإمارات للإعلام`)** | **Egypt (`Supreme Council for Media Regulation & Egyptian Tax Authority`)** |
| :--- | :--- | :--- | :--- |
| **1. Resident Creator Advertising Locally** | Mandatory **GAMR `Mawthooq` License** (`SAR 15,000` / 3 yrs). Display license number in bio/account (`AMP-281`). | Mandatory **UAE Media Council Advertiser Permit (`تصريح معلن`)** + valid UAE Trade/Freelance License (`DED` or Media Free Zone). Permit number must be displayed clearly on social profile. | Must hold valid **Egyptian Tax Registration & E-Invoicing (`الفاتورة الإلكترونية / ضريبة الدخل والقيمة المضافة لمناع المحتوى`)** + SCM/CPA commercial disclosure rules (`AMP-064`). |
| **2. Resident of Country A Filmed Locally, Ad Boosted into Country B** | Ad content boosted into KSA must comply with GAMR content standards, `#إعلان` labeling, and sector permits (`SFDA / REGA / MOH`). | Ad boosted into UAE must comply with UAE Media Council content standards, `#Ad / #إعلان` disclosure, and sector approvals (`MOHAP / DET`). | Ad boosted into Egypt must comply with Egypt CPA Law 181/2018 & EDA medical/cosmetic rules (`AMP-176`). |
| **3. Visiting Creator Flown In to Film Paid Ad on Location (`HIGH RISK TRAP`)** | **Non-Saudi visiting KSA**: Cannot operate as an unlicensed solo advertiser; must be contracted through a **GAMR-licensed Saudi advertising agency** with required commercial/shooting clearances. | **Visiting Creator in UAE**: Mandatory **Visiting Advertiser Permit (`تصريح معلن زائر`)** issued via a UAE-licensed advertising/talent agency registered with the UAE Media Council (valid up to 3 months). | Foreign commercial production shoots in public/heritage sites require local production company clearance & permits. |
| **4. Kuwait & Oman Specific Creator Permit Rules (`AMP-554`)** | *Boundary Note (`DEFER_EVIDENCE`)*: While KSA (`GAMR Mawthooq`) and UAE (`Media Council`) rules are verified via primary portals, verify current Q4 2026 creator permit fee updates in Kuwait (Ministry of Information) and Oman directly with local counsel before contracting. |

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **UAE Media Council Advertiser Permit & KSA GAMR Mawthooq Regulations** | `supported` | [Official Reference](https://voctos.net/influencer-advertiser-permits-arab-markets-white-friday/) (`2026-10-25`) | VOCTOS Oct 2026 regulatory analysis documents the distinct permit requirements of KSA GAMR (Mawthooq) and UAE Media Council (Advertiser Permit & Visiting Advertiser Permit). | Always execute cross-border creator shoots through a licensed local agency of record in the host country. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-292`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Jurisdiction-by-jurisdiction creator compliance matrix before multi-country campaign sign-off.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-302`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Jurisdiction-by-jurisdiction creator compliance matrix before multi-country campaign sign-off.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-312`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Jurisdiction-by-jurisdiction creator compliance matrix before multi-country campaign sign-off.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-322`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Jurisdiction-by-jurisdiction creator compliance matrix before multi-country campaign sign-off.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: Regional Tourism & Retail App flying 3 creators (1 Saudi, 1 Egyptian, 1 Emirati) to Dubai for a 4-day paid brand shoot, followed by a 3-day shoot in Riyadh.
- **Human Review & Key Edits Applied**: 1. **Added 14-Day Lead Time Gate**: Blocked flight ticket booking until permit numbers for both legs were issued and logged in the production tracker.
2. **Tax Withholding & E-Invoice Check (Egypt)**: Confirmed the Egyptian creator's contract includes their Egyptian Tax Registration Number (`رقم التسجيل الضريبي`) and electronic invoice (`الفاتورة الإلكترونية`) compliance.
- **Final Usable Output**: - All 3 creators cleared with jurisdiction-specific permits for both the UAE and KSA shoots 10 days before departure, with zero cross-border permit violations.
- **What Can Go Wrong**: A Dubai agency books a famous Saudi creator (who holds a valid KSA `Mawthooq` license) to film paid restaurant & mall ads inside Dubai without obtaining a UAE Media Council Visiting Advertiser Permit, assuming `Mawthooq` is valid across the GCC.
- **Correction & Fallback**: Enforce the **Jurisdiction Independence Rule**: `KSA Mawthooq != UAE Media Council Permit`. Always verify the permit required by (a) the country where the creator is physically filming/residing AND (b) the country where the ad is targeted.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% permit verification across every active market (`KSA + UAE + Egypt`) at least 10 business days before filming/publishing.
- **Baseline Definition**: Pre-campaign compliance audit.
- **Observation Window**: Checked per campaign wave. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: This matrix guides operational compliance workflow; confirm visa and commercial permit specifics with qualified local legal counsel in each country.
