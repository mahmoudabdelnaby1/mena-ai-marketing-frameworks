# FW-060: Anti-Coupon-Leak Influencer Attribution & Unique Landing-Page / Cart-Link Workflow
## مسار عمل قياس عائد المؤثرين ومنع تسرب أكواد الخصم الثابتة (`Promo Code Cannibalization`) لزيارات الدفع العضوية

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-298`, `AMP-308`, `AMP-318`, `AMP-328`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent browser coupon extensions and Telegram/WhatsApp coupon groups from hijacking static influencer promo codes (`AHMED10`) at checkout—stopping AI attribution models from over-crediting creators for organic sales they didn't drive.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع إضافات المتصفح ومجموعات الكوبونات من سرقة أكواد خصم المؤثرين الثابتة وتطبيقها على المتسوقين العضويين عند الدفع، وضمان قياس المبيعات الحقيقية التي جلبها المؤثر فعلياً.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: In KSA, UAE, and Egypt, static creator promo codes (`SARA15`, `NOOR20`) are scraped within hours by coupon websites, browser extensions, and Telegram channels; organic shoppers already at checkout paste the leaked code, and naive last-touch/code-based AI attribution credits the influencer for 100% of those cannibalized organic orders! An OPERATING_FRAMEWORK combining auto-applied deep links, first-touch UTM validation, and 72-hour code expiration windows fixes creator ROI measurement.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تنتشر أكواد خصم المؤثرين الثابتة (`SARA15`) خلال ساعات في مواقع الكوبونات وقنوات تيليجرام؛ فيقوم المتسوق العضوي الذي دخل الموقع بمفرده بلصق الكود عند الدفع، وتنسب لوحة التحكم البيعة للمؤثر وتدفع له عمولة على عميل لم يجلبه! ويعالج هذا الإطار التشغيلي الخلل عبر الروابط المدمجة والتحقق من مصدر الزيارة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever issuing promo codes or affiliate links to influencers in KSA, UAE, or Egypt on Salla, Zid, Shopify, WooCommerce, or custom apps.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إصدار أكواد خصم أو روابط إحالة للمؤثرين على سلة أو زد أو شوبيفاي أو ووكومرس في السعودية والإمارات ومصر.
- **When NOT to Use It (EN)**: Never pay creator commission or evaluate influencer ROAS on `Total Orders Using Promo Code X` without splitting `Click-Verified Influencer Sessions` vs. `Zero-Click Checkout Code Paste`.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً بحساب عمولة المؤثر أو تقييم عائده الإعلاني بناءً على «إجمالي الطلبات التي استخدمت الكود» دون فصل «الزيارات القادمة فعلياً من رابط المؤثر» عن «لصق الكود في صفحة الدفع من زوار محركات البحث».

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Storefront Auto-Apply Discount URL structure (e.g., `https://store.sa/discount/SARA15?redirect=/collections/best&utm_source=snapchat&utm_medium=influencer&utm_campaign=sara_oct26`)
2. GA4 / Backend Order Attribution Table (`first_user_source_medium`, `session_source_medium`, `coupon_code`, `time_from_landing_to_checkout`)
3. Creator Burst Window (`48–72 hours` post-story)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 3-Layer Anti-Cannibalization Influencer Attribution Workflow

#### Layer 1: Use Time-Boxed Auto-Apply Deep Links (`72-Hour Burst Codes`, Never Permanent Static Codes)
1. Instead of leaving `SARA15` active for 6 months (where coupon scrapers rank for `"كود خصم متجر X"` on Google!), set the promo code's active window in Salla/Zid/Shopify to **`72 hours` starting at the exact hour of the creator's post**.
2. Give the creator a **1-Click Auto-Apply Deep Link** (`https://store.sa/discount/SARA15?utm_source=snapchat&utm_medium=influencer&utm_campaign=sara_oct26`) so real viewers get the discount applied automatically without typing, while stamping their session with `utm_campaign=sara_oct26`.

#### Layer 2: Reconcile "Verified Creator Orders" vs. "Scraped Coupon Cannibalization"
Run this classification logic on every order that uses a creator coupon code:
```python
def classify_influencer_order(order):
    has_creator_utm = (order.get("utm_medium") == "influencer" or "influencer" in order.get("first_touch_medium", ""))
    within_burst_window = order.get("hours_since_creator_post", 999) <= 72
    searched_coupon_on_google = order.get("session_source") == "google" and order.get("seconds_on_site_before_checkout", 999) < 90

    if has_creator_utm and within_burst_window:
        return "TIER_A_VERIFIED_CREATOR_DRIVEN (100% Attribution Weight)"
    elif within_burst_window and not searched_coupon_on_google:
        return "TIER_B_VIEW_THROUGH_PROBABLE (50% Cross-Device Weight)"
    else:
        return "TIER_C_COUPON_SCRAPER_CANNIBALIZATION (0% Creator Credit — Organic Checkout Leak)"
```

#### Layer 3: Block Coupon-Extension Auto-Injection & Protect Branded `"كود خصم [اسم المتجر]"` SERPs
- Create a dedicated evergreen page on your own store (`/ar/coupons` or `/ar/offers`) targeting `"كود خصم [اسم متجرك]"` with a modest `5%` welcome code (`WELCOME5`) so organic coupon-hunters land on your own page rather than scraping a `20%` influencer code from third-party coupon sites!

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Salla, Zid & Shopify Discount Code Expiration Scheduling & Auto-Apply URLs** | `supported` | [Official Reference](https://voctos.net/ga4-ai-traffic-arab-markets/) (`2026-10-25`) | All major MENA e-commerce platforms support start/end timestamps on coupon codes and URL-parameter discount auto-application. | Always set an explicit end date (`+72 hours` from post time) when creating any influencer promo code. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-298`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Unique single-creator codes paired with dedicated landing URLs and new-vs-returning customer split reporting.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-308`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Unique single-creator codes paired with dedicated landing URLs and new-vs-returning customer split reporting.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-318`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Unique single-creator codes paired with dedicated landing URLs and new-vs-returning customer split reporting.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-328`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Unique single-creator codes paired with dedicated landing URLs and new-vs-returning customer split reporting.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-528`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-298 (Influencer Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Saudi Footwear & Sportswear Store on Salla/Shopify.
- **Problem**: Paid Creator X a `15%` commission on `410` orders that used code `FAHAD15` over 30 days. Forensic GA4 + backend audit revealed only `95` orders (`23%`) occurred during the 72-hour story burst or carried `utm_medium=influencer`; the other `315` orders (`77%`) happened weeks later from shoppers who were already on the checkout page, opened Google to search `"كود خصم متجر ..."`, found `FAHAD15` on a coupon site, and pasted it!
- **Human Review & Key Edits Applied**: 1. **Updated Creator Contract Commission Clause**: Defined commission-eligible orders strictly as orders placed via the tracked link or using the burst code **within 72 hours of story publication**.
2. **Launched `/ar/offers` Branded Coupon Page**: Captured `"كود خصم [اسم المتجر]"` searchers with a `5%` first-order code instead of leaking `15%` creator codes.
- **Final Usable Output**: - Stopped `77%` coupon-scraper commission overpayment and locked all creator codes to 72-hour burst windows with auto-applied UTM deep links.
- **What Can Go Wrong**: A creator refuses to use a link sticker and only says the promo code verbally on Snapchat; because Snapchat viewers open Safari/Chrome manually and type the store name on Google, 100% of their legitimate orders arrive as `google / organic` in GA4.
- **Correction & Fallback**: That is exactly why `classify_influencer_order()` includes **`TIER_B_VIEW_THROUGH_PROBABLE`**: for verbal-only Snapchat/TikTok posts, measure the **72-hour incremental lift in branded organic + direct orders using the burst code** compared to the prior 7-day baseline, and immediately expire the code at Hour 72 so coupon sites cannot harvest it later.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Incremental Creator ROAS (`(Tier_A_Revenue + 0.5 * Tier_B_Revenue) / Creator_Fee`) and Reduction in Unattributed Coupon Discount Leakage (`%`).
- **Baseline Definition**: Prior 30-day raw promo-code order count vs. UTM-verified + 72h burst order count.
- **Observation Window**: 72 hours post-creator activation. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Separating burst/UTM orders from late coupon-scraper usage prevents overpaying for cannibalized organic traffic.
