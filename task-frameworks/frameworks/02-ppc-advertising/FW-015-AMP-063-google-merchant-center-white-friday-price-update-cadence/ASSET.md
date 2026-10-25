# FW-015: Google Merchant Center White Friday Price-Update Cadence & Sale-Price Schema Checklist
## قائمة فحص وتوقيت تحديث الأسعار في Google Merchant Center خلال الجمعة البيضاء والمواسم لمنع رفض المنتجات

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-073`, `AMP-083`, `AMP-093`, `AMP-103`, `AMP-113`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Performance Marketing Manager, Media Buyer, PPC Specialist, Growth Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Schedule promotional price updates in Google Merchant Center using `sale_price` and `sale_price_effective_date` instead of mutating base `price` more than once per day.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: جدولة عروض الجمعة البيضاء والمواسم في Google Merchant Center باستخدام حقول `sale_price` و`sale_price_effective_date` بدلاً من تغيير السعر الأساسي أكثر من مرة يومياً وتجنب رفض المنتجات.
- **Why `CHECKLIST` Fits This User Job (EN)**: Google Merchant Center's 27 Sep 2026 policy explicitly warns that changing prices more than once a day causes automatic item updates to fail and risks item disapproval; a technical CHECKLIST for feed scheduling prevents mid-White-Friday Shopping/PMax blackouts.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تحذر وثيقة سياسات Google Merchant Center (المحدثة في 27 سبتمبر 2026) من أن تغيير الأسعار أكثر من مرة في اليوم يعطل التحديث التلقائي ويعرض المنتجات للرفض؛ لذا تحمي قائمة الفحص هذه حملات التسوق في ذروة المواسم.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before running White/Yellow Friday, Ramadan, Eid, Saudi National/Founding Day, or flash-sale campaigns linked to Google Merchant Center (`PMax` / `Shopping`).
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل تشغيل عروض الجمعة البيضاء أو رمضان أو العيد أو اليوم الوطني المرتبطة بحساب Google Merchant Center.
- **When NOT to Use It (EN)**: Do not use dynamic hourly repricing scripts or countdown-timer price mutations on URLs submitted to Google Merchant Center.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بتشغيل إضافات التغيير الساعي للأسعار على صفحات المنتجات المربوطة بـ Google Merchant Center.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Promotional SKU list with Base Price (`price`), Promotional Price (`sale_price`), and exact start/end timestamps with timezone offset (`+03:00` KSA/Egypt DST or `+04:00` UAE)
2. Product page JSON-LD `offers` schema configuration
3. Statutory discount permit & baseline price history (`AMP-064`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### White Friday & Peak-Season GMC Price Stability Checklist

#### 1. Hard Feed Rules (Google Merchant Center Policy — Verified 2026-10-25)
- [ ] **Rule 1 — Max 1 Price Change Per 24 Hours**: Never mutate the base `price` attribute or landing page JSON-LD price more than **once per day**. Frequent intraday changes cause GMC Automatic Item Updates (`تحديثات السلع التلقائية`) to fail and trigger `[price_mismatch]` disapprovals.
- [ ] **Rule 2 — Use `sale_price` + `sale_price_effective_date` Instead of Overwriting `price`**:
  - Keep `[price]` locked to your stable baseline price (e.g., `400.00 SAR`).
  - Pass the discount in `[sale_price]` (e.g., `299.00 SAR`).
  - Pass the exact ISO 8601 window in `[sale_price_effective_date]` with explicit Riyadh/Cairo/Dubai offset:
    `2026-11-20T00:00+03:00/2026-11-30T23:59+03:00`
- [ ] **Rule 3 — Match Currency ISO Code & Tax Inclusion**:
  - **Saudi Arabia (`SAR`)**: Must include 15% ZATCA VAT on both the landing page and the GMC feed (`AMP-239`).
  - **UAE (`AED`)**: Must include 5% VAT.
  - **Egypt (`EGP`)**: Must include 14% VAT where applicable.
- [ ] **Rule 4 — Pre-Upload 48 Hours Before Flash Sale Launch**:
  - Submit the feed containing `sale_price` and `sale_price_effective_date` at least **48 hours before** the promotion starts so Google crawls and pre-approves the schedule without crawl lag.
- [ ] **Rule 5 — For Extra Intraday Flash Deals (Use Coupon Code / Merchant Promotions, Not Price Edits)**:
  - If you want a 4-hour evening booster during White Friday, keep the landing page price fixed and offer an extra promo code (`WF10`) via **Google Merchant Promotions** or a site banner—never alter the HTML/JSON-LD product price mid-day!

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Google Merchant Center Price Attribute & Automatic Item Updates Policy (27 Sep 2026)** | `supported` | [Official Reference](https://voctos.net/merchant-center-price-changes-white-friday-arab-stores/) (`2026-10-25`) | Google's 27 Sep 2026 Merchant Center guidance warns against updating prices >1x/day and recommends `sale_price` + `sale_price_effective_date`. | Use promo codes / Merchant Promotions for short intraday offers instead of mutating product page prices. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-073`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Static single-window promotions where feed sale_price and sale_price_effective_date are synced 24 hours ahead.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-083`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Static single-window promotions where feed sale_price and sale_price_effective_date are synced 24 hours ahead.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-093`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Static single-window promotions where feed sale_price and sale_price_effective_date are synced 24 hours ahead.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-103`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Static single-window promotions where feed sale_price and sale_price_effective_date are synced 24 hours ahead.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-113`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Static single-window promotions where feed sale_price and sale_price_effective_date are synced 24 hours ahead.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Saudi Home Appliances Store on Salla/Shopify syncing 600 SKUs to Google Merchant Center for White Friday (20–30 Nov 2026).
- **Previous Failure**: Team changed product prices 3 times on White Friday (Morning Deal, Afternoon Deal, Midnight Deal); GMC disapproved 410 of 600 SKUs for `Price mismatch between feed and landing page` during peak weekend traffic.
- **Human Review & Key Edits Applied**: 1. **JSON-LD Sync Check**: Verified that the storefront Product JSON-LD outputs `749.00` (`SAR`) starting at `2026-11-20T00:00+03:00` and stays locked at `749.00` for the entire 10-day window.
2. **Midnight Booster Workaround**: Replaced the planned midnight price drop with a checkout promo code (`FRIDAY50`) so the landing page `<meta itemprop="price">` and JSON-LD `offers.price` never fluctuate intraday.
- **Final Usable Output**: - All 600 SKUs pre-approved in Google Merchant Center 48 hours ahead of White Friday with `0` `[price_mismatch]` disapprovals and automatic `sale_price` badge activation at `00:00+03:00`.
- **What Can Go Wrong**: A store enables a multi-currency Geo-IP switcher script that serves `USD` prices to Googlebot (crawling from a US IP) while the GMC KSA feed submits `SAR` prices, causing 100% account-wide price/currency mismatch disapproval.
- **Correction & Fallback**: Never redirect or rewrite currency based on visitor IP on country-specific Merchant Center URLs; use separate URL paths/parameters (`?currency=SAR`) or keep the `.sa` storefront locked to `SAR` regardless of crawler IP.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Percentage of active/approved items in Google Merchant Center Diagnostics during peak sale week (`Target: >=99% Approved`).
- **Baseline Definition**: Prior seasonal event disapproval count for `Price mismatch`.
- **Observation Window**: Full promotional period (e.g., 10 days of White Friday). *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Feed approval keeps Shopping/PMax ads serving uninterrupted, while ROAS still depends on bid strategy and competitive pricing.
