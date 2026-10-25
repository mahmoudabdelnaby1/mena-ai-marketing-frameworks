# GA4 MENA Marketplace & E-Commerce Referral Reclassification Checklist (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`)
## <span dir="rtl">قائمة فحص إعادة تصنيف المتاجر والأسواق العربية (`amazon.sa`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`) في `GA4` بدلاً من ضياعها في `Referral`</span>

> **Asset ID**: `FW-086` (`AMP-444`) | **Artifact Type**: `CHECKLIST` | **Channel**: Marketing Automation | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Rescue traffic from `amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, `haraj.com.sa`, `dubizzle`, and `instashop` that Google's 819-domain default GA4 source list misclassifies as generic `Referral` instead of `Shopping`.
- **AR**: <span dir="rtl">إنقاذ الزيارات القادمة من منصات التجارة العربية (`amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, `zid.sa`, `حراج`, `دوبيزل`) التي تصنفها قائمة جوجل الافتراضية في `GA4` كإحالات عادية (`Referral`) بدلاً من قنوات التسوق (`Shopping`).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when auditing GA4 properties for any brand, marketplace seller, or e-commerce store operating in Saudi Arabia, UAE, or Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند ضبط أو تدقيق حساب `GA4` لأي علامة تجارية أو متجر إلكتروني يعمل في السعودية أو الإمارات أو مصر.</span>
- **When NOT to Use It (EN)**: Be careful to distinguish **External Regional Marketplaces** (which belong in `Organic Shopping` / `Paid Shopping`) from **Your Own Storefront Checkout/Payment Domains** (`salla.sa`, `zid.sa`, `tabby.ai`, `tamara.co`, `paymob.com` — which belong in **`List Unwanted Referrals`** so they don't overwrite the original ad source!).
- **متى لا تستخدمها (AR)**: <span dir="rtl">انتبه للتفريق الحاسم بين: (1) **الأسواق الخارجية** (`amazon.sa / noon.com / haraj.com.sa`) التي تضاف لقناة `Shopping`، وبين (2) **نطاقات الدفع وإتمام الطلب الخاصة بمتجرك** (`salla.sa / tabby.ai / tamara.co / paymob.com`) التي يجب إضافتها لقائمة **`Unwanted Referrals`** لمنع مسح مصدر الإعلان الأصلي!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- GA4 Admin access (`Data Streams -> Configure tag settings -> List unwanted referrals` AND `Data display -> Channel groups`)
- List of active payment gateways (`Tabby`, `Tamara`, `Moyasar`, `HyperPay`, `Tap`, `Paymob`, `Fawry`, `Kashier`) and storefront domains

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Riyadh & Cairo Beauty Brand selling D2C on its own site (with Tabby, Tamara, and Paymob) AND linking from brand store pages/campaigns on `amazon.sa`, `noon.com`, and `niceonesa.com`.
- **Audit Findings Before Fix**:
  1. `38%` of all paid conversions in GA4 were attributed to `tabby.ai / referral`, `tamara.co / referral`, and `accept.paymob.com / referral` (destroying paid ad ROAS visibility!).
  2. Traffic arriving from `amazon.sa`, `amazon.eg`, and `noon.com` was buried inside generic `Referral` instead of `Shopping`.

### Step B: Initial Output (`المخرج الأولي`)
- **Applied Part 1 & Part 2 Configurations**:
  1. Added all 16 MENA payment/BNPL gateways (`tabby.ai`, `tamara.co`, `paymob.com`, `moyasar.com`, etc.) to `List Unwanted Referrals` (`_gl` session continuity preserved).
  2. Added the MENA Marketplace Regex to `Organic Shopping` and `Paid Shopping` in the Custom Channel Group above `Referral`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified `ignore_referrer=true` on Payment Return**: Confirmed in GA4 DebugView that completing a test order via Tabby and Paymob preserves the original `utm_source=meta / utm_medium=paid_social` session instead of starting a new `referral` session.
2. **Retroactive Verification**: Confirmed historical `amazon.sa` and `noon.com` sessions moved cleanly from `Referral` into `Organic/Paid Shopping`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Eliminated payment-gateway self-referral hijacking (`38%` of revenue restored to true acquisition channels) and classified all MENA marketplaces (`Amazon.sa/.ae/.eg`, `Noon`, `NiceOne`, `Haraj`, `B.TECH`) under `Shopping`.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An analyst puts `salla.sa` into the `Organic Shopping` Channel Group rule on a store whose own checkout is hosted on a `salla.sa` subdomain WITHOUT adding `salla.sa` to `Unwanted Referrals`—causing every checkout redirect to be counted as a new 'Organic Shopping' session!
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always complete **Part 1 (`List Unwanted Referrals`) FIRST** for your own store/checkout/payment domains, and reserve **Part 2 (`Shopping` Channel Regex)** for external third-party marketplaces where users discover your brand.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Google Analytics 4 Default Source Categories PDF (819 Domains) vs. Unwanted Referrals & Custom Channel Groups** | `supported` | [Official Docs](https://voctos.net/ga4-ai-traffic-arab-markets/) (`2026-10-25`) | VOCTOS Oct 2026 audit of Google's 819-entry GA4 source category list proved that `amazon.sa`, `amazon.ae`, `amazon.eg`, `noon.com`, `salla.sa`, and `zid.sa` are absent from Google's default list. | Maintain the custom MENA Shopping Regex in GA4 Channel Groups and the MENA Payment Gateway list in Unwanted Referrals. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero revenue attributed to payment gateways (`tabby.ai / tamara.co / paymob.com / moyasar.com`) in GA4 `Session source / medium`, and accurate `Shopping` channel reporting for regional marketplaces.
- **Baseline**: Percentage of GA4 revenue previously hijacked by payment gateway referrals.
- **Observation Window**: 7 days post-deployment for `Unwanted Referrals` (forward-looking) + immediate retroactive reclassification for Custom Channel Groups.
- **Interpretation Boundary**: Fixing referral exclusion restores true first/last-click acquisition credit in GA4; pair with Server CAPI (`AMP-067`) for in-platform ad optimization.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Amazon.sa and noon SEO in 2026: How Product Search Works on Saudi and UAE Marketplaces](https://voctos.net/amazon-sa-noon-seo-guide/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Amazon.sa enforces a 75-character title rule (June/July 2026) and a <250-byte hidden keyword limit where UTF-8 Arabic letters consume 2 bytes each (~26 Arabic words max vs ~54 Latin); Noon requires English in KSA/UAE but hides English-only listings on its Arabic site; GA4 misclassifies amazon.sa and noon.com into Referral.
- [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) — *VOCTOS* (Published `2026-10-18`, Accessed `2026-10-25`): GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral.
