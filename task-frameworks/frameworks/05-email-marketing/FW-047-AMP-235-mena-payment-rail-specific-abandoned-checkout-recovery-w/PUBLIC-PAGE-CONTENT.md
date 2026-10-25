# MENA Payment-Rail Specific Abandoned Checkout Recovery Workflow (COD vs. Tabby/Tamara BNPL vs. Fawry/InstaPay)
## <span dir="rtl">مسار عمل استرداد السلات المتروكة المخصص حسب وسيلة الدفع في مصر والخليج (`COD` مقابل `Tabby/Tamara` مقابل كود `فوري/إنستاباي`)</span>

> **Asset ID**: `FW-047` (`AMP-235`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Branch abandoned checkout emails and WhatsApp reminders by the shopper's selected payment method—separating Fawry OTC reference-code expiry reminders in Egypt from Tabby/Tamara installment nudges in KSA/UAE and COD trust reassurance.
- **AR**: <span dir="rtl">تفريع رسائل استرداد السلات المتروكة وتوقيتها حسب وسيلة الدفع التي اختارها المتسوق (تذكير بصلاحية كود «فوري» قبل انتهائه في مصر، مقابل تذكير تقسيط «تابي/تمارا» في الخليج، أو طمأنة الدفع عند الاستلام).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when configuring abandoned checkout / pending-payment automation flows in Klaviyo, HubSpot, Omnisend, Salla, Zid, or Shopify/WooCommerce across Egypt, KSA, and UAE.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد سلاسل استرداد السلات المتروكة والدفعات المعلقة في متاجر مصر والسعودية والإمارات.</span>
- **When NOT to Use It (EN)**: Do not send an 'Abandoned Cart 10% Discount Code' to a customer who already generated a Pending Fawry Reference Code or Pending Bank/InstaPay Transfer—that cannibalizes margin on an already-committed order!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا ترسل «كود خصم 10% للسلة المتروكة» لعميل قام بالفعل بإصدار كود دفع «فوري» معلق أو تحويل «إنستاباي»؛ لأن ذلك يهدر هامش الربح لطلب تم تأكيده بالفعل وينتظر السداد النقدي.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Checkout Event Webhook Payload containing `payment_gateway_selected` (`fawry_otc`, `instapay`, `tabby`, `tamara`, `mada_card`, `cod`, or `none`)
- Fawry Reference Code (`{{fawry_ref_number}}`) & Expiry Timestamp (`{{fawry_expires_at}}`)
- Customer COD Return History Score (`AMP-240`)

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### 4-Branch MENA Payment-Rail Recovery Architecture

| Branch ID & Trigger Condition | Exact Timing Cadence | Message Content & Action (Arabic + English) | Discount Policy |
| :--- | :--- | :--- | :--- |
| **Branch A: Pending Fawry OTC Cash Code (`payment_method == 'fawry_pay_at_outlet'`, Egypt)** | **T+5 mins** (Code Receipt) → **T+18 hours** (Reminder) → **T+42 hours** (6h before 48h expiry) | **DO NOT say "You left items in your cart!"** Instead:<br>`"كود الدفع الخاص بطلبك عبر فوري هو: [ {{fawry_ref}} ] — الكود صالح حتى {{expiry_time}}. توجه لأقرب منفذ فوري أو صيدلية أو سوبر ماركت واطلب سداد كود فوري باي (خدمة رقم 788) ليتم شحن طلبك فوراً."` | **0% Discount** (Order is already placed; customer just needs the reference code handy when walking past a Fawry machine). |
| **Branch B: Declined Mada / Apple Pay / Card 3DS (`payment_status == 'failed_3ds'`, KSA/UAE/EG)** | **T+15 mins** → **T+6 hours** | `"لاحظنا عدم اكتمال عملية الدفع لطلبك. حفظنا لك القطع في سلتك — يمكنك إتمام الطلب الآن بضغطة واحدة عبر Apple Pay أو تقسيط المبلغ على 4 دفعات بدون فوائد عبر تابي أو تمارا (أو إنستاباي في مصر): {{checkout_recovery_url}}"` | **0% Discount at T+15m** (Friction was technical/bank limit; offer BNPL split instead of cutting margin). |
| **Branch C: Abandoned at Shipping/Price Step (`payment_method == 'none'`, KSA/UAE)** | **T+1 hour** → **T+24 hours** | Highlight **Tabby/Tamara 4-installment price** (`"ادفعي 74.75 ر.س اليوم فقط بدلاً من 299 ر.س وقسمي الباقي على 3 أشهر بدون فوائد أو رسوم"`) + exact delivery SLA (`التوصيل خلال 24 ساعة في الرياض`). | Optional free shipping or small gift at `T+24h` for first-time buyers. |
| **Branch D: Abandoned COD Selection (`payment_method == 'cod'`, Egypt/KSA)** | **T+45 mins** → **T+20 hours** | Address delivery trust & sizing doubts (`"تأكد من مقاسك مع ضمان الاستبدال السريع — أو ادفع الآن عبر إنستاباي/مدى واحصل على أولوية الشحن المجاني"`). | Check `AMP-240` first: **NEVER send discount codes to chronic COD returners (`>40%` return rate)**! |

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Cairo Electronics & Home Appliances Store on WooCommerce + Paymob/Fawry (`Average Cart: 3,200 EGP`).
- **Problem**: `38%` of shoppers selecting `Fawry Reference Code` at checkout let the 48-hour code expire because Klaviyo sent them a generic English-translated `'You forgot your cart!'` email that did NOT contain their 10-digit Fawry reference number (`{{fawry_ref}}`) or the Fawry service code (`788`).

### Step B: Initial Output (`المخرج الأولي`)
- **Deployed Branch A (`Fawry Pending Payment Flow`)**:
  - **T+5m Email + SMS/WhatsApp**: Displays `<bdi style="font-size:22px; font-weight:bold;">{{fawry_ref_number}}</bdi>`, exact amount (`3,200 EGP`), Fawry Service Code (`788`), and 48-hour expiry timestamp.
  - **T+18h Evening Reminder (`6:00 PM` when shoppers are out commuting)**: `"كود فوري الخاص بطلبك ({{fawry_ref_number}}) ما زال مفعلاً — يمكنك سداده من أي ماكينة فوري أو تطبيق MyFawry في دقيقة واحدة."`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Added MyFawry App & InstaPay Switch Option**: Included a secondary button inside the T+18h email: `"تفضل الدفع من موبايلك الآن بدون الذهاب لمنفذ فوري؟ ادفع بضغطة واحدة عبر تطبيق MyFawry أو إنستاباي من هنا"`.
2. **Suppressed Generic Abandoned Cart Flow**: Added filter `payment_method != 'fawry_pay_at_outlet'` to the generic abandoned cart flow so Fawry buyers never receive conflicting messages.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- 4-Branch payment-specific recovery flows active across Egypt and KSA with dynamic `<bdi>` reference code injection and zero margin-cannibalizing discounts on pending OTC orders.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A customer generates a Fawry reference code (`1,000 EGP`), then receives an automated 'Abandoned Cart 15% Off (`850 EGP`)' email 2 hours later; the customer abandons the first Fawry code, creates a second discounted order, and inventory stays double-locked for 48 hours.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Treat `Pending Fawry OTC` and `Pending Bank/InstaPay Transfer` as **`Awaiting_Offline_Settlement`** (a post-order state), strictly excluded from pre-order `Abandoned_Cart` discount flows.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Paymob / Fawry / Kashier / Moyasar / Tap Webhook Metadata in Klaviyo & HubSpot** | `supported` | [Official Docs](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) (`2026-10-25`) | Egyptian and Gulf payment gateways emit `pending` webhook events containing the OTC reference number (`bill_reference`) and selected payment rail (`fawry`, `valu`, `tabby`, `tamara`). | Pass `selected_payment_method` and `fawry_reference_code` as custom event properties in the `Started Checkout` / `Placed Pending Order` event. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Fawry OTC Code Paid-Conversion Rate (`Paid Fawry Orders / Generated Fawry Codes`) and Abandoned Checkout Recovery Revenue by Payment Branch.
- **Baseline**: Prior 30-day Fawry code expiration rate and cart recovery rate.
- **Observation Window**: 28 days post-launch.
- **Interpretation Boundary**: Payment-specific reminders remove execution friction, while stock reservation window and outlet proximity influence OTC completion.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Conversion Rate Optimization for UAE E-Commerce (2026)](https://soluvide.com/blog/conversion-rate-optimization-uae-ecommerce-2026) — *Soluvide* (Published `2026-02-19`, Accessed `2026-10-25`): Shows how Cash on Delivery (COD) and Buy Now Pay Later (Tabby and Tamara) reduce checkout friction and lift AOV in UAE/GCC e-commerce.
- [Payment Gateway Egypt: Fees, Comparison & Best Providers (2026)](https://digitology.co/payment-gateway-egypt/) — *Digitology Egypt* (Published `2026-08-07`, Accessed `2026-10-25`): Reports Use the merchant’s recent order records to estimate payment mix; warns that card-only checkouts address less than a quarter of Egyptian shoppers.
- [Payment Gateways in Egypt 2026: Paymob, Fawry, InstaPay](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) — *Nilex Digital Systems* (Published `2026-09-26`, Accessed `2026-10-25`): Details checkout UX, reconciliation, and conversion fixes for Paymob, Fawry reference codes, Meeza, InstaPay, and valU in Egypt.
