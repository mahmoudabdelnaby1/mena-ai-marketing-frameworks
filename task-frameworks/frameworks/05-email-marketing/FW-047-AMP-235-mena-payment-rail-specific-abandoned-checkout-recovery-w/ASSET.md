# FW-047: MENA Payment-Rail Specific Abandoned Checkout Recovery Workflow (COD vs. Tabby/Tamara BNPL vs. Fawry/InstaPay)
## مسار عمل استرداد السلات المتروكة المخصص حسب وسيلة الدفع في مصر والخليج (`COD` مقابل `Tabby/Tamara` مقابل كود `فوري/إنستاباي`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-245`, `AMP-255`, `AMP-265`, `AMP-275`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Branch abandoned checkout emails and WhatsApp reminders by the shopper's selected payment method—separating Fawry OTC reference-code expiry reminders in Egypt from Tabby/Tamara installment nudges in KSA/UAE and COD trust reassurance.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تفريع رسائل استرداد السلات المتروكة وتوقيتها حسب وسيلة الدفع التي اختارها المتسوق (تذكير بصلاحية كود «فوري» قبل انتهائه في مصر، مقابل تذكير تقسيط «تابي/تمارا» في الخليج، أو طمأنة الدفع عند الاستلام).
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Standard AI abandoned-cart templates assume every shopper abandoned a credit-card form and send the same `'Did you forget something? Take 10% off'` email at 4 hours and 24 hours; in reality, an Egyptian shopper who generated a Fawry cash reference code hasn't 'abandoned'—they need their 48-hour reference code and nearest Fawry outlet reminder, while a KSA shopper who failed a Mada 3DS or Tabby split needs a 15-minute payment-switch link; an OPERATING_FRAMEWORK branches by payment rail.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تفترض قوالب السلات المتروكة التقليدية أن كل متسوق ترك صفحة البطاقة البنكية؛ بينما في الواقع يحتاج المتسوق المصري الذي أصدر «كود مرجعي لدفع فوري» إلى رسالة تحفظ له الكود وتذكره بموعد انتهاء صلاحيته (48 ساعة)، ويحتاج متسوق السعودية/الإمارات الذي تعثرت دفعته في مدى أو تابي إلى رابط سريع لتبديل وسيلة الدفع خلال 15 دقيقة؛ لذا يفصل هذا الإطار التشغيلي المسارات بدقة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when configuring abandoned checkout / pending-payment automation flows in Klaviyo, HubSpot, Omnisend, Salla, Zid, or Shopify/WooCommerce across Egypt, KSA, and UAE.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند إعداد سلاسل استرداد السلات المتروكة والدفعات المعلقة في متاجر مصر والسعودية والإمارات.
- **When NOT to Use It (EN)**: Do not send an 'Abandoned Cart 10% Discount Code' to a customer who already generated a Pending Fawry Reference Code or Pending Bank/InstaPay Transfer—that cannibalizes margin on an already-committed order!
- **متى لا تستخدم هذه الأداة (AR)**: لا ترسل «كود خصم 10% للسلة المتروكة» لعميل قام بالفعل بإصدار كود دفع «فوري» معلق أو تحويل «إنستاباي»؛ لأن ذلك يهدر هامش الربح لطلب تم تأكيده بالفعل وينتظر السداد النقدي.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Checkout Event Webhook Payload containing `payment_gateway_selected` (`fawry_otc`, `instapay`, `tabby`, `tamara`, `mada_card`, `cod`, or `none`)
2. Fawry Reference Code (`{{fawry_ref_number}}`) & Expiry Timestamp (`{{fawry_expires_at}}`)
3. Customer COD Return History Score (`AMP-240`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 4-Branch MENA Payment-Rail Recovery Architecture

| Branch ID & Trigger Condition | Exact Timing Cadence | Message Content & Action (Arabic + English) | Discount Policy |
| :--- | :--- | :--- | :--- |
| **Branch A: Pending Fawry OTC Cash Code (`payment_method == 'fawry_pay_at_outlet'`, Egypt)** | **T+5 mins** (Code Receipt) → **T+18 hours** (Reminder) → **T+42 hours** (6h before 48h expiry) | **DO NOT say "You left items in your cart!"** Instead:<br>`"كود الدفع الخاص بطلبك عبر فوري هو: [ {{fawry_ref}} ] — الكود صالح حتى {{expiry_time}}. توجه لأقرب منفذ فوري أو صيدلية أو سوبر ماركت واطلب سداد كود فوري باي (خدمة رقم 788) ليتم شحن طلبك فوراً."` | **0% Discount** (Order is already placed; customer just needs the reference code handy when walking past a Fawry machine). |
| **Branch B: Declined Mada / Apple Pay / Card 3DS (`payment_status == 'failed_3ds'`, KSA/UAE/EG)** | **T+15 mins** → **T+6 hours** | `"لاحظنا عدم اكتمال عملية الدفع لطلبك. حفظنا لك القطع في سلتك — يمكنك إتمام الطلب الآن بضغطة واحدة عبر Apple Pay أو تقسيط المبلغ على 4 دفعات بدون فوائد عبر تابي أو تمارا (أو إنستاباي في مصر): {{checkout_recovery_url}}"` | **0% Discount at T+15m** (Friction was technical/bank limit; offer BNPL split instead of cutting margin). |
| **Branch C: Abandoned at Shipping/Price Step (`payment_method == 'none'`, KSA/UAE)** | **T+1 hour** → **T+24 hours** | Highlight **Tabby/Tamara 4-installment price** (`"ادفعي 74.75 ر.س اليوم فقط بدلاً من 299 ر.س وقسمي الباقي على 3 أشهر بدون فوائد أو رسوم"`) + exact delivery SLA (`التوصيل خلال 24 ساعة في الرياض`). | Optional free shipping or small gift at `T+24h` for first-time buyers. |
| **Branch D: Abandoned COD Selection (`payment_method == 'cod'`, Egypt/KSA)** | **T+45 mins** → **T+20 hours** | Address delivery trust & sizing doubts (`"تأكد من مقاسك مع ضمان الاستبدال السريع — أو ادفع الآن عبر إنستاباي/مدى واحصل على أولوية الشحن المجاني"`). | Check `AMP-240` first: **NEVER send discount codes to chronic COD returners (`>40%` return rate)**! |

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Paymob / Fawry / Kashier / Moyasar / Tap Webhook Metadata in Klaviyo & HubSpot** | `supported` | [Official Reference](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) (`2026-10-25`) | Egyptian and Gulf payment gateways emit `pending` webhook events containing the OTC reference number (`bill_reference`) and selected payment rail (`fawry`, `valu`, `tabby`, `tamara`). | Pass `selected_payment_method` and `fawry_reference_code` as custom event properties in the `Started Checkout` / `Placed Pending Order` event. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-245`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Payment-method-branched recovery flows tailored to Fawry OTC, InstaPay, Tabby/Tamara, and COD.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-255`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Payment-method-branched recovery flows tailored to Fawry OTC, InstaPay, Tabby/Tamara, and COD.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-265`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Payment-method-branched recovery flows tailored to Fawry OTC, InstaPay, Tabby/Tamara, and COD.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-275`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Payment-method-branched recovery flows tailored to Fawry OTC, InstaPay, Tabby/Tamara, and COD.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-525`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-265 (Email Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Cairo Electronics & Home Appliances Store on WooCommerce + Paymob/Fawry (`Average Cart: 3,200 EGP`).
- **Problem**: `38%` of shoppers selecting `Fawry Reference Code` at checkout let the 48-hour code expire because Klaviyo sent them a generic English-translated `'You forgot your cart!'` email that did NOT contain their 10-digit Fawry reference number (`{{fawry_ref}}`) or the Fawry service code (`788`).
- **Human Review & Key Edits Applied**: 1. **Added MyFawry App & InstaPay Switch Option**: Included a secondary button inside the T+18h email: `"تفضل الدفع من موبايلك الآن بدون الذهاب لمنفذ فوري؟ ادفع بضغطة واحدة عبر تطبيق MyFawry أو إنستاباي من هنا"`.
2. **Suppressed Generic Abandoned Cart Flow**: Added filter `payment_method != 'fawry_pay_at_outlet'` to the generic abandoned cart flow so Fawry buyers never receive conflicting messages.
- **Final Usable Output**: - 4-Branch payment-specific recovery flows active across Egypt and KSA with dynamic `<bdi>` reference code injection and zero margin-cannibalizing discounts on pending OTC orders.
- **What Can Go Wrong**: A customer generates a Fawry reference code (`1,000 EGP`), then receives an automated 'Abandoned Cart 15% Off (`850 EGP`)' email 2 hours later; the customer abandons the first Fawry code, creates a second discounted order, and inventory stays double-locked for 48 hours.
- **Correction & Fallback**: Treat `Pending Fawry OTC` and `Pending Bank/InstaPay Transfer` as **`Awaiting_Offline_Settlement`** (a post-order state), strictly excluded from pre-order `Abandoned_Cart` discount flows.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Fawry OTC Code Paid-Conversion Rate (`Paid Fawry Orders / Generated Fawry Codes`) and Abandoned Checkout Recovery Revenue by Payment Branch.
- **Baseline Definition**: Prior 30-day Fawry code expiration rate and cart recovery rate.
- **Observation Window**: 28 days post-launch. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Payment-specific reminders remove execution friction, while stock reservation window and outlet proximity influence OTC completion.
