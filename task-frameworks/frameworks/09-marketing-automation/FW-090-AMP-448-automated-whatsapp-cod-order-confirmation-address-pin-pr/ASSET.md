# FW-090: Automated WhatsApp COD Order Confirmation, Address-Pin & Prepaid-Switch Workflow (Egypt & KSA)
## مسار عمل التأكيد الآلي لطلبات الدفع عند الاستلام (`COD`) والتحقق من موقع التوصيل عبر واتساب قبل تسليم الشحنة للمندوب (مصر والسعودية)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-458`, `AMP-468`, `AMP-478`, `AMP-488`, `AMP-498`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Marketing Operations Manager, CRM & Automation Architect, Data Analyst, Growth Engineer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Cut Cash-on-Delivery (`COD`) courier return-to-origin (`RTO`) losses by 25–40% in Egypt and Saudi Arabia by automatically verifying the buyer's intent, street/landmark, or map pin on WhatsApp within 90 seconds of order placement before printing the courier AWB.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: خفض نسبة مرتجعات الدفع عند الاستلام (`COD RTO`) في مصر والسعودية بنسبة 25–40% عبر إرسال رسالة تأكيد تفاعلية آلية على واتساب خلال 90 ثانية من الطلب للتحقق من الجدية وتثبيت العنوان/الموقع قبل إصدار بوليصة الشحن.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: In Egypt using the merchant’s measured COD share and KSA (15–30% COD), impulse social-media shoppers frequently enter a typo in their phone number, write a vague 2-word address (`'القاهرة - مدينة نصر'`), or order from 3 stores and only accept the first parcel that arrives; dispatching unconfirmed COD parcels blindly costs the merchant double shipping fees (`75–110 EGP` / `30–45 SAR` per returned box); a pre-dispatch WhatsApp confirmation OPERATING_FRAMEWORK filters fake/remorse orders before they leave the warehouse.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: في أسواق مصر والسعودية، تتضمن نسبة كبيرة من طلبات الدفع عند الاستلام الاندفاعية أخطاءً في رقم الهاتف أو عناوين ناقصة («القاهرة - مدينة نصر» بدون رقم عقار) أو تردد المشتري؛ وإرسال هذه الشحنات للمندوب دون تأكيد مسبق يكبد المتجر رسوم شحن مزدوجة؛ لذا يقوم هذا الإطار التشغيلي بفلترة وتأكيد الطلبات آلياً عبر واتساب قبل طباعة البوليصة.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use on 100% of Cash-on-Delivery (`COD`) orders in Egypt, Saudi Arabia, UAE, and wider MENA.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم لجميع طلبات الدفع عند الاستلام (`COD`) في مصر والسعودية والإمارات قبل تسليمها لشركة الشحن.
- **When NOT to Use It (EN)**: Do not put already-paid orders (`Apple Pay`, `Mada`, `Card`, `InstaPay Verified`, `Tabby`, `Tamara`) on hold waiting for WhatsApp confirmation—ship prepaid orders immediately and send them a standard shipping notification!
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً بتجميد أو تعليق الشحن للطلبات المدفوعة مسبقاً (`مدى`، `Apple Pay`، `تابي`، `تمارا`، `إنستاباي`) بانتظار تأكيد واتساب؛ اشحن الطلبات المدفوعة فوراً، وطبّق شرط التأكيد على طلبات `COD` فقط!

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Storefront `Order Created` Webhook (`payment_method == 'cod'`)
2. Approved WhatsApp `UTILITY` Order Confirmation Template (`AMP-441`) with 3 interactive Quick-Reply buttons
3. Courier API (`Bosta`, `Mylerz`, `Aramex`, `SMSA`, `J&T`) auto-dispatch tag (`Tag: COD_CONFIRMED_READY_TO_SHIP`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 4-Step Automated WhatsApp COD Verification & Dispatch Gate

#### Step 1: Hold Unconfirmed COD Orders from Courier AWB Generation (`Status: On_Hold_Awaiting_COD_Confirm`)
When an order arrives with `payment_method == 'cod'`:
- Do **NOT** automatically push the AWB to Bosta/SMSA/Aramex at `T+0s`.
- Normalize the phone number (`AMP-388`, `AMP-067`). If the phone number fails E.164 mobile length validation (`e.g., 9 digits instead of 11 in Egypt`), flag `INVALID_PHONE_CANCEL` immediately.

#### Step 2: Fire Instant WhatsApp `UTILITY` Confirmation Template at `T+60 Seconds`
```text
Template Category: UTILITY (AMP-441 Compliant — Zero Promo Text)
Header: تأكيد طلب الدفع عند الاستلام #{{1}} 📦
Body:
أهلاً {{2}}، استلمنا طلبك من {{3}} بقيمة إجمالية {{4}} (الدفع نقداً عند الاستلام).
عنوان التوصيل المسجل: {{5}}
يرجى الضغط على الزر أدناه لتأكيد الطلب وتجهيزه للشحن اليوم:

Buttons (Quick Reply):
[ 1️⃣ تأكيد الطلب والعنوان ]
[ 2️⃣ تعديل العنوان / إرسال اللوكيشن 📍 ]
[ 3️⃣ إلغاء الطلب ]
```

#### Step 3: Automated Branch Handling
1. **If Buyer Taps `[ 1️⃣ تأكيد الطلب والعنوان ]`**:
   - Flip order tag in Salla/Zid/Shopify/WooCommerce to **`COD_CONFIRMED_READY_TO_SHIP`**.
   - Automatically generate Courier AWB (`Bosta / SMSA / Aramex`) AND fire the `Order_Confirmed_WhatsApp` CAPI event (`AMP-062`).
   - *(Optional Prepaid Nudge After Confirmation)*: Send a 1-line follow-up: `"تم تأكيد طلبك! 💡 تفضل الدفع الآن عبر (إنستاباي / مدى / Apple Pay) لتفادي تجهيز النقدية للمندوب؟ ادفع من هنا: {{payment_link}}"`.
2. **If Buyer Taps `[ 2️⃣ تعديل العنوان / إرسال اللوكيشن 📍 ]`**:
   - Prompt the user to share their **WhatsApp Native Location Pin (`مشاركة الموقع`)** or type the missing building/apartment/landmark (`AMP-390`). Parse `latitude, longitude` and append the Google Maps link directly into the courier `delivery_notes` field!
3. **If Buyer Taps `[ 3️⃣ إلغاء الطلب ]`**:
   - Cancel order cleanly in backend, release reserved inventory immediately, and save `75–110 EGP / 35 SAR` in wasted courier shipping fees!
4. **If No Reply After `4 Hours` (`Daytime`)**:
   - Send 1 automated SMS / second WhatsApp reminder; if still unconfirmed after `24 hours` on a high-risk/first-time COD order, route to a 30-second automated IVR/human confirmation call before printing the AWB.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **WhatsApp Cloud API Interactive Quick-Reply Buttons & Location Message Webhook (`type: location`)** | `supported` | [Official Reference](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) (`2026-10-25`) | WhatsApp Cloud API supports up to 3 Quick-Reply buttons on `UTILITY` templates and receives native GPS `location` objects (`latitude`, `longitude`, `address`) when a customer shares their pin. | If WhatsApp number is unreachable (landline or non-WhatsApp SIM), fall back automatically to an SMS confirmation link after 2 hours. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-458`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Automated WhatsApp Utility confirmation flow (Confirm / Edit Address / Cancel) that holds courier AWB generation until confirmed or verified by phone.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-468`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Automated WhatsApp Utility confirmation flow (Confirm / Edit Address / Cancel) that holds courier AWB generation until confirmed or verified by phone.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-478`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Automated WhatsApp Utility confirmation flow (Confirm / Edit Address / Cancel) that holds courier AWB generation until confirmed or verified by phone.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-488`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Automated WhatsApp Utility confirmation flow (Confirm / Edit Address / Cancel) that holds courier AWB generation until confirmed or verified by phone.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-498`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Automated WhatsApp Utility confirmation flow (Confirm / Edit Address / Cancel) that holds courier AWB generation until confirmed or verified by phone.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Cairo & Alexandria D2C Apparel & Cosmetics Store (`320` COD orders/day via Bosta).
- **Problem**: Store printed AWBs and shipped 100% of COD orders blindly. `29%` (`93` parcels/day) were returned to sender (`RTO` — fake phone numbers, buyers saying `'طلبت بالغلط'`, or missing building numbers), costing **`246,000 EGP / month`** in dead courier fees.
- **Human Review & Key Edits Applied**: 1. **Fast-Track VIP Bypass (`AMP-240`)**: Added an automatic bypass rule: if the buyer is a **`TIER_1_VERIFIED_DELIVERED_VIP`** (`>= 2` past delivered orders and `<10%` RTO), mark the order ready to ship immediately while sending a courtesy confirmation notice.
2. **Courier GPS Note Injection**: Mapped the WhatsApp `location` message (`lat, long`) into Bosta/SMSA's driver notes field so the courier can open Google Maps in 1 tap.
- **Final Usable Output**: - Courier RTO rate on shipped COD parcels dropped from `29%` to **`11.8%`**, saving over **`145,000 EGP / month`** in wasted round-trip shipping fees.
- **What Can Go Wrong**: A store holds an Apple Pay / Mada / InstaPay prepaid order in the `Awaiting_COD_Confirmation` queue by mistake because the webhook didn't check `financial_status != 'paid'`; the paying customer gets angry asking why their paid order hasn't shipped.
- **Correction & Fallback**: Enforce the **Strict Entry Filter**: `IF order.financial_status == 'paid' THEN SHIP_IMMEDIATELY`. Only route orders where `payment_method == 'cod' AND financial_status == 'pending'` into the COD Confirmation Gate.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Pre-Dispatch Cancellation/Fake-Order Catch Rate (`%`), Post-Dispatch Courier RTO Rate (`Target: <12%`), and Monthly Saved Courier Fees (`SAR / EGP`).
- **Baseline Definition**: Prior 30-day courier RTO `%` and monthly RTO shipping charges.
- **Observation Window**: 28 days post-deployment. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Pre-dispatch confirmation eliminates fake numbers, remorse clicks, and incomplete addresses before shipping; courier last-mile speed (`<48h`) still governs doorstep acceptance.
