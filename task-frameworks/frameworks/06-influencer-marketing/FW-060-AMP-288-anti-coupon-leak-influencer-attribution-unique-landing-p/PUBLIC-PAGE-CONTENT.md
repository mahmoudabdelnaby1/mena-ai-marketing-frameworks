# Anti-Coupon-Leak Influencer Attribution & Unique Landing-Page / Cart-Link Workflow
## <span dir="rtl">مسار عمل قياس عائد المؤثرين ومنع تسرب أكواد الخصم الثابتة (`Promo Code Cannibalization`) لزيارات الدفع العضوية</span>

> **Asset ID**: `FW-060` (`AMP-288`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Influencer Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent browser coupon extensions and Telegram/WhatsApp coupon groups from hijacking static influencer promo codes (`AHMED10`) at checkout—stopping AI attribution models from over-crediting creators for organic sales they didn't drive.
- **AR**: <span dir="rtl">منع إضافات المتصفح ومجموعات الكوبونات من سرقة أكواد خصم المؤثرين الثابتة وتطبيقها على المتسوقين العضويين عند الدفع، وضمان قياس المبيعات الحقيقية التي جلبها المؤثر فعلياً.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever issuing promo codes or affiliate links to influencers in KSA, UAE, or Egypt on Salla, Zid, Shopify, WooCommerce, or custom apps.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إصدار أكواد خصم أو روابط إحالة للمؤثرين على سلة أو زد أو شوبيفاي أو ووكومرس في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Never pay creator commission or evaluate influencer ROAS on `Total Orders Using Promo Code X` without splitting `Click-Verified Influencer Sessions` vs. `Zero-Click Checkout Code Paste`.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم أبداً بحساب عمولة المؤثر أو تقييم عائده الإعلاني بناءً على «إجمالي الطلبات التي استخدمت الكود» دون فصل «الزيارات القادمة فعلياً من رابط المؤثر» عن «لصق الكود في صفحة الدفع من زوار محركات البحث».</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Storefront Auto-Apply Discount URL structure (e.g., `https://store.sa/discount/SARA15?redirect=/collections/best&utm_source=snapchat&utm_medium=influencer&utm_campaign=sara_oct26`)
- GA4 / Backend Order Attribution Table (`first_user_source_medium`, `session_source_medium`, `coupon_code`, `time_from_landing_to_checkout`)
- Creator Burst Window (`48–72 hours` post-story)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Saudi Footwear & Sportswear Store on Salla/Shopify.
- **Problem**: Paid Creator X a `15%` commission on `410` orders that used code `FAHAD15` over 30 days. Forensic GA4 + backend audit revealed only `95` orders (`23%`) occurred during the 72-hour story burst or carried `utm_medium=influencer`; the other `315` orders (`77%`) happened weeks later from shoppers who were already on the checkout page, opened Google to search `"كود خصم متجر ..."`, found `FAHAD15` on a coupon site, and pasted it!

### Step B: Initial Output (`المخرج الأولي`)
- **Attribution Reconciliation**:
  - `TIER_A_VERIFIED_CREATOR_DRIVEN`: `68` orders (`100%` credit)
  - `TIER_B_VIEW_THROUGH_PROBABLE` (within 72h burst): `27` orders (`50%` credit)
  - `TIER_C_COUPON_SCRAPER_CANNIBALIZATION` (after 72h / coupon site referrer): `315` orders (`0%` creator credit; code rotated/expired after 72h!).

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Updated Creator Contract Commission Clause**: Defined commission-eligible orders strictly as orders placed via the tracked link or using the burst code **within 72 hours of story publication**.
2. **Launched `/ar/offers` Branded Coupon Page**: Captured `"كود خصم [اسم المتجر]"` searchers with a `5%` first-order code instead of leaking `15%` creator codes.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Stopped `77%` coupon-scraper commission overpayment and locked all creator codes to 72-hour burst windows with auto-applied UTM deep links.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A creator refuses to use a link sticker and only says the promo code verbally on Snapchat; because Snapchat viewers open Safari/Chrome manually and type the store name on Google, 100% of their legitimate orders arrive as `google / organic` in GA4.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: That is exactly why `classify_influencer_order()` includes **`TIER_B_VIEW_THROUGH_PROBABLE`**: for verbal-only Snapchat/TikTok posts, measure the **72-hour incremental lift in branded organic + direct orders using the burst code** compared to the prior 7-day baseline, and immediately expire the code at Hour 72 so coupon sites cannot harvest it later.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Salla, Zid & Shopify Discount Code Expiration Scheduling & Auto-Apply URLs** | `supported` | [Official Docs](https://voctos.net/ga4-ai-traffic-arab-markets/) (`2026-10-25`) | All major MENA e-commerce platforms support start/end timestamps on coupon codes and URL-parameter discount auto-application. | Always set an explicit end date (`+72 hours` from post time) when creating any influencer promo code. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Incremental Creator ROAS (`(Tier_A_Revenue + 0.5 * Tier_B_Revenue) / Creator_Fee`) and Reduction in Unattributed Coupon Discount Leakage (`%`).
- **Baseline**: Prior 30-day raw promo-code order count vs. UTM-verified + 72h burst order count.
- **Observation Window**: 72 hours post-creator activation.
- **Interpretation Boundary**: Separating burst/UTM orders from late coupon-scraper usage prevents overpaying for cannibalized organic traffic.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) — *VOCTOS* (Published `2026-10-18`, Accessed `2026-10-25`): GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral.
- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
