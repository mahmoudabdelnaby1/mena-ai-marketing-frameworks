# FW-079: Authentic Verified-Buyer Review & Social Proof Governance Checklist (Eliminating Fake AI Review Widgets)
## قائمة فحص حوكمة التقييمات وإثباتات الثقة الاجتماعية (`Social Proof` — منع ودجات التقييمات الوهمية المولدة بالذكاء الاصطناعي)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-402`, `AMP-412`, `AMP-422`, `AMP-432`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Remove deceptive AI-generated review widgets and fake `'سارة من الرياض اشترت قبل دقيقتين'` popups that violate Saudi E-Commerce Law, UAE Consumer Protection Law, and Egypt Law 181/2018, replacing them with automated post-delivery WhatsApp verified-buyer review collection.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إزالة إضافات التقييمات الوهمية وإشعارات الشراء الزائفة («سارة من الرياض اشترت قبل دقيقتين») التي تخالف نظام التجارة الإلكترونية السعودي وقانون حماية المستهلك الإماراتي والمصري، واستبدالها بنظام جمع تقييمات حقيقية موثقة بعد التسليم عبر واتساب.
- **Why `CHECKLIST` Fits This User Job (EN)**: AI store-builder plugins often pre-populate new stores with 50 fake Arabic reviews (`'منتج رائع جداً أنصح به بشدة - محمد العتيبي'`) and fake real-time purchase toast popups; Arab shoppers immediately spot translated-sounding fake reviews, and Saudi Ministry of Commerce / UAE / Egypt CPA laws strictly penalize deceptive commercial representations—making a cleanup + verified-review collection CHECKLIST essential.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تقوم العديد من إضافات بناء المتاجر بالذكاء الاصطناعي بملء المتجر الجديد بـ 50 تقييماً عربياً وهمياً وإشعارات منبثقة كاذبة؛ ويكتشف المتسوق العربي زيف هذه التقييمات فوراً، فضلاً عن كونها مخالفة صريحة لنظام التجارة الإلكترونية السعودي وقوانين حماية المستهلك في الإمارات ومصر؛ لذا تستبدلها قائمة الفحص هذه بآلية جمع تقييمات موثقة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when auditing product pages, landing pages, or app store listings across KSA, UAE, and Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند تدقيق صفحات المنتجات وصفحات الهبوط في السعودية والإمارات ومصر.
- **When NOT to Use It (EN)**: Never import scraped AliExpress/Amazon reviews translated by AI into Arabic onto your store, and never run random-timer 'X from Jeddah just bought this' popups.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً باستيراد تقييمات مترجمة آلياً من مواقع خارجية (`AliExpress / Amazon`) وادعاء أنها لعملاء متجرك، ولا تشغل نوافذ إشعارات الشراء العشوائية الوهمية.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Audit of installed review & social-proof apps (`Judge.me`, `Loox`, `Salla Reviews`, `Zid Reviews`, `Sales Pop`)
2. Courier `DELIVERED` webhook trigger (`T+3 days after physical delivery`)
3. Saudi `Maroof` (`معروف`) / Saudi Business Center (`المركز السعودي للأعمال - موثق`) badge link

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Social Proof Authenticity & Verified-Review Collection Checklist

#### 1. Immediate Purge Checklist (`Delete Deceptive AI Social Proof`)
- [ ] **Check 1 — Purge Translated/Scraped & AI-Generated Reviews**:
  - Delete any review not tied to a real backend `order_id` (`طلب مكتمل ومسلّم`).
  - Remove fake AI avatar headshots paired with generic MSA praise (`"لقد كانت تجربة تسوق مذهلة للغاية"`).
- [ ] **Check 2 — Disable Fake Random-Timer Purchase Toast Popups**:
  - Uninstall or disable any popup plugin that fabricates `"فهد من الرياض اشترى هذا المنتج قبل 3 دقائق"` on a random loop (it both violates consumer-protection truth-in-advertising rules and annoys mobile shoppers by covering product photos!).
- [ ] **Check 3 — Replace Fake Popups with Official Government & Payment Trust Badges**:
  - **In KSA**: Link your verified **Saudi Business Center (`المركز السعودي للأعمال - توثيق التجارة الإلكترونية`)** / Commercial Registration (`السجل التجاري`) and Tax ID (`الرقم الضريبي`) in the footer + PDP trust bar.
  - **In UAE**: Display verified **DED / Dubai Economy E-Trader License** number.
  - **In Egypt**: Display **Tax Registration Number (`رقم التسجيل الضريبي`)** + clear 14-day CPA return policy link.

#### 2. High-Response Post-Delivery WhatsApp Review Collection Flow (`T+3 Days After Courier Delivery`)
Instead of faking reviews, collect 10–18% verified buyer reviews automatically via WhatsApp (`where open rates exceed 85% in MENA` vs. `<15%` for review emails):
1. **Trigger**: `Courier_Status == 'DELIVERED'` + `72 hours` elapsed (never trigger `T+7 days after order placement` without checking if the parcel was actually delivered!).
2. **WhatsApp Interactive Message**:
   `"أهلاً {{first_name}} 🌟 نتمنى أن طلبك ({{product_name}}) نال إعجابك! تقييمك بكلمة أو صورة للمنتج يساعد المتسوقين ويكسبك كود خصم 10% لطلبك القادم (يرسل لك تلقائياً فور إضافة التقييم بغض النظر عن عدد النجوم): {{one_click_verified_review_link}}"`
   *(Compliance Rule: If offering a thank-you coupon for leaving a review, grant it for **any honest review regardless of star rating**, never conditioned on leaving 5 stars!).*

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi E-Commerce Law, UAE Consumer Protection Law & Google Rich Results Review Schema Guidelines** | `supported` | [Official Reference](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) (`2026-10-25`) | Regional consumer laws prohibit fabricated reviews and false popularity indicators; Google Search Central also issues manual actions if `aggregateRating` JSON-LD is populated with non-genuine or scraped reviews. | If a brand-new product has `0` reviews yet, hide the star counter (`عرض: منتج جديد`) and highlight the official warranty and Saudi Business Center verification badge until the first 3 real buyer reviews arrive. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-402`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Displaying only verified buyer reviews synced from real order IDs with verified-purchase badges.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-412`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Displaying only verified buyer reviews synced from real order IDs with verified-purchase badges.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-422`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Displaying only verified buyer reviews synced from real order IDs with verified-purchase badges.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-432`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Displaying only verified buyer reviews synced from real order IDs with verified-purchase badges.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Jeddah & Cairo D2C Home Appliance Store.
- **Problem**: Agency had installed an AI review generator that posted 120 reviews in formal translated Arabic (`"هذا الخلاط يغير قواعد اللعبة في مطبخي - جون سميث / الرياض"`) and a popup firing every 8 seconds. Bounce rate was `76%` and comments on Instagram ads called the site a scam.
- **Human Review & Key Edits Applied**: 1. **Kept Genuine 4-Star Constructive Reviews Live**: Instructed moderation staff NOT to hide honest 4-star reviews (e.g., `"المنتج ممتاز وصوته هادي بس الكرتون وصل متأخر يوم"`), because a `4.7 / 5.0` rating with real Saudi/Egyptian dialect phrasing converts significantly higher than a suspicious `5.00 / 5.00` wall of AI praise!
2. **Validated `aggregateRating` Schema (`AMP-007`)**: Connected the verified review count (`142 real reviews, 4.8 average`) to the `Product` JSON-LD schema.
- **Final Usable Output**: - `142` genuine, order-verified customer reviews (with real mobile photos in Saudi & Egyptian homes) collected in 21 days; PDP conversion rate increased by `+29%`.
- **What Can Go Wrong**: An automated review email fires `5 days after Order Placed`; because a shipment to Upper Egypt or Northern KSA took 6 days to arrive, the customer receives `'كيف كان المنتج؟ قيمه الآن!'` before receiving the parcel, prompting an angry 1-star review saying `'الطلب لم يصلني أصلاً!'`.
- **Correction & Fallback**: Trigger review requests **strictly off the Courier `DELIVERED` event (`+48 to 72 hours`)**, never off `Order Placed + X days`!

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Verified-Buyer Review Submission Rate (`Target: >= 8–12%` of delivered orders via WhatsApp) and PDP Conversion Rate.
- **Baseline Definition**: Count of genuine `order_id`-linked reviews.
- **Observation Window**: 28 days post-implementation. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Authentic dialect reviews with real customer photos build high local trust, while product quality governs actual star ratings.
