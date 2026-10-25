# End-to-End Worked Example & Failure Recovery — `FW-081` (`AMP-394`)

- **Framework**: WhatsApp Floating-Button Placement & Prepaid-Checkout Protection Decision Aid
- **العنوان بالعربية**: أداة قرار ضبط ظهور زر «واتساب العائم» لمنع خطف متسوقي الدفع الإلكتروني الجاهزين للشراء (`Prepaid Checkout Hijack`)
- **Selected Artifact Type**: `DECISION_AID`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Store**: Riyadh Women's Modest Fashion Store (`AOV: 380 SAR`, Apple Pay + Mada + Tabby enabled).
- **Problem**: A developer placed a giant green button `"اطلبي عبر واتساب بدلاً من الموقع 💬"` directly underneath the `'Add to Cart'` button and inside the `/cart` drawer. `31%` of shoppers clicked the WhatsApp button instead of checking out; human agents took 40 minutes to reply during evening peak hours, converting less than `18%` of those chats—and the ones who did buy demanded COD instead of Apple Pay/Tabby!

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Applied Contextual Visibility Rules**:
  1. Removed `"اطلبي عبر واتساب بدلاً من الموقع"` from the buy-box and hid the widget completely on `/cart` and the first 90 seconds of `/checkout`.
  2. Kept a subtle `"مساعدة في اختيار المقاس؟"` link inside the Size Guide accordion that passes the exact SKU and size in the message.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Enabled 1-Tap Apple Pay & Tabby Express on PDP**: Highlighted instant self-serve checkout (`"إتمام الطلب في 10 ثوانٍ عبر Apple Pay أو تابي"`).
2. **Configured Checkout Error Rescue**: If a Mada/card 3DS attempt fails on `/checkout`, the rescue banner immediately offers a 1-click switch to Tabby/Tamara or WhatsApp assistance with the pre-built cart URL attached.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Self-serve Prepaid/Tabby checkout rate jumped by `+34%`, human support chat backlog dropped by `62%`, and COD share fell from `29%` to `14%`.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A shopper clicks the WhatsApp help icon from a specific product page (`/products/silk-abaya-black-54`), and the widget opens a blank chat saying only `'مرحباً'` with zero URL or product name—forcing the agent to ask `'أي منتج تقصدين؟ صوري لي الشاشة!'`.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Never use a static `https://wa.me/9665...` URL on product or checkout pages; always dynamically inject `window.location.href` (stripped of PII) and `document.title` into `?text=` (`AMP-126`).
