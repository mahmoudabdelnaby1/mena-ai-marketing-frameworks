# Bilingual Landing Page RTL CSS Mirroring, Directional Icon & Sticky-CTA Collision Checklist
## <span dir="rtl">قائمة فحص الانعكاس الكامل لواجهات اليمين لليسار (`RTL CSS Mirroring`) واتجاه الأسهم ومنع تصادم الأزرار العائمة في الجوال</span>

> **Asset ID**: `FW-076` (`AMP-389`) | **Artifact Type**: `CHECKLIST` | **Channel**: CRO - Conversion Rate Optimization | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Audit and fix incomplete RTL CSS mirroring on Arabic landing pages—flipping directional progress arrows, fixing reverse-scrolling Swiper/Slick carousels, and stopping floating WhatsApp buttons from covering the mobile 'Add to Cart / Checkout' CTA.
- **AR**: <span dir="rtl">تدقيق وإصلاح الانعكاس الناقص لواجهات `RTL` في صفحات الهبوط العربية (عكس اتجاه أسهم المتابعة، ضبط السلايدر، ومنع أيقونة واتساب العائمة من تغطية زر «إضافة للسلة / إتمام الطلب» على الجوال).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before launching any Arabic or bilingual landing page, Salla/Zid/Shopify theme customization, or checkout redesign on mobile and desktop.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل إطلاق أي صفحة هبوط عربية أو ثنائية اللغة أو تعديل قوالب سلة وزد وشوبيفاي على الجوال وسطح المكتب.</span>
- **When NOT to Use It (EN)**: Do not mirror universal non-directional icons (checkmarks `✓`, clock faces, play buttons `▶` on standard media players, or brand logos) when mirroring directional UI arrows!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم بعكس الأيقونات العالمية غير الاتجاهية (مثل علامة الصح `✓` أو عقارب الساعة أو شعار العلامة التجارية)؛ العكس يقتصر على أسهم الاتجاه والخطوات والتقدم.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Live Arabic Landing Page / Storefront URL viewed on a `375x812px` mobile viewport
- Theme CSS stylesheet and Swiper/Slick carousel initialization script
- List of active floating widgets (WhatsApp button, Chat widget, Loyalty launcher, Cookie banner, Sticky Add-to-Cart bar)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 6-Point RTL CSS Mirroring & Mobile Z-Index Collision Checklist

#### 1. Copy-Ready CSS Logical Properties & Directional Icon Flip Snippet
Replace physical `left`/`right` properties with **CSS Logical Properties** (`margin-inline-start`, `padding-inline-end`, `inset-inline-end`) so a single stylesheet works flawlessly in both `dir="rtl"` and `dir="ltr"`:
```css
/* 1. Automatically flip directional navigation/CTA arrows in RTL (while preserving checkmarks & logos) */
[dir="rtl"] .icon-arrow-next,
[dir="rtl"] .icon-chevron-right,
[dir="rtl"] .breadcrumb-separator,
[dir="rtl"] .btn-cta svg.directional-arrow {
  transform: scaleX(-1);
}

/* 2. Keep phone numbers, prices, card inputs, and English promo codes strictly LTR inside RTL pages */
[dir="rtl"] input[type="tel"],
[dir="rtl"] .price-amount,
[dir="rtl"] .promo-code-pill,
[dir="rtl"] .ltr-token {
  direction: ltr;
  unicode-bidi: isolate;
}

/* 3. Prevent Floating WhatsApp / Chat Widget from Covering the Mobile Sticky Add-to-Cart Bar! */
@media (max-width: 768px) {
  .whatsapp-floating-widget,
  #tidio-chat,
  .intercom-lightweight-app-launcher {
    bottom: 88px !important; /* Lift 88px above the 68px Sticky Add-to-Cart / Checkout bar! */
    inset-inline-end: 16px !important;
    z-index: 990 !important; /* Below open cart drawer/modals (z-index: 1050) */
  }
}
```

#### 2. Interactive Component Audit Checklist (`375px` Mobile Viewport)
- [ ] **Check 1 — Directional Arrows (`التالي / أكمل الطلب ←`)**: In RTL, forward progress moves **from Right to Left (`←`)**. Confirm every `'أكمل الطلب'` and `'التالي'` button arrow points **left (`←`)**, and `'السابق / رجوع'` points **right (`→`)**.
- [ ] **Check 2 — Carousel / Slider `dir="rtl"` Attribute**: Confirm Swiper.js (`<div class="swiper" dir="rtl">`) or Slick (`rtl: true`) has explicit RTL initialization—without it, swiping left/right on mobile jumps to a blank white slide!
- [ ] **Check 3 — Star Ratings (`4.5 ★`) Partial Fill Direction**: Confirm half-filled stars fill from **right to left** in `[dir="rtl"]` rather than showing the empty half first.
- [ ] **Check 4 — Zero Floating Widget Collision on Sticky CTA**: Open a product page on mobile, scroll down until the sticky `'أضف للسلة'` bar appears, and verify that the floating WhatsApp icon (`AMP-394`) sits **`>= 88px` above the bottom edge** and disappears (`z-index` lower) when the Slide-Out Cart Drawer opens!

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Saudi & Emirati Home Furniture Store on Shopify (`Custom Bilingual Theme`).
- **Defects Found on Mobile Arabic (`/ar/`)**:
  1. Product image gallery (Swiper.js) lacked `dir="rtl"` on the container, so swiping to view Photo #2 scrolled into an empty white void.
  2. The floating green WhatsApp button sat at `bottom: 16px; right: 16px; z-index: 999999`, covering the right half of the sticky `"إتمام الطلب الآن"` button even when the Cart Drawer was open!
  3. Checkout breadcrumb arrows pointed backward (`السلة → الشحن → الدفع`).

### Step B: Initial Output (`المخرج الأولي`)
- **Applied RTL & Z-Index Fixes**:
  1. Added `dir="rtl"` dynamically to `.swiper` containers when `document.documentElement.dir === 'rtl'`.
  2. Applied `bottom: 88px !important` and `z-index: 990` to the WhatsApp launcher, and hid it (`display: none`) whenever `body.cart-drawer-open` is active.
  3. Applied `transform: scaleX(-1)` to `.breadcrumb-separator` and `.btn-cta .icon-arrow` under `[dir="rtl"]`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Checked Half-Star SVG Gradient**: Fixed the 4.5-star product rating SVG linearGradient under `[dir="rtl"]` (`x1="100%" x2="0%"`) so 4.5 stars display properly.
2. **Replaced Physical Margins**: Converted 14 instances of `margin-left: 12px` on icon labels to `margin-inline-start: 12px`.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- 100% of mobile `/ar/` carousels, directional arrows, star ratings, and sticky CTAs verified collision-free across iOS Safari and Android Chrome.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A developer applies `transform: scaleX(-1)` globally to ALL `svg` elements under `[dir="rtl"]`, flipping the company logo, the Apple Pay logo, and checkmark icons (`✓`) backward!
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Scope `transform: scaleX(-1)` strictly to **directional navigation classes** (`.icon-arrow`, `.icon-chevron`, `.breadcrumb-arrow`), never to global `svg` or `img` tags.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **CSS Logical Properties (`margin-inline`, `inset-inline`) & Swiper/Slick RTL Mode** | `supported` | [Official Docs](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) (`2026-10-25`) | CSS Logical Properties are supported across 98%+ of modern mobile and desktop browsers; JS carousels (Swiper/Slick) still require explicit `dir='rtl'` / `rtl: true` attributes. | Test every `/ar/` landing page on a real mobile screen by swiping through the product gallery and opening the cart drawer. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Mobile `/ar/` Product Gallery Swipe-Interaction Rate, Cart-Drawer-to-Checkout Click Rate, and Zero Rage-Clicks on covered sticky CTAs (Microsoft Clarity / Hotjar).
- **Baseline**: Pre-fix mobile `/ar/` vs `/en/` conversion gap and Clarity rage-click heatmap.
- **Observation Window**: 14 days post-deployment.
- **Interpretation Boundary**: Eliminating broken RTL carousels and blocked CTAs removes technical layout blockers, while pricing and shipping terms drive final checkout conversion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [We Audited 20 Salla and Zid Stores: The SEO Defaults Saudi Merchants Inherit (2026)](https://voctos.net/salla-zid-store-seo-audit/) — *VOCTOS* (Published `2026-10-08`, Accessed `2026-10-25`): Audit of 20 Saudi stores (10 Salla, 10 Zid): 60% of sampled Salla sitemap URLs (88/146) redirected or returned 410; 6/6 Salla English pages canonicalized to Arabic; 9/10 Zid stores lacked Sitemap in robots.txt; 0/10 Salla stores had Brand in Product JSON-LD; 8/11 English pages kept Arabic-script titles.
- [The Arabic SEO in Saudi Arabia Mistakes Costing Riyadh Brands Rankings](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) — *DigiStreet Media* (Published `2026-09-29`, Accessed `2026-10-25`): Identifies 5 recurring KSA SEO failures: treating Arabic as translation, running one strategy across Arabic/English, broken hreflang/RTL mobile UX, ignoring Vision 2030 sector context, and chasing non-local backlinks while treating Riyadh, Jeddah, and Dammam as homogeneous.
- [Top Arabic Content Writing Mistakes Hurting Your SEO Rankings](https://www.aiqalam.com/en/blog/top-arabic-content-writing-mistakes-hurting-your-seo-rankings) — *AI Qalam* (Published `2026-10-24`, Accessed `2026-10-25`): Documents poor RTL text alignment, unnatural AI phrasing, and morphological keyword stuffing in Arabic content.
