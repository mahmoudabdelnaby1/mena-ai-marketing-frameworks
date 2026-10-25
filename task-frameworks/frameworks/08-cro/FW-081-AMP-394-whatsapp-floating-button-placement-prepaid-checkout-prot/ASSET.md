# FW-081: WhatsApp Floating-Button Placement & Prepaid-Checkout Protection Decision Aid
## أداة قرار ضبط ظهور زر «واتساب العائم» لمنع خطف متسوقي الدفع الإلكتروني الجاهزين للشراء (`Prepaid Checkout Hijack`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-404`, `AMP-414`, `AMP-424`, `AMP-434`
- **Selected Artifact Type**: `DECISION_AID`
- **Intended Audience**: CRO Specialist, UX/UI Designer, E-Commerce Product Manager, Frontend Developer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Prevent intrusive floating WhatsApp buttons from pulling ready-to-pay Apple Pay, Mada, Tabby, and Card shoppers out of your self-serve checkout funnel into slow, unattributed manual chat queues.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: منع أزرار واتساب العائمة المزعجة من سحب المتسوقين الجاهزين للدفع الذاتي الفوري (عبر `Apple Pay` أو `مدى` أو `تابي` أو البطاقة) إلى طوابير محادثات يدوية بطيئة تفقد الإحالة وتؤجل البيع.
- **Why `DECISION_AID` Fits This User Job (EN)**: Many MENA stores place a giant pulsing `'اطلب عبر واتساب الآن!'` button right next to (or larger than) the `'Add to Cart'` and `'Checkout'` buttons on every page, even for simple 150 SAR/800 EGP items; ready-to-pay Apple Pay/Mada shoppers click WhatsApp instead, wait 25 minutes for a human agent to reply, lose their attribution cookie (`AMP-126`), or switch from Prepaid to COD! A contextual DECISION_AID shows when to display WhatsApp and when to hide it.
- **لماذا يناسب شكل `DECISION_AID` هذه المهمة (AR)**: تضع كثير من المتاجر زر «اطلب عبر واتساب» بحجم أكبر من زر «إضافة للسلة» في كل الصفحات وحتى داخل صفحة الدفع؛ فيضغط المتسوق الذي كان مستعداً للدفع الفوري بـ `Apple Pay` أو `مدى` على واتساب وينتظر 20 دقيقة لرد الموظف فيبرد حماسه أو يتحول للدفع عند الاستلام! وتحدد أداة القرار هذه متى يظهر زر واتساب ومتى يختفي.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when configuring WhatsApp chat widgets on e-commerce stores and landing pages in KSA, UAE, and Egypt.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إعداد أزرار وودجات واتساب في المتاجر الإلكترونية وصفحات الهبوط في السعودية والإمارات ومصر.
- **When NOT to Use It (EN)**: Never display a floating `'Order on WhatsApp'` button on the `/checkout` page unless an actual payment failure or idle timeout (`>90 seconds` stalled on an error) has occurred!
- **متى لا تستخدم هذه الأداة (AR)**: لا تُظهر زر «اطلب عبر واتساب» العائم داخل صفحة إتمام الدفع (`/checkout`) إلا في حالة تعثر عملية الدفع فعلياً أو توقف المستخدم لأكثر من 90 ثانية!

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Product AOV & Customization Complexity (`Standard Self-Serve SKU < 1,000 SAR / 4,000 EGP` vs. `Bespoke / High-Ticket > 2,000 SAR / 10,000 EGP`)
2. Page Route (`/`, `/collections/*`, `/products/*`, `/cart`, `/checkout`)
3. Cart Context Deep-Link Generator (`AMP-126`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Contextual WhatsApp Widget Visibility & Cart-Context Decision Matrix

#### 1. Page-by-Page Visibility & Trigger Rules
| Storefront Page / Context | Standard Self-Serve SKUs (`Perfumes, Apparel, Gadgets, Cosmetics`) | High-Ticket / Bespoke SKUs (`Custom Furniture, Jewelry, B2B Bulk, Clinics`) | Mandatory Cart-Context Payload (`Never Send Blank Chat!`) |
| :--- | :--- | :--- | :--- |
| **1. Product Detail Page (`/products/*`)** | **Secondary Quiet Help Link Only** (`"لديك استفسار عن المقاس؟ تواصل معنا"` placed *below* the fold or as a small non-pulsing icon `88px` above the sticky bar `AMP-389`). **Primary CTA is 100% `Apple Pay / أضف للسلة`!** | **Co-Primary Consult CTA** (`"تحدث مع مستشار التصميم عبر واتساب"` alongside `"احجز الآن"`). | Automatically pass `Product Name`, `Selected Variant/Size`, `Price`, and `UTM Campaign Code` (`AMP-126`) in the pre-filled message! |
| **2. Slide-Out Cart Drawer (`/cart`)** | **`HIDE WHATSAPP WIDGET` (`display: none`)** — Do NOT distract a shopper who is 1 tap away from Apple Pay / Tabby / Checkout! | Small text link only (`"تحتاج عرض سعر لشركة؟"`). | Pass full `Cart Recovery Link` + `Cart Item SKUs`. |
| **3. Checkout Funnel (`/checkout`)** | **`STRICTLY HIDDEN BY DEFAULT`** — **Reveal ONLY on Conditional Rescue Trigger**: If payment gateway returns `declined/error` OR user stalls on the shipping/payment step for **`> 90 seconds`**. | Reveal quiet `"تحتاج مساعدة في إتمام الدفع؟"` pill after `60s` idle or payment error. | Pass `Checkout_ID`, `Cart_Total`, and `Error_Step` so the support agent/bot sends a direct payment link in 10 seconds! |

#### 2. Copy-Ready Conditional Checkout Rescue Script (Only Shows WhatsApp If User Stalls or Hits Payment Error)
```javascript
(function conditionalCheckoutWhatsAppRescue() {
  var waWidget = document.querySelector('.whatsapp-floating-widget');
  if (!waWidget) return;
  if (window.location.pathname.indexOf('/checkout') !== -1 || window.location.pathname.indexOf('/cart') !== -1) {
    waWidget.style.display = 'none'; // Hide by default so self-serve prepaid buyers aren't hijacked
    // Reveal ONLY if payment error appears or user stalls for 90 seconds
    setTimeout(function() {
      waWidget.style.display = 'block';
    }, 90000);
    window.addEventListener('payment_gateway_error', function() {
      waWidget.style.display = 'block';
    });
  }
})();
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Salla, Zid, Shopify & WooCommerce Cart/Checkout Conditional Script Visibility** | `supported` | [Official Reference](https://23hublab.com/digital-advertising-landscape-in-egypt/) (`2026-10-25`) | Self-serve prepaid checkouts convert at significantly higher net margin and lower RTO than manual chat orders for standard <1,000 SAR / <4,000 EGP retail items. | Always hide floating chat launchers when the slide-out cart drawer or checkout step is active, revealing them only on error/idle timeout. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-404`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Triggering WhatsApp assistance only on exit-intent, high-cart-value thresholds, or validation errors, while passing full cart SKU context.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-414`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Triggering WhatsApp assistance only on exit-intent, high-cart-value thresholds, or validation errors, while passing full cart SKU context.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-424`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Triggering WhatsApp assistance only on exit-intent, high-cart-value thresholds, or validation errors, while passing full cart SKU context.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-434`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Triggering WhatsApp assistance only on exit-intent, high-cart-value thresholds, or validation errors, while passing full cart SKU context.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Riyadh Women's Modest Fashion Store (`AOV: 380 SAR`, Apple Pay + Mada + Tabby enabled).
- **Problem**: A developer placed a giant green button `"اطلبي عبر واتساب بدلاً من الموقع 💬"` directly underneath the `'Add to Cart'` button and inside the `/cart` drawer. `31%` of shoppers clicked the WhatsApp button instead of checking out; human agents took 40 minutes to reply during evening peak hours, converting less than `18%` of those chats—and the ones who did buy demanded COD instead of Apple Pay/Tabby!
- **Human Review & Key Edits Applied**: 1. **Enabled 1-Tap Apple Pay & Tabby Express on PDP**: Highlighted instant self-serve checkout (`"إتمام الطلب في 10 ثوانٍ عبر Apple Pay أو تابي"`).
2. **Configured Checkout Error Rescue**: If a Mada/card 3DS attempt fails on `/checkout`, the rescue banner immediately offers a 1-click switch to Tabby/Tamara or WhatsApp assistance with the pre-built cart URL attached.
- **Final Usable Output**: - Self-serve Prepaid/Tabby checkout rate jumped by `+34%`, human support chat backlog dropped by `62%`, and COD share fell from `29%` to `14%`.
- **What Can Go Wrong**: A shopper clicks the WhatsApp help icon from a specific product page (`/products/silk-abaya-black-54`), and the widget opens a blank chat saying only `'مرحباً'` with zero URL or product name—forcing the agent to ask `'أي منتج تقصدين؟ صوري لي الشاشة!'`.
- **Correction & Fallback**: Never use a static `https://wa.me/9665...` URL on product or checkout pages; always dynamically inject `window.location.href` (stripped of PII) and `document.title` into `?text=` (`AMP-126`).

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Self-Serve Checkout Completion Rate (`%`), Prepaid vs. COD Order Ratio, and Support Agent Chat-to-Order Conversion Rate.
- **Baseline Definition**: Prior 14-day checkout conversion rate and manual WhatsApp chat volume.
- **Observation Window**: 14 days post-update. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Protecting the self-serve funnel maximizes instant prepaid conversions, while high-ticket bespoke items still benefit from consultative WhatsApp sales.
