# End-to-End Worked Example & Failure Recovery — `FW-076` (`AMP-389`)

- **Framework**: Bilingual Landing Page RTL CSS Mirroring, Directional Icon & Sticky-CTA Collision Checklist
- **العنوان بالعربية**: قائمة فحص الانعكاس الكامل لواجهات اليمين لليسار (`RTL CSS Mirroring`) واتجاه الأسهم ومنع تصادم الأزرار العائمة في الجوال
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Saudi & Emirati Home Furniture Store on Shopify (`Custom Bilingual Theme`).
- **Defects Found on Mobile Arabic (`/ar/`)**:
  1. Product image gallery (Swiper.js) lacked `dir="rtl"` on the container, so swiping to view Photo #2 scrolled into an empty white void.
  2. The floating green WhatsApp button sat at `bottom: 16px; right: 16px; z-index: 999999`, covering the right half of the sticky `"إتمام الطلب الآن"` button even when the Cart Drawer was open!
  3. Checkout breadcrumb arrows pointed backward (`السلة → الشحن → الدفع`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Applied RTL & Z-Index Fixes**:
  1. Added `dir="rtl"` dynamically to `.swiper` containers when `document.documentElement.dir === 'rtl'`.
  2. Applied `bottom: 88px !important` and `z-index: 990` to the WhatsApp launcher, and hid it (`display: none`) whenever `body.cart-drawer-open` is active.
  3. Applied `transform: scaleX(-1)` to `.breadcrumb-separator` and `.btn-cta .icon-arrow` under `[dir="rtl"]`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Checked Half-Star SVG Gradient**: Fixed the 4.5-star product rating SVG linearGradient under `[dir="rtl"]` (`x1="100%" x2="0%"`) so 4.5 stars display properly.
2. **Replaced Physical Margins**: Converted 14 instances of `margin-left: 12px` on icon labels to `margin-inline-start: 12px`.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- 100% of mobile `/ar/` carousels, directional arrows, star ratings, and sticky CTAs verified collision-free across iOS Safari and Android Chrome.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A developer applies `transform: scaleX(-1)` globally to ALL `svg` elements under `[dir="rtl"]`, flipping the company logo, the Apple Pay logo, and checkmark icons (`✓`) backward!
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Scope `transform: scaleX(-1)` strictly to **directional navigation classes** (`.icon-arrow`, `.icon-chevron`, `.breadcrumb-arrow`), never to global `svg` or `img` tags.
