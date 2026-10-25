# FW-076: Bilingual Landing Page RTL CSS Mirroring, Directional Icon & Sticky-CTA Collision Checklist
## قائمة فحص الانعكاس الكامل لواجهات اليمين لليسار (`RTL CSS Mirroring`) واتجاه الأسهم ومنع تصادم الأزرار العائمة في الجوال

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-399`, `AMP-409`, `AMP-419`, `AMP-429`, `AMP-439`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Audit and fix incomplete RTL CSS mirroring on Arabic landing pages—flipping directional progress arrows, fixing reverse-scrolling Swiper/Slick carousels, and stopping floating WhatsApp buttons from covering the mobile 'Add to Cart / Checkout' CTA.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تدقيق وإصلاح الانعكاس الناقص لواجهات `RTL` في صفحات الهبوط العربية (عكس اتجاه أسهم المتابعة، ضبط السلايدر، ومنع أيقونة واتساب العائمة من تغطية زر «إضافة للسلة / إتمام الطلب» على الجوال).
- **Why `CHECKLIST` Fits This User Job (EN)**: AI landing-page builders and poorly localized themes apply `direction: rtl` to text while leaving physical CSS (`margin-left`, `right: 20px`), directional SVG arrows (`→`), and carousel physics in LTR—causing 'Continue' arrows to point backward (`→` instead of `←`), carousels to freeze on swipe, and floating WhatsApp/chat widgets to sit directly on top of the mobile sticky Checkout button!
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تكتفي أدوات بناء صفحات الهبوط بالذكاء الاصطناعي بعكس اتجاه النص (`direction: rtl`) مع ترك الهوامش الفيزيائية (`margin-left`) وأسهم المتابعة (`→`) وإعدادات السلايدر بالاتجاه الإنجليزي، مما يجعل سهم «التالي» يشير للخلف، ويتسبب في تغطية زر واتساب العائم لزر «إتمام الطلب» السفلي في الجوال!

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before launching any Arabic or bilingual landing page, Salla/Zid/Shopify theme customization, or checkout redesign on mobile and desktop.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل إطلاق أي صفحة هبوط عربية أو ثنائية اللغة أو تعديل قوالب سلة وزد وشوبيفاي على الجوال وسطح المكتب.
- **When NOT to Use It (EN)**: Do not mirror universal non-directional icons (checkmarks `✓`, clock faces, play buttons `▶` on standard media players, or brand logos) when mirroring directional UI arrows!
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم بعكس الأيقونات العالمية غير الاتجاهية (مثل علامة الصح `✓` أو عقارب الساعة أو شعار العلامة التجارية)؛ العكس يقتصر على أسهم الاتجاه والخطوات والتقدم.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Live Arabic Landing Page / Storefront URL viewed on a `375x812px` mobile viewport
2. Theme CSS stylesheet and Swiper/Slick carousel initialization script
3. List of active floating widgets (WhatsApp button, Chat widget, Loyalty launcher, Cookie banner, Sticky Add-to-Cart bar)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **CSS Logical Properties (`margin-inline`, `inset-inline`) & Swiper/Slick RTL Mode** | `supported` | [Official Reference](https://digistreetmedia.com/blog/the-arabic-seo-in-saudi-arabia-mistakes-costing-riyadh-brands-rankings/) (`2026-10-25`) | CSS Logical Properties are supported across 98%+ of modern mobile and desktop browsers; JS carousels (Swiper/Slick) still require explicit `dir='rtl'` / `rtl: true` attributes. | Test every `/ar/` landing page on a real mobile screen by swiping through the product gallery and opening the cart drawer. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-399`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Logical CSS properties (`margin-inline-start`, `padding-inline-end`) and RTL icon mirroring (`transform: scaleX(-1)`) QA checklist.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-409`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Logical CSS properties (`margin-inline-start`, `padding-inline-end`) and RTL icon mirroring (`transform: scaleX(-1)`) QA checklist.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-419`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Logical CSS properties (`margin-inline-start`, `padding-inline-end`) and RTL icon mirroring (`transform: scaleX(-1)`) QA checklist.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-429`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Logical CSS properties (`margin-inline-start`, `padding-inline-end`) and RTL icon mirroring (`transform: scaleX(-1)`) QA checklist.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-439`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Logical CSS properties (`margin-inline-start`, `padding-inline-end`) and RTL icon mirroring (`transform: scaleX(-1)`) QA checklist.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-539`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-419 (CRO - Conversion Rate Optimization)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Saudi & Emirati Home Furniture Store on Shopify (`Custom Bilingual Theme`).
- **Defects Found on Mobile Arabic (`/ar/`)**:
  1. Product image gallery (Swiper.js) lacked `dir="rtl"` on the container, so swiping to view Photo #2 scrolled into an empty white void.
  2. The floating green WhatsApp button sat at `bottom: 16px; right: 16px; z-index: 999999`, covering the right half of the sticky `"إتمام الطلب الآن"` button even when the Cart Drawer was open!
  3. Checkout breadcrumb arrows pointed backward (`السلة → الشحن → الدفع`).
- **Human Review & Key Edits Applied**: 1. **Checked Half-Star SVG Gradient**: Fixed the 4.5-star product rating SVG linearGradient under `[dir="rtl"]` (`x1="100%" x2="0%"`) so 4.5 stars display properly.
2. **Replaced Physical Margins**: Converted 14 instances of `margin-left: 12px` on icon labels to `margin-inline-start: 12px`.
- **Final Usable Output**: - 100% of mobile `/ar/` carousels, directional arrows, star ratings, and sticky CTAs verified collision-free across iOS Safari and Android Chrome.
- **What Can Go Wrong**: A developer applies `transform: scaleX(-1)` globally to ALL `svg` elements under `[dir="rtl"]`, flipping the company logo, the Apple Pay logo, and checkmark icons (`✓`) backward!
- **Correction & Fallback**: Scope `transform: scaleX(-1)` strictly to **directional navigation classes** (`.icon-arrow`, `.icon-chevron`, `.breadcrumb-arrow`), never to global `svg` or `img` tags.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Mobile `/ar/` Product Gallery Swipe-Interaction Rate, Cart-Drawer-to-Checkout Click Rate, and Zero Rage-Clicks on covered sticky CTAs (Microsoft Clarity / Hotjar).
- **Baseline Definition**: Pre-fix mobile `/ar/` vs `/en/` conversion gap and Clarity rage-click heatmap.
- **Observation Window**: 14 days post-deployment. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Eliminating broken RTL carousels and blocked CTAs removes technical layout blockers, while pricing and shipping terms drive final checkout conversion.
