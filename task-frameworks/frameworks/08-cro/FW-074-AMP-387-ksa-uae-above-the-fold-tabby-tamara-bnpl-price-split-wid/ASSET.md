# FW-074: KSA & UAE Above-the-Fold Tabby & Tamara BNPL Price-Split Widget Checklist
## قائمة فحص وضع شارات تقسيط «تابي» و«تمارا» (`Tabby & Tamara`) بجوار السعر مباشرة أعلى طية صفحة المنتج في السعودية والإمارات

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-397`, `AMP-407`, `AMP-417`, `AMP-427`, `AMP-437`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Place dynamic Tabby and Tamara 4-installment price calculators (`'أو 4 دفعات بقيمة 74.75 ر.س بدون فوائد أو رسوم'`) immediately beneath the product price above the fold on mobile PDPs in KSA and UAE.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إظهار حاسبة الدفعات الأربع لـ «تابي» و«تمارا» (`أو قسّمها على 4 دفعات بقيمة X ر.س/د.إ بدون فوائد`) مباشرة تحت سعر المنتج أعلى طية شاشة الجوال في السعودية والإمارات.
- **Why `CHECKLIST` Fits This User Job (EN)**: Huptech and Soluvide 2026 UAE/KSA CRO studies confirm that BNPL (Tabby & Tamara) accounts for ~14%+ of UAE/KSA Shopify checkout volume and significantly increases AOV, yet AI-generated landing pages and default themes hide BNPL logos in the page footer or only reveal them on the final payment step—after the shopper already bounced from sticker shock on the Product Detail Page (PDP)!
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تثبت دراسات تحسين التحويل في الإمارات والسعودية (2026) أن الدفع الآجل عبر «تابي» و«تمارا» يمثل نحو 14%+ من المدفوعات ويرفع متوسط السلة، لكن القوالب الافتراضية تخفي الشارات في تذييل الموقع أو في الخطوة الأخيرة للدفع بعد أن يغادر المتسوق صفحة المنتج بسبب صدمة السعر الكلي!

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use on every Product Detail Page (PDP), Slide-Out Cart Drawer, and Landing Page in Saudi Arabia, UAE, Kuwait, and Qatar where AOV is `>= 100 SAR / 100 AED`.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم في جميع صفحات المنتجات (`PDP`) وسلة التسوق الجانبية وصفحات الهبوط في السعودية والإمارات والكويت وقطر للمنتجات التي تزيد عن 100 ريال/درهم.
- **When NOT to Use It (EN)**: Do not display static image screenshots of Tabby/Tamara that show a fixed or wrong installment number when the shopper switches product size/variant price!
- **متى لا تستخدم هذه الأداة (AR)**: لا تضع صورة ثابتة لتابي وتمارا تعرض رقماً خاطئاً عند تغيير مقاس أو خيار المنتج؛ استخدم الودجت الديناميكي الذي يقسم السعر الفعلي على 4 تلقائياً.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Mobile Product Detail Page (`PDP`) above-the-fold layout (`375x812px` iPhone viewport)
2. Official Tabby Promo Snippet & Tamara Product Widget script (or Salla/Zid native BNPL widget toggle)
3. Store currency (`SAR`, `AED`, `KWD`, `QAR`) and minimum/maximum eligible order thresholds

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Tabby & Tamara Official On-Site Messaging Widgets (Salla, Zid, Shopify, WooCommerce)** | `supported` | [Official Reference](https://www.huptechweb.com/blogs/tabby-vs-tamara-shopify-uae-bnpl-2026) (`2026-10-25`) | Huptech and Soluvide 2026 UAE/KSA CRO studies confirm ~14% BNPL checkout share and highlight PDP above-the-fold installment visibility as a primary conversion and AOV driver. | If third-party widget JS slows down mobile LCP (`AMP-393`), use the lightweight zero-JS Liquid/HTML box above and lazy-load the modal script on click. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-397`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Placing dynamic Tabby/Tamara installment calculation badges directly below the primary price on PDPs and cart drawers.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-407`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Placing dynamic Tabby/Tamara installment calculation badges directly below the primary price on PDPs and cart drawers.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-417`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Placing dynamic Tabby/Tamara installment calculation badges directly below the primary price on PDPs and cart drawers.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-427`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Placing dynamic Tabby/Tamara installment calculation badges directly below the primary price on PDPs and cart drawers.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-437`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Placing dynamic Tabby/Tamara installment calculation badges directly below the primary price on PDPs and cart drawers.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-537`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-397 (CRO - Conversion Rate Optimization)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Dubai & Riyadh Luxury Eyewear & Watches Store on Shopify (`AOV: 680 AED / 700 SAR`).
- **Problem**: Tabby and Tamara were active at the final checkout payment step, but on the Product Detail Page (PDP), the AI-designed landing page template only showed `700 SAR` at the top and buried small greyscale payment icons at the very bottom footer (`Y: 4200px`).
- **Human Review & Key Edits Applied**: 1. **Sharia-Compliance Reassurance**: Included the official Tabby/Tamara note (`"متوافق مع أحكام الشريعة الإسلامية — بدون فوائد"`) inside the info tooltip, which resolves the #1 hesitation among Saudi shoppers.
2. **Checked Salla Native Toggle**: For the brand's Salla KSA sub-store, verified that `إعدادات الدفع -> إظهار بنر تابي وتمارا في صفحة المنتج` was toggled ON and styled above the fold.
- **Final Usable Output**: - Above-the-fold dynamic BNPL price-split widget live across 100% of PDPs and the slide-out cart drawer in KSA and UAE.
- **What Can Go Wrong**: A developer hard-codes `/ 4` integer division in Liquid (`divided_by: 4` instead of `divided_by: 4.0`), causing rounding truncation on odd prices, or displays the Tabby widget on a `25 SAR` accessory that is below the merchant's minimum BNPL cart threshold (`e.g., 100 SAR`), leading to a declined option at checkout.
- **Correction & Fallback**: Wrap the BNPL widget in an eligibility threshold check (`{% if product.price >= 10000 %}` in cents/halalas) and for items under `100 SAR`, display `"أضف منتجات بقيمة [100 - price] ر.س لتفعيل التقسيط على 4 دفعات عبر تابي وتمارا"`!

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: PDP Add-to-Cart Rate (`%`), BNPL Share of Checkout (`%`), and Average Order Value (`AOV`) on BNPL orders vs. single-payment orders.
- **Baseline Definition**: Prior 14-day Add-to-Cart rate and BNPL share when widget was below the fold.
- **Observation Window**: 14–28 days (covering both pre-payday and post-payday weeks `AMP-391`). *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Above-the-fold BNPL visibility reduces price friction on the PDP, especially during the mid-month pre-salary window (10th–24th of the month).
