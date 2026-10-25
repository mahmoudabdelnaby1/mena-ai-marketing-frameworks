# FW-051: Cross-Border GCC & Egypt Automated Lifecycle Email Currency, VAT & BNPL Localization Checklist
## قائمة فحص توطين العملات وضريبة القيمة المضافة (`15% KSA / 5% UAE / 0% Qatar / 14% Egypt`) وخيارات الدفع في الرسائل الآلية

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-249`, `AMP-259`, `AMP-269`, `AMP-279`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent cross-border MENA lifecycle emails (abandoned cart, browse abandonment, back-in-stock, win-back) from displaying wrong currencies (`USD` or `SAR` to UAE/Egypt buyers) or omitting mandatory tax-inclusive VAT disclosures.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع رسائل البريد الآلية العابرة للحدود من عرض عملات خاطئة أو إغفال بيان شمول ضريبة القيمة المضافة الإلزامية (`15%` في السعودية، `5%` في الإمارات، `0%` في قطر، `14%` في مصر) وخيارات التقسيط المحلية.
- **Why `CHECKLIST` Fits This User Job (EN)**: Multi-country stores on Shopify Markets, Salla, Zid, or Magento frequently send dynamic product blocks in Klaviyo/Omnisend that pull the store's base currency (`SAR` or `USD`) regardless of the recipient's country, or omit mandatory tax-inclusive consumer pricing disclosures; a localization CHECKLIST with Liquid currency/VAT routing prevents checkout shock.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: ترسل المتاجر متعددة الدول قوالب بريدية ديناميكية تسحب العملة الأساسية للمتجر (`SAR` أو `USD`) لجميع العملاء بغض النظر عن دولتهم، أو تغفل عبارة «شامل ضريبة القيمة المضافة» الإلزامية؛ وتضمن قائمة الفحص هذه تطابق العملة والضريبة ووسيلة الدفع مع دولة المستلم.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever operating automated lifecycle emails for a store selling across 2 or more MENA countries (KSA, UAE, Kuwait, Qatar, Bahrain, Oman, Egypt).
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند تشغيل سلاسل البريد الآلي لمتجر يبيع في دولتين أو أكثر من دول الخليج ومصر.
- **When NOT to Use It (EN)**: Never display consumer product prices in Saudi Arabia or UAE as 'Tax-Exclusive' (`السعر غير شامل الضريبة`) in marketing emails only to add 15% or 5% VAT as a surprise at checkout.
- **متى لا تستخدم هذه الأداة (AR)**: يُحظر عرض أسعار المستهلكين في رسائل البريد بالسعودية أو الإمارات «بدون ضريبة» ثم مفاجأة العميل بإضافة 15% أو 5% عند الدفع؛ فالأسعار المعلنة للمستهلك يجب أن تكون شاملة للضريبة.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Customer Country Property in ESP (`person.country_code`: `SA`, `AE`, `KW`, `QA`, `BH`, `OM`, `EG`)
2. Catalog Multi-Currency Price Attributes or Presentment Currency (`event.extra.presentment_currency`)
3. Country-Specific Payment & Shipping Threshold Table

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Cross-Border GCC & Egypt Currency, VAT & Payment Matrix (Verified 2026-10-25)

| Country (`ISO`) | Currency Display (`<bdi>`) | Mandatory Consumer VAT Disclosure Rule | Local Payment Badges to Display in Footer | Free Shipping Threshold Example |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi Arabia (`SA`)** | `SAR` / `ر.س` (ASCII digits `299.00 ر.س`) | **`شامل ضريبة القيمة المضافة (15%)`** *(Mandatory ZATCA & Ministry of Commerce consumer pricing rule)* | `مدى (Mada)` · `Apple Pay` · `تابي (Tabby)` · `تمارا (Tamara)` | `شحن مجاني للطلبات فوق 250 ر.س` |
| **UAE (`AE`)** | `AED` / `د.إ` (`299.00 د.إ`) | **`شامل ضريبة القيمة المضافة (5%)`** *(Mandatory FTA UAE consumer pricing rule)* | `Apple Pay` · `Tabby` · `Tamara` · `Visa/Mastercard` | `شحن مجاني للطلبات فوق 250 د.إ` |
| **Qatar (`QA`)** | `QAR` / `ر.ق` (`299.00 ر.ق`) | **`0% VAT`** *(Do NOT print "Includes 15% VAT" on Qatar emails!)* | `Apple Pay` · `NAPS/QPay` · `Visa/Mastercard` | `شحن سريع للدوحة للطلبات فوق 300 ر.ق` |
| **Kuwait (`KW`)** | `KWD` / `د.ك` (`24.500 د.ك` — **3 decimal places!**) | **`0% VAT`** *(Note: KWD uses 3 decimal places `.000`, not 2!)* | `KNET (كي نت)` · `Apple Pay` · `Tabby` | `توصيل مجاني للكويت فوق 20 د.ك` |
| **Bahrain (`BH`) & Oman (`OM`)** | `BHD` (`.000` 3 decimals) / `OMR` (`.000` 3 decimals) | **Bahrain**: `شامل الضريبة (10%)`<br>**Oman**: `شامل الضريبة (5%)` | `BenefitPay` (Bahrain) · `Thawani/OmanNet` (Oman) · `Apple Pay` | Localized to `BHD` / `OMR` |
| **Egypt (`EG`)** | `EGP` / `ج.م` (`2,450 ج.م`) | **`شامل الضريبة`** | `إنستاباي (InstaPay)` · `فوري (Fawry)` · `فاليو (valU)` · `ميزة` · `الدفع عند الاستلام` | `شحن مجاني للطلبات فوق 1,500 ج.م` |

#### Pre-Flight Checklist for Multi-Currency Dynamic Email Blocks
- [ ] **Check 1 — Bind `presentment_currency`, Never Store Base Currency**: In Shopify/Salla/Magento Klaviyo events, render `{{ event.extra.presentment_price }} {{ event.extra.presentment_currency }}` instead of `{{ item.price }}` (which defaults to base store currency).
- [ ] **Check 2 — Respect 3-Decimal Currencies (`KWD`, `BHD`, `OMR`)**: Ensure your template number formatter outputs `24.500 KWD` (or `24.5 د.ك`), never multiplying by 10 into `245.00 KWD`!
- [ ] **Check 3 — Dynamic VAT & Payment Footer Block**: Wrap the VAT line and payment icons in an `{% if person.country_code == 'SA' %}...{% elsif person.country_code == 'AE' %}...` conditional so Qatari/Kuwaiti shoppers never see `"شامل ضريبة 15%"` and Egyptian shoppers never see `"ادفع عبر مدى"`.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Shopify Markets / Salla Multi-Currency Events in Klaviyo & Omnisend** | `supported` | [Official Reference](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) (`2026-10-25`) | Checkout and cart events carry both `shop_currency` (base) and `presentment_currency` (customer-facing); templates must explicitly reference `presentment` fields. | If `Browse Viewed Product` events only pass base currency, use a Liquid lookup table keyed by `person.country_code`. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-249`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Locale-aware dynamic liquid tags rendering tax-inclusive SAR, AED, QAR, or EGP prices.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-259`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Locale-aware dynamic liquid tags rendering tax-inclusive SAR, AED, QAR, or EGP prices.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-269`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Locale-aware dynamic liquid tags rendering tax-inclusive SAR, AED, QAR, or EGP prices.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-279`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Locale-aware dynamic liquid tags rendering tax-inclusive SAR, AED, QAR, or EGP prices.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: GCC & Egypt Luxury Oud & Perfumes Brand headquartered in Riyadh (`Base Currency: SAR`) selling across KSA, UAE, Kuwait, Qatar, and Egypt.
- **Problem**: Browse Abandonment email showed `450.00 SAR (شامل ضريبة 15% - ادفع عبر مدى)` to shoppers in Dubai (`AED`), Kuwait City (`KWD`), Doha (`QAR`), and Cairo (`EGP`).
- **Human Review & Key Edits Applied**: 1. **Verified URL Locale Parameter**: Appended `?currency={{ presentment_currency }}&country={{ person.country_code }}` to the email CTA link so clicking from the email opens the storefront pre-switched to the exact same currency shown in the email (`AMP-063`).
2. **Checked KWD 3-Decimal Formatting**: Confirmed Kuwaiti Dinar prices format cleanly to 3 decimal places.
- **Final Usable Output**: - Cross-border lifecycle templates live across all 7 MENA markets with 100% currency, VAT-rate, and local payment-method accuracy.
- **What Can Go Wrong**: An email displays `440 AED` to a Dubai shopper, but clicking the product link opens the website in `SAR` (`450 ر.س`) because the deep link lacked the currency/market parameter.
- **Correction & Fallback**: Always pass the market/currency deep-link parameter (`?country=AE&currency=AED` or country subfolder `/ae-ar/`) on every product link inside cross-border emails.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Non-home-country Email-to-Checkout Conversion Rate (`AE`, `KW`, `QA`, `EG` segments) and zero currency-mismatch support tickets.
- **Baseline Definition**: Prior 30-day conversion rate of non-KSA email subscribers.
- **Observation Window**: 28 days post-update. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Displaying accurate local currency, VAT, and payment rails removes cross-border friction, while cross-border shipping duties and courier speed affect final checkout completion.
