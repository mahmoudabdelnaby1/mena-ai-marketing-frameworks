# KSA & UAE Above-the-Fold Tabby & Tamara BNPL Price-Split Widget Checklist
## <span dir="rtl">قائمة فحص وضع شارات تقسيط «تابي» و«تمارا» (`Tabby & Tamara`) بجوار السعر مباشرة أعلى طية صفحة المنتج في السعودية والإمارات</span>

> **Asset ID**: `FW-074` (`AMP-387`) | **Artifact Type**: `CHECKLIST` | **Channel**: CRO - Conversion Rate Optimization | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Place dynamic Tabby and Tamara 4-installment price calculators (`'أو 4 دفعات بقيمة 74.75 ر.س بدون فوائد أو رسوم'`) immediately beneath the product price above the fold on mobile PDPs in KSA and UAE.
- **AR**: <span dir="rtl">إظهار حاسبة الدفعات الأربع لـ «تابي» و«تمارا» (`أو قسّمها على 4 دفعات بقيمة X ر.س/د.إ بدون فوائد`) مباشرة تحت سعر المنتج أعلى طية شاشة الجوال في السعودية والإمارات.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use on every Product Detail Page (PDP), Slide-Out Cart Drawer, and Landing Page in Saudi Arabia, UAE, Kuwait, and Qatar where AOV is `>= 100 SAR / 100 AED`.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم في جميع صفحات المنتجات (`PDP`) وسلة التسوق الجانبية وصفحات الهبوط في السعودية والإمارات والكويت وقطر للمنتجات التي تزيد عن 100 ريال/درهم.</span>
- **When NOT to Use It (EN)**: Do not display static image screenshots of Tabby/Tamara that show a fixed or wrong installment number when the shopper switches product size/variant price!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تضع صورة ثابتة لتابي وتمارا تعرض رقماً خاطئاً عند تغيير مقاس أو خيار المنتج؛ استخدم الودجت الديناميكي الذي يقسم السعر الفعلي على 4 تلقائياً.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Mobile Product Detail Page (`PDP`) above-the-fold layout (`375x812px` iPhone viewport)
- Official Tabby Promo Snippet & Tamara Product Widget script (or Salla/Zid native BNPL widget toggle)
- Store currency (`SAR`, `AED`, `KWD`, `QAR`) and minimum/maximum eligible order thresholds

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Above-the-Fold Tabby & Tamara PDP Placement Checklist

#### 1. Mobile Viewport (`375x812px`) Vertical Hierarchy Contract
On mobile (70%+ of KSA/UAE traffic), the shopper MUST see these 4 elements **without scrolling** (or within the first swipe beneath the hero image):
1. **Product Title (`H1`) & Star Rating**
2. **Full Tax-Inclusive Price**: e.g., `<bdi>399.00 ر.س</bdi> شامل ضريبة القيمة المضافة`
3. **Dynamic Tabby & Tamara 4-Payment Breakdown (`IMMEDIATELY BELOW PRICE — MAX 12px MARGIN`)**:
   - `"أو قسّمها على 4 دفعات شهرية بقيمة 99.75 ر.س بدون فوائد أو رسوم تأخير عبر [شعار تابي] و [شعار تمارا] — متوافق مع الشريعة الإسلامية"`
4. **Primary Sticky CTA Button (`أضف إلى السلة / اشترِ الآن عبر Apple Pay أو مدى`)**

#### 2. Copy-Ready RTL Dynamic Installment Widget Snippet (Shopify Liquid / Salla Custom HTML)
```html
<!-- Dynamic RTL Tabby & Tamara Installment Box (Places price / 4 directly below main price) -->
<div dir="rtl" class="mena-bnpl-box" style="margin:10px 0 16px 0; padding:10px 14px; background:#F8FAFC; border:1px solid #E2E8F0; border-radius:8px; direction:rtl; text-align:right; font-family:'Tajawal','Cairo',sans-serif; font-size:14px; line-height:1.6; color:#1E293B;">
  <span>أو قسّمها على <strong>4 دفعات</strong> بقيمة </span>
  <bdi id="bnpl-installment-amount" style="font-weight:700; color:#0F172A;">
    {{ product.selected_or_first_available_variant.price | divided_by: 4.0 | money }}
  </bdi>
  <span>/شهرياً بدون فوائد أو رسوم مع </span>
  <strong style="background:#3BFFB3; color:#000; padding:1px 6px; border-radius:4px; font-size:12px;">tabby</strong>
  <span> أو </span>
  <strong style="background:#F3E8FF; color:#4C1D95; padding:1px 6px; border-radius:4px; font-size:12px;">تمارا</strong>
</div>
```

#### 3. Verification Checklist
- [ ] **Check 1 — Variant Change Listener**: Confirm that when a shopper clicks a larger size or bundle variant (`e.g., 100ml at 399 SAR -> 200ml at 599 SAR`), `#bnpl-installment-amount` updates dynamically from `99.75 ر.س` to `149.75 ر.س`.
- [ ] **Check 2 — Cart Drawer Upsell Bar**: In the slide-out cart drawer, display `"أنت مؤهل لتقسيط سلتك على 4 دفعات بقيمة [Cart_Total / 4] ر.س اليوم!"` right above the Checkout button.

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Dubai & Riyadh Luxury Eyewear & Watches Store on Shopify (`AOV: 680 AED / 700 SAR`).
- **Problem**: Tabby and Tamara were active at the final checkout payment step, but on the Product Detail Page (PDP), the AI-designed landing page template only showed `700 SAR` at the top and buried small greyscale payment icons at the very bottom footer (`Y: 4200px`).

### Step B: Initial Output (`المخرج الأولي`)
- **PDP & Cart Drawer Fix**:
  1. Placed the dynamic RTL Tabby & Tamara 4-payment box (`"أو قسّمها على 4 دفعات بقيمة 175.00 ر.س بدون فوائد"`) `8px` directly beneath the `700.00 ر.س` price tag above the fold.
  2. Added the interactive modal explaining `"ادفع 25% اليوم (175 ر.س) والباقي على 3 أشهر بدون أي رسوم"`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Sharia-Compliance Reassurance**: Included the official Tabby/Tamara note (`"متوافق مع أحكام الشريعة الإسلامية — بدون فوائد"`) inside the info tooltip, which resolves the #1 hesitation among Saudi shoppers.
2. **Checked Salla Native Toggle**: For the brand's Salla KSA sub-store, verified that `إعدادات الدفع -> إظهار بنر تابي وتمارا في صفحة المنتج` was toggled ON and styled above the fold.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Above-the-fold dynamic BNPL price-split widget live across 100% of PDPs and the slide-out cart drawer in KSA and UAE.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A developer hard-codes `/ 4` integer division in Liquid (`divided_by: 4` instead of `divided_by: 4.0`), causing rounding truncation on odd prices, or displays the Tabby widget on a `25 SAR` accessory that is below the merchant's minimum BNPL cart threshold (`e.g., 100 SAR`), leading to a declined option at checkout.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Wrap the BNPL widget in an eligibility threshold check (`{% if product.price >= 10000 %}` in cents/halalas) and for items under `100 SAR`, display `"أضف منتجات بقيمة [100 - price] ر.س لتفعيل التقسيط على 4 دفعات عبر تابي وتمارا"`!

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Tabby & Tamara Official On-Site Messaging Widgets (Salla, Zid, Shopify, WooCommerce)** | `supported` | [Official Docs](https://www.huptechweb.com/blogs/tabby-vs-tamara-shopify-uae-bnpl-2026) (`2026-10-25`) | Huptech and Soluvide 2026 UAE/KSA CRO studies confirm ~14% BNPL checkout share and highlight PDP above-the-fold installment visibility as a primary conversion and AOV driver. | If third-party widget JS slows down mobile LCP (`AMP-393`), use the lightweight zero-JS Liquid/HTML box above and lazy-load the modal script on click. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: PDP Add-to-Cart Rate (`%`), BNPL Share of Checkout (`%`), and Average Order Value (`AOV`) on BNPL orders vs. single-payment orders.
- **Baseline**: Prior 14-day Add-to-Cart rate and BNPL share when widget was below the fold.
- **Observation Window**: 14–28 days (covering both pre-payday and post-payday weeks `AMP-391`).
- **Interpretation Boundary**: Above-the-fold BNPL visibility reduces price friction on the PDP, especially during the mid-month pre-salary window (10th–24th of the month).

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Conversion Rate Optimization for UAE E-Commerce (2026)](https://soluvide.com/blog/conversion-rate-optimization-uae-ecommerce-2026) — *Soluvide* (Published `2026-02-19`, Accessed `2026-10-25`): Shows how Cash on Delivery (COD) and Buy Now Pay Later (Tabby and Tamara) reduce checkout friction and lift AOV in UAE/GCC e-commerce.
- [Tabby vs Tamara Shopify UAE 2026: BNPL Comparison](https://www.huptechweb.com/blogs/tabby-vs-tamara-shopify-uae-bnpl-2026) — *Huptech Web* (Published `2026-06-25`, Accessed `2026-10-25`): Documents BNPL representing ~14% of UAE e-commerce checkout and compares Tabby vs Tamara placement, approval behavior, and merchant fees on Shopify.
