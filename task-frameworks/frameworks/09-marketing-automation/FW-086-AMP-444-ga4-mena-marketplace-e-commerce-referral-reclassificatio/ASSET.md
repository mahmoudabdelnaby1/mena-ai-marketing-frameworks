# FW-086: GA4 MENA Marketplace & E-Commerce Referral Reclassification Checklist (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`)
## قائمة فحص إعادة تصنيف المتاجر والأسواق العربية (`amazon.sa`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`) في `GA4` بدلاً من ضياعها في `Referral`

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-454`, `AMP-464`, `AMP-474`, `AMP-484`, `AMP-494`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Rescue traffic from `amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, `haraj.com.sa`, `dubizzle`, and `instashop` that Google's 819-domain default GA4 source list misclassifies as generic `Referral` instead of `Shopping`.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إنقاذ الزيارات القادمة من منصات التجارة العربية (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, `حراج`, `دوبيزل`) التي تصنفها قائمة جوجل الافتراضية في `GA4` كإحالات عادية (`Referral`) بدلاً من قنوات التسوق (`Shopping`).
- **Why `CHECKLIST` Fits This User Job (EN)**: VOCTOS's October 2026 line-by-line inspection of all 819 entries in Google's official GA4 `Source Categories` PDF confirmed that while `amazon.com` and `amazon.co.uk` are classified as `SOURCE_CATEGORY_SHOPPING`, **`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, and `haraj.com.sa` are completely absent from Google's list**—causing GA4 to dump all traffic from regional marketplaces into generic `Referral` (and causing self-referrals when customers return from `salla.sa`/`zid.sa` checkout sub-routes)!
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: أثبت الفحص الكامل لقائمة جوجل الرسمية لمصادر `GA4` (البالغة 819 نطاقاً — أكتوبر 2026) غياب النطاقات العربية كلياً (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, `haraj.com.sa`) رغم وجود `amazon.com`؛ مما يؤدي لرمي زيارات المتاجر الإقليمية داخل `Referral` أو تدمير الإحالة الأصلية عبر الإحالة الذاتية (`Unwanted Referrals`)!

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when auditing GA4 properties for any brand, marketplace seller, or e-commerce store operating in Saudi Arabia, UAE, or Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند ضبط أو تدقيق حساب `GA4` لأي علامة تجارية أو متجر إلكتروني يعمل في السعودية أو الإمارات أو مصر.
- **When NOT to Use It (EN)**: Be careful to distinguish **External Regional Marketplaces** (which belong in `Organic Shopping` / `Paid Shopping`) from **Your Own Storefront Checkout/Payment Domains** (`salla.sa`, `zid.sa`, `tabby.ai`, `tamara.co`, `paymob.com` — which belong in **`List Unwanted Referrals`** so they don't overwrite the original ad source!).
- **متى لا تستخدم هذه الأداة (AR)**: انتبه للتفريق الحاسم بين: (1) **الأسواق الخارجية** (`amazon.sa / noon.com / haraj.com.sa`) التي تضاف لقناة `Shopping`، وبين (2) **نطاقات الدفع وإتمام الطلب الخاصة بمتجرك** (`salla.sa / tabby.ai / tamara.co / paymob.com`) التي يجب إضافتها لقائمة **`Unwanted Referrals`** لمنع مسح مصدر الإعلان الأصلي!

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. GA4 Admin access (`Data Streams -> Configure tag settings -> List unwanted referrals` AND `Data display -> Channel groups`)
2. List of active payment gateways (`Tabby`, `Tamara`, `Moyasar`, `HyperPay`, `Tap`, `Paymob`, `Fawry`, `Kashier`) and storefront domains

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Dual GA4 MENA Marketplace Channel & Unwanted-Referral Fix Checklist

#### Part 1: CRITICAL — Add MENA Payment Gateways & Platform Subdomains to `List Unwanted Referrals`
When a shopper clicks a Meta/Google/Snap ad, lands on your store, goes to `checkout.tabby.ai` or `tamara.co` or `accept.paymob.com` to pay, and redirects back to your `/thank-you` page, GA4 sees `tabby.ai` or `paymob.com` as a new referrer and **credits `tabby.ai / referral` with 100% of the sale instead of your paid ad**!
- [ ] Open `GA4 Admin -> Data Streams -> [Your Web Stream] -> Configure tag settings -> Show more -> List unwanted referrals` and add:
  - **Storefront / Checkout Domains**: `salla.sa`, `zid.sa`, `myshopify.com`, plus your own custom domain (`yourdomain.sa`).
  - **GCC & Egypt BNPL & Payment Gateways**:
    `tabby.ai`, `tamara.co`, `moyasar.com`, `hyperpay.com`, `tap.company`, `gonoon.com`, `payfort.com`, `urway-tech.com`, `geidea.net`, `paymob.com`, `accept.paymob.com`, `fawry.com`, `atfawry.com`, `kashier.io`, `valu.com.eg`, `sympl.ai`, `myfatoorah.com`.

#### Part 2: Add Regional Marketplaces (`Amazon.sa/.ae/.eg`, `Noon`, `Haraj`, `Dubizzle`) to GA4 `Organic Shopping` & `Paid Shopping`
In `GA4 Admin -> Data display -> Channel groups` (inside the same custom Channel Group from `AMP-443`), edit **`Organic Shopping`** and **`Paid Shopping`** (placed **above `Referral`**) to include this **Source** regex:
```regex
(?i).*(amazon\.(sa|ae|eg|com|co\.uk)|noon\.com|namshi\.com|ounass\.(ae|sa|com)|styli\.com|niceonesa\.com|golden-scent\.com|goldenscent\.com|jarir\.com|extra\.com|btech\.com|jumia\.com\.eg|haraj\.com\.sa|dubizzle\.(com|com\.eg)|opensooq\.com|instashop\.com|talabat\.com|jahez\.net|hungerstation\.com|careem\.com|mrsool\.co).*
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Google Analytics 4 Default Source Categories PDF (819 Domains) vs. Unwanted Referrals & Custom Channel Groups** | `supported` | [Official Reference](https://voctos.net/ga4-ai-traffic-arab-markets/) (`2026-10-25`) | VOCTOS Oct 2026 audit of Google's 819-entry GA4 source category list proved that `amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, and `zid.sa` are absent from Google's default list. | Maintain the custom MENA Shopping Regex in GA4 Channel Groups and the MENA Payment Gateway list in Unwanted Referrals. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-454`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Adding a custom 'Arab Marketplaces' GA4 channel group rule matching `amazon\.(sa|ae|eg)|noon\.com|namshi\.com|salla\.sa|zid\.sa|haraj\.com\.sa` positioned above Referral.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-464`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Adding a custom 'Arab Marketplaces' GA4 channel group rule matching `amazon\.(sa|ae|eg)|noon\.com|namshi\.com|salla\.sa|zid\.sa|haraj\.com\.sa` positioned above Referral.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-474`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Adding a custom 'Arab Marketplaces' GA4 channel group rule matching `amazon\.(sa|ae|eg)|noon\.com|namshi\.com|salla\.sa|zid\.sa|haraj\.com\.sa` positioned above Referral.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-484`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Adding a custom 'Arab Marketplaces' GA4 channel group rule matching `amazon\.(sa|ae|eg)|noon\.com|namshi\.com|salla\.sa|zid\.sa|haraj\.com\.sa` positioned above Referral.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-494`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Adding a custom 'Arab Marketplaces' GA4 channel group rule matching `amazon\.(sa|ae|eg)|noon\.com|namshi\.com|salla\.sa|zid\.sa|haraj\.com\.sa` positioned above Referral.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Riyadh & Cairo Beauty Brand selling D2C on its own site (with Tabby, Tamara, and Paymob) AND linking from brand store pages/campaigns on `amazon.sa`, `noon.com`, and `niceonesa.com`.
- **Audit Findings Before Fix**:
  1. `38%` of all paid conversions in GA4 were attributed to `tabby.ai / referral`, `tamara.co / referral`, and `accept.paymob.com / referral` (destroying paid ad ROAS visibility!).
  2. Traffic arriving from `amazon.sa`, `amazon.eg`, and `noon.com` was buried inside generic `Referral` instead of `Shopping`.
- **Human Review & Key Edits Applied**: 1. **Verified `ignore_referrer=true` on Payment Return**: Confirmed in GA4 DebugView that completing a test order via Tabby and Paymob preserves the original `utm_source=meta / utm_medium=paid_social` session instead of starting a new `referral` session.
2. **Retroactive Verification**: Confirmed historical `amazon.sa` and `noon.com` sessions moved cleanly from `Referral` into `Organic/Paid Shopping`.
- **Final Usable Output**: - Eliminated payment-gateway self-referral hijacking (`38%` of revenue restored to true acquisition channels) and classified all MENA marketplaces (`Amazon.sa/.ae/.eg`, `Noon`, `NiceOne`, `Haraj`, `B.TECH`) under `Shopping`.
- **What Can Go Wrong**: An analyst puts `salla.sa` into the `Organic Shopping` Channel Group rule on a store whose own checkout is hosted on a `salla.sa` subdomain WITHOUT adding `salla.sa` to `Unwanted Referrals`—causing every checkout redirect to be counted as a new 'Organic Shopping' session!
- **Correction & Fallback**: Always complete **Part 1 (`List Unwanted Referrals`) FIRST** for your own store/checkout/payment domains, and reserve **Part 2 (`Shopping` Channel Regex)** for external third-party marketplaces where users discover your brand.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Zero revenue attributed to payment gateways (`tabby.ai / tamara.co / paymob.com / moyasar.com`) in GA4 `Session source / medium`, and accurate `Shopping` channel reporting for regional marketplaces.
- **Baseline Definition**: Percentage of GA4 revenue previously hijacked by payment gateway referrals.
- **Observation Window**: 7 days post-deployment for `Unwanted Referrals` (forward-looking) + immediate retroactive reclassification for Custom Channel Groups. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Fixing referral exclusion restores true first/last-click acquisition credit in GA4; pair with Server CAPI (`AMP-067`) for in-platform ad optimization.
