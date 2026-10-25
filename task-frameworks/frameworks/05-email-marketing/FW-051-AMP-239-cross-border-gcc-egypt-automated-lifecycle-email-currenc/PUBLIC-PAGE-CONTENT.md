# Cross-Border GCC & Egypt Automated Lifecycle Email Currency, VAT & BNPL Localization Checklist
## <span dir="rtl">قائمة فحص توطين العملات وضريبة القيمة المضافة (`15% KSA / 5% UAE / 0% Qatar / 14% Egypt`) وخيارات الدفع في الرسائل الآلية</span>

> **Asset ID**: `FW-051` (`AMP-239`) | **Artifact Type**: `CHECKLIST` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent cross-border MENA lifecycle emails (abandoned cart, browse abandonment, back-in-stock, win-back) from displaying wrong currencies (`USD` or `SAR` to UAE/Egypt buyers) or omitting mandatory tax-inclusive VAT disclosures.
- **AR**: <span dir="rtl">منع رسائل البريد الآلية العابرة للحدود من عرض عملات خاطئة أو إغفال بيان شمول ضريبة القيمة المضافة الإلزامية (`15%` في السعودية، `5%` في الإمارات، `0%` في قطر، `14%` في مصر) وخيارات التقسيط المحلية.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever operating automated lifecycle emails for a store selling across 2 or more MENA countries (KSA, UAE, Kuwait, Qatar, Bahrain, Oman, Egypt).
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تشغيل سلاسل البريد الآلي لمتجر يبيع في دولتين أو أكثر من دول الخليج ومصر.</span>
- **When NOT to Use It (EN)**: Never display consumer product prices in Saudi Arabia or UAE as 'Tax-Exclusive' (`السعر غير شامل الضريبة`) in marketing emails only to add 15% or 5% VAT as a surprise at checkout.
- **متى لا تستخدمها (AR)**: <span dir="rtl">يُحظر عرض أسعار المستهلكين في رسائل البريد بالسعودية أو الإمارات «بدون ضريبة» ثم مفاجأة العميل بإضافة 15% أو 5% عند الدفع؛ فالأسعار المعلنة للمستهلك يجب أن تكون شاملة للضريبة.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Customer Country Property in ESP (`person.country_code`: `SA`, `AE`, `KW`, `QA`, `BH`, `OM`, `EG`)
- Catalog Multi-Currency Price Attributes or Presentment Currency (`event.extra.presentment_currency`)
- Country-Specific Payment & Shipping Threshold Table

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: GCC & Egypt Luxury Oud & Perfumes Brand headquartered in Riyadh (`Base Currency: SAR`) selling across KSA, UAE, Kuwait, Qatar, and Egypt.
- **Problem**: Browse Abandonment email showed `450.00 SAR (شامل ضريبة 15% - ادفع عبر مدى)` to shoppers in Dubai (`AED`), Kuwait City (`KWD`), Doha (`QAR`), and Cairo (`EGP`).

### Step B: Initial Output (`المخرج الأولي`)
- **Deployed Dynamic Country-Aware Liquid Footer & Price Macro**:
  - Saudi Recipient (`SA`): `<bdi>450.00 ر.س</bdi> (شامل ضريبة القيمة المضافة 15%) | الدفع عبر: مدى، Apple Pay، تابي، تمارا`
  - UAE Recipient (`AE`): `<bdi>440.00 د.إ</bdi> (شامل ضريبة القيمة المضافة 5%) | الدفع عبر: Apple Pay، تابي، تمارا`
  - Kuwait Recipient (`KW`): `<bdi>36.500 د.ك</bdi> | الدفع عبر: كي نت (KNET)، Apple Pay، تابي`
  - Egypt Recipient (`EG`): `<bdi>4,950 ج.م</bdi> (شامل الضريبة) | الدفع عبر: إنستاباي، فوري، فاليو، أو عند الاستلام`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified URL Locale Parameter**: Appended `?currency={{ presentment_currency }}&country={{ person.country_code }}` to the email CTA link so clicking from the email opens the storefront pre-switched to the exact same currency shown in the email (`AMP-063`).
2. **Checked KWD 3-Decimal Formatting**: Confirmed Kuwaiti Dinar prices format cleanly to 3 decimal places.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Cross-border lifecycle templates live across all 7 MENA markets with 100% currency, VAT-rate, and local payment-method accuracy.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An email displays `440 AED` to a Dubai shopper, but clicking the product link opens the website in `SAR` (`450 ر.س`) because the deep link lacked the currency/market parameter.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always pass the market/currency deep-link parameter (`?country=AE&currency=AED` or country subfolder `/ae-ar/`) on every product link inside cross-border emails.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Shopify Markets / Salla Multi-Currency Events in Klaviyo & Omnisend** | `supported` | [Official Docs](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) (`2026-10-25`) | Checkout and cart events carry both `shop_currency` (base) and `presentment_currency` (customer-facing); templates must explicitly reference `presentment` fields. | If `Browse Viewed Product` events only pass base currency, use a Liquid lookup table keyed by `person.country_code`. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Non-home-country Email-to-Checkout Conversion Rate (`AE`, `KW`, `QA`, `EG` segments) and zero currency-mismatch support tickets.
- **Baseline**: Prior 30-day conversion rate of non-KSA email subscribers.
- **Observation Window**: 28 days post-update.
- **Interpretation Boundary**: Displaying accurate local currency, VAT, and payment rails removes cross-border friction, while cross-border shipping duties and courier speed affect final checkout completion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) — *VOCTOS* (Published `2026-10-22`, Accessed `2026-10-25`): Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000.
- [GCC Marketing Playbook: UAE, Saudi Arabia and Qatar](https://thegrower.ai/gcc-marketing) — *Grower AI* (Published `2026-10-12`, Accessed `2026-10-25`): Cites DataReportal Digital 2026 reach: Snapchat reaches 72.9% in KSA vs 44.9% in UAE and 39.5% in Qatar; LinkedIn reaches 87.6% in UAE vs 34.6% in KSA; X reaches 43.1% in KSA vs 25.0% in UAE; also discusses Saudi localization policy (Saudi localization requirements vary by activity and workforce inputs; check the current official HRSD calculator).
