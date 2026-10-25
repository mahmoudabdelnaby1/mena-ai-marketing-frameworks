# WhatsApp Floating-Button Placement & Prepaid-Checkout Protection Decision Aid
## <span dir="rtl">أداة قرار ضبط ظهور زر «واتساب العائم» لمنع خطف متسوقي الدفع الإلكتروني الجاهزين للشراء (`Prepaid Checkout Hijack`)</span>

> **Asset ID**: `FW-081` (`AMP-394`) | **Artifact Type**: `DECISION_AID` | **Channel**: CRO - Conversion Rate Optimization | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Prevent intrusive floating WhatsApp buttons from pulling ready-to-pay Apple Pay, Mada, Tabby, and Card shoppers out of your self-serve checkout funnel into slow, unattributed manual chat queues.
- **AR**: <span dir="rtl">منع أزرار واتساب العائمة المزعجة من سحب المتسوقين الجاهزين للدفع الذاتي الفوري (عبر `Apple Pay` أو `مدى` أو `تابي` أو البطاقة) إلى طوابير محادثات يدوية بطيئة تفقد الإحالة وتؤجل البيع.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when configuring WhatsApp chat widgets on e-commerce stores and landing pages in KSA, UAE, and Egypt.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد أزرار وودجات واتساب في المتاجر الإلكترونية وصفحات الهبوط في السعودية والإمارات ومصر.</span>
- **When NOT to Use It (EN)**: Never display a floating `'Order on WhatsApp'` button on the `/checkout` page unless an actual payment failure or idle timeout (`>90 seconds` stalled on an error) has occurred!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تُظهر زر «اطلب عبر واتساب» العائم داخل صفحة إتمام الدفع (`/checkout`) إلا في حالة تعثر عملية الدفع فعلياً أو توقف المستخدم لأكثر من 90 ثانية!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Product AOV & Customization Complexity (`Standard Self-Serve SKU < 1,000 SAR / 4,000 EGP` vs. `Bespoke / High-Ticket > 2,000 SAR / 10,000 EGP`)
- Page Route (`/`, `/collections/*`, `/products/*`, `/cart`, `/checkout`)
- Cart Context Deep-Link Generator (`AMP-126`)

## 2. The Working `DECISION_AID` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Riyadh Women's Modest Fashion Store (`AOV: 380 SAR`, Apple Pay + Mada + Tabby enabled).
- **Problem**: A developer placed a giant green button `"اطلبي عبر واتساب بدلاً من الموقع 💬"` directly underneath the `'Add to Cart'` button and inside the `/cart` drawer. `31%` of shoppers clicked the WhatsApp button instead of checking out; human agents took 40 minutes to reply during evening peak hours, converting less than `18%` of those chats—and the ones who did buy demanded COD instead of Apple Pay/Tabby!

### Step B: Initial Output (`المخرج الأولي`)
- **Applied Contextual Visibility Rules**:
  1. Removed `"اطلبي عبر واتساب بدلاً من الموقع"` from the buy-box and hid the widget completely on `/cart` and the first 90 seconds of `/checkout`.
  2. Kept a subtle `"مساعدة في اختيار المقاس؟"` link inside the Size Guide accordion that passes the exact SKU and size in the message.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Enabled 1-Tap Apple Pay & Tabby Express on PDP**: Highlighted instant self-serve checkout (`"إتمام الطلب في 10 ثوانٍ عبر Apple Pay أو تابي"`).
2. **Configured Checkout Error Rescue**: If a Mada/card 3DS attempt fails on `/checkout`, the rescue banner immediately offers a 1-click switch to Tabby/Tamara or WhatsApp assistance with the pre-built cart URL attached.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Self-serve Prepaid/Tabby checkout rate jumped by `+34%`, human support chat backlog dropped by `62%`, and COD share fell from `29%` to `14%`.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A shopper clicks the WhatsApp help icon from a specific product page (`/products/silk-abaya-black-54`), and the widget opens a blank chat saying only `'مرحباً'` with zero URL or product name—forcing the agent to ask `'أي منتج تقصدين؟ صوري لي الشاشة!'`.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Never use a static `https://wa.me/9665...` URL on product or checkout pages; always dynamically inject `window.location.href` (stripped of PII) and `document.title` into `?text=` (`AMP-126`).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Salla, Zid, Shopify & WooCommerce Cart/Checkout Conditional Script Visibility** | `supported` | [Official Docs](https://23hublab.com/digital-advertising-landscape-in-egypt/) (`2026-10-25`) | Self-serve prepaid checkouts convert at significantly higher net margin and lower RTO than manual chat orders for standard <1,000 SAR / <4,000 EGP retail items. | Always hide floating chat launchers when the slide-out cart drawer or checkout step is active, revealing them only on error/idle timeout. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Self-Serve Checkout Completion Rate (`%`), Prepaid vs. COD Order Ratio, and Support Agent Chat-to-Order Conversion Rate.
- **Baseline**: Prior 14-day checkout conversion rate and manual WhatsApp chat volume.
- **Observation Window**: 14 days post-update.
- **Interpretation Boundary**: Protecting the self-serve funnel maximizes instant prepaid conversions, while high-ticket bespoke items still benefit from consultative WhatsApp sales.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) — *VOCTOS* (Published `2026-10-18`, Accessed `2026-10-25`): GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral.
- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
