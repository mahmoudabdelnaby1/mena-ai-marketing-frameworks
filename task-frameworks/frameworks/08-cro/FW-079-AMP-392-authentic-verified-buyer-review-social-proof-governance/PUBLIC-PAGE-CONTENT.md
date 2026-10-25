# Authentic Verified-Buyer Review & Social Proof Governance Checklist (Eliminating Fake AI Review Widgets)
## <span dir="rtl">قائمة فحص حوكمة التقييمات وإثباتات الثقة الاجتماعية (`Social Proof` — منع ودجات التقييمات الوهمية المولدة بالذكاء الاصطناعي)</span>

> **Asset ID**: `FW-079` (`AMP-392`) | **Artifact Type**: `CHECKLIST` | **Channel**: CRO - Conversion Rate Optimization | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Remove deceptive AI-generated review widgets and fake `'سارة من الرياض اشترت قبل دقيقتين'` popups that violate Saudi E-Commerce Law, UAE Consumer Protection Law, and Egypt Law 181/2018, replacing them with automated post-delivery WhatsApp verified-buyer review collection.
- **AR**: <span dir="rtl">إزالة إضافات التقييمات الوهمية وإشعارات الشراء الزائفة («سارة من الرياض اشترت قبل دقيقتين») التي تخالف نظام التجارة الإلكترونية السعودي وقانون حماية المستهلك الإماراتي والمصري، واستبدالها بنظام جمع تقييمات حقيقية موثقة بعد التسليم عبر واتساب.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when auditing product pages, landing pages, or app store listings across KSA, UAE, and Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند تدقيق صفحات المنتجات وصفحات الهبوط في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Never import scraped AliExpress/Amazon reviews translated by AI into Arabic onto your store, and never run random-timer 'X from Jeddah just bought this' popups.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم أبداً باستيراد تقييمات مترجمة آلياً من مواقع خارجية (`AliExpress / Amazon`) وادعاء أنها لعملاء متجرك، ولا تشغل نوافذ إشعارات الشراء العشوائية الوهمية.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Audit of installed review & social-proof apps (`Judge.me`, `Loox`, `Salla Reviews`, `Zid Reviews`, `Sales Pop`)
- Courier `DELIVERED` webhook trigger (`T+3 days after physical delivery`)
- Saudi `Maroof` (`معروف`) / Saudi Business Center (`المركز السعودي للأعمال - موثق`) badge link

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Jeddah & Cairo D2C Home Appliance Store.
- **Problem**: Agency had installed an AI review generator that posted 120 reviews in formal translated Arabic (`"هذا الخلاط يغير قواعد اللعبة في مطبخي - جون سميث / الرياض"`) and a popup firing every 8 seconds. Bounce rate was `76%` and comments on Instagram ads called the site a scam.

### Step B: Initial Output (`المخرج الأولي`)
- **Executed Authenticity Overhaul**:
  1. Deleted all 120 unverified/translated reviews and uninstalled the fake toast popup app.
  2. Added the store's official **Saudi Business Center Verification Badge (`موثق في المركز السعودي للأعمال`)** and clear 2-year warranty card below the Add-to-Cart button.
  3. Launched the `T+3 Days Post-Delivery` WhatsApp review request flow for real delivered orders.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Kept Genuine 4-Star Constructive Reviews Live**: Instructed moderation staff NOT to hide honest 4-star reviews (e.g., `"المنتج ممتاز وصوته هادي بس الكرتون وصل متأخر يوم"`), because a `4.7 / 5.0` rating with real Saudi/Egyptian dialect phrasing converts significantly higher than a suspicious `5.00 / 5.00` wall of AI praise!
2. **Validated `aggregateRating` Schema (`AMP-007`)**: Connected the verified review count (`142 real reviews, 4.8 average`) to the `Product` JSON-LD schema.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `142` genuine, order-verified customer reviews (with real mobile photos in Saudi & Egyptian homes) collected in 21 days; PDP conversion rate increased by `+29%`.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An automated review email fires `5 days after Order Placed`; because a shipment to Upper Egypt or Northern KSA took 6 days to arrive, the customer receives `'كيف كان المنتج؟ قيمه الآن!'` before receiving the parcel, prompting an angry 1-star review saying `'الطلب لم يصلني أصلاً!'`.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Trigger review requests **strictly off the Courier `DELIVERED` event (`+48 to 72 hours`)**, never off `Order Placed + X days`!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi E-Commerce Law, UAE Consumer Protection Law & Google Rich Results Review Schema Guidelines** | `supported` | [Official Docs](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) (`2026-10-25`) | Regional consumer laws prohibit fabricated reviews and false popularity indicators; Google Search Central also issues manual actions if `aggregateRating` JSON-LD is populated with non-genuine or scraped reviews. | If a brand-new product has `0` reviews yet, hide the star counter (`عرض: منتج جديد`) and highlight the official warranty and Saudi Business Center verification badge until the first 3 real buyer reviews arrive. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Verified-Buyer Review Submission Rate (`Target: >= 8–12%` of delivered orders via WhatsApp) and PDP Conversion Rate.
- **Baseline**: Count of genuine `order_id`-linked reviews.
- **Observation Window**: 28 days post-implementation.
- **Interpretation Boundary**: Authentic dialect reviews with real customer photos build high local trust, while product quality governs actual star ratings.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [False Discounts in Arab Markets: What Saudi, UAE and Egyptian Law Say Before White Friday](https://voctos.net/false-discount-advertising-law-arab-markets-white-friday/) — *VOCTOS* (Published `2026-10-22`, Accessed `2026-10-25`): Fake reference prices violate law across all 3 markets: KSA fines up to SAR 1,000,000 and requires a Ministry of Commerce discount license + old/new price tag; Egypt Law 181/2018 fines EGP 50,000 to EGP 2,000,000; UAE fines AED 100,000.
- [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) — *DigiStreet Media* (Published `2026-09-29`, Accessed `2026-10-25`): Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous.
