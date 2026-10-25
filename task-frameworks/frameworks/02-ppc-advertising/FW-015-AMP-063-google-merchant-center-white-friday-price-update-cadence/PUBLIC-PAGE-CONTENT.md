# Google Merchant Center White Friday Price-Update Cadence & Sale-Price Schema Checklist
## <span dir="rtl">قائمة فحص وتوقيت تحديث الأسعار في Google Merchant Center خلال الجمعة البيضاء والمواسم لمنع رفض المنتجات</span>

> **Asset ID**: `FW-015` (`AMP-063`) | **Artifact Type**: `CHECKLIST` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Schedule promotional price updates in Google Merchant Center using `sale_price` and `sale_price_effective_date` instead of mutating base `price` more than once per day.
- **AR**: <span dir="rtl">جدولة عروض الجمعة البيضاء والمواسم في Google Merchant Center باستخدام حقول `sale_price` و`sale_price_effective_date` بدلاً من تغيير السعر الأساسي أكثر من مرة يومياً وتجنب رفض المنتجات.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before running White/Yellow Friday, Ramadan, Eid, Saudi National/Founding Day, or flash-sale campaigns linked to Google Merchant Center (`PMax` / `Shopping`).
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل تشغيل عروض الجمعة البيضاء أو رمضان أو العيد أو اليوم الوطني المرتبطة بحساب Google Merchant Center.</span>
- **When NOT to Use It (EN)**: Do not use dynamic hourly repricing scripts or countdown-timer price mutations on URLs submitted to Google Merchant Center.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بتشغيل إضافات التغيير الساعي للأسعار على صفحات المنتجات المربوطة بـ Google Merchant Center.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Promotional SKU list with Base Price (`price`), Promotional Price (`sale_price`), and exact start/end timestamps with timezone offset (`+03:00` KSA/Egypt DST or `+04:00` UAE)
- Product page JSON-LD `offers` schema configuration
- Statutory discount permit & baseline price history (`AMP-064`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Saudi Home Appliances Store on Salla/Shopify syncing 600 SKUs to Google Merchant Center for White Friday (20–30 Nov 2026).
- **Previous Failure**: Team changed product prices 3 times on White Friday (Morning Deal, Afternoon Deal, Midnight Deal); GMC disapproved 410 of 600 SKUs for `Price mismatch between feed and landing page` during peak weekend traffic.

### Step B: Initial Output (`المخرج الأولي`)
```xml
<!-- Compliant GMC XML Item Entry Pre-Scheduled 48h Before White Friday -->
<item>
  <g:id>SKU-COFF-901</g:id>
  <g:title>ماكينة قهوة إسبريسو ديلونجي ديديكا 15 بار - فضي</g:title>
  <g:price>999.00 SAR</g:price>
  <g:sale_price>749.00 SAR</g:sale_price>
  <g:sale_price_effective_date>2026-11-20T00:00+03:00/2026-11-30T23:59+03:00</g:sale_price_effective_date>
  <g:availability>in_stock</g:availability>
</item>
```

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **JSON-LD Sync Check**: Verified that the storefront Product JSON-LD outputs `749.00` (`SAR`) starting at `2026-11-20T00:00+03:00` and stays locked at `749.00` for the entire 10-day window.
2. **Midnight Booster Workaround**: Replaced the planned midnight price drop with a checkout promo code (`FRIDAY50`) so the landing page `<meta itemprop="price">` and JSON-LD `offers.price` never fluctuate intraday.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- All 600 SKUs pre-approved in Google Merchant Center 48 hours ahead of White Friday with `0` `[price_mismatch]` disapprovals and automatic `sale_price` badge activation at `00:00+03:00`.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A store enables a multi-currency Geo-IP switcher script that serves `USD` prices to Googlebot (crawling from a US IP) while the GMC KSA feed submits `SAR` prices, causing 100% account-wide price/currency mismatch disapproval.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Never redirect or rewrite currency based on visitor IP on country-specific Merchant Center URLs; use separate URL paths/parameters (`?currency=SAR`) or keep the `.sa` storefront locked to `SAR` regardless of crawler IP.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Google Merchant Center Price Attribute & Automatic Item Updates Policy (27 Sep 2026)** | `supported` | [Official Docs](https://voctos.net/merchant-center-price-changes-white-friday-arab-stores/) (`2026-10-25`) | Google's 27 Sep 2026 Merchant Center guidance warns against updating prices >1x/day and recommends `sale_price` + `sale_price_effective_date`. | Use promo codes / Merchant Promotions for short intraday offers instead of mutating product page prices. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Percentage of active/approved items in Google Merchant Center Diagnostics during peak sale week (`Target: >=99% Approved`).
- **Baseline**: Prior seasonal event disapproval count for `Price mismatch`.
- **Observation Window**: Full promotional period (e.g., 10 days of White Friday).
- **Interpretation Boundary**: Feed approval keeps Shopping/PMax ads serving uninterrupted, while ROAS still depends on bid strategy and competitive pricing.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Merchant Center May Now Disapprove Products Whose Price Changes More Than Once a Day: A White Friday Price-Markup Audit of Arab Online Stores](https://voctos.net/merchant-center-price-changes-white-friday-arab-stores/) — *VOCTOS* (Published `2026-10-15`, Accessed `2026-10-25`): Google Merchant Center (updated 27 Sep 2026) warns automatic item updates fail and products risk disapproval when prices change >1x/day; in an audit of 40 Arab stores (Salla, Zid, Shopify, WooCommerce across KSA, UAE, Egypt), 0 of 24 discounted pages included readable sale_price_effective_date schema markup.
- [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) — *VOCTOS* (Published `2026-10-22`, Accessed `2026-10-25`): Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000.
