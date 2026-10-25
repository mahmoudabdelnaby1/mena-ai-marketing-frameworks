# Egypt & KSA Localized Checkout Address Form Workflow
## <span dir="rtl">مسار تخصيص حقول العنوان في صفحة الدفع لمصر والسعودية</span>

> **Asset ID**: `FW-077` (`AMP-390`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: CRO - Conversion Rate Optimization | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Review checkout address fields against the merchant's platform, address-validation needs, and selected carrier; do not assume a postal-code rule is universal. An Egypt-specific option is `Governorate -> City/District -> Street/Building/Floor -> Landmark` structure and Saudi Arabia's `City + District + Optional National Address Short-Code / Map Pin`.
- **AR**: <span dir="rtl">استبدال حقول العناوين الغربية (`State` والرمز البريدي الإجباري `Zip Code`) بهيكلة الشحن الفعلية في مصر (المحافظة ← المنطقة/الحي ← الشارع ورقم العقار والدور ← علامة مميزة) وفي السعودية (المدينة ← الحي ← الرمز المختصر للعنوان الوطني أو دبوس الخريطة).</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when configuring checkout shipping address forms on Salla, Zid, Shopify, WooCommerce, Magento, or custom apps in Egypt, Saudi Arabia, and the UAE.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند إعداد نموذج عنوان الشحن في صفحة الدفع لمتاجر مصر والسعودية والإمارات.</span>
- **When NOT to Use It (EN)**: Confirm whether a postal code is required by the merchant’s platform, carrier, address validation, or delivery market before making it mandatory.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تجعل حقل «الرمز البريدي (`Postal Code`)» حقلاً إجبارياً يمنع إتمام الطلب في متاجر مصر أو السعودية أو الإمارات!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Courier Partner Zone & City Picklist (`Bosta / Mylerz` 27 Governorates & Districts in Egypt; `SMSA / Aramex / SPL` Cities in KSA; Emirates & Areas in UAE)
- Checkout Field Configuration in Shopify (`Settings -> Checkout -> Address options`), WooCommerce, Salla, or Zid

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Country-Aware MENA Checkout Address Field Schema

| Field Slot | **Egypt (`EG` — Bosta / Mylerz / Aramex Standard)** | **Saudi Arabia (`SA` — SPL / SMSA / Aramex Standard)** | **UAE (`AE` — Dubai / Abu Dhabi Standard)** |
| :--- | :--- | :--- | :--- |
| **1. Top Geo Dropdown** | **`المحافظة (Governorate)`** — Controlled dropdown of all 27 Egyptian Governorates (`القاهرة، الجيزة، الإسكندرية، الدقهلية...`). | **`المدينة (City)`** — Searchable dropdown (`الرياض، جدة، الدمام، الخبر، مكة، المدينة...`). | **`الإمارة (Emirate)`** — Dropdown of the 7 Emirates (`دبي، أبوظبي، الشارقة، عجمان...`). |
| **2. Sub-Area / District** | **`المنطقة / الحي (District / Area)`** — Cascading dropdown or text (`مثلاً: مدينة نصر، التجمع الخامس، المعادي، الشيخ زايد، سموحة`). | **`الحي (District)`** — Required text/dropdown (`مثلاً: حي الملقا، حي النرجس، حي الروضة`). | **`المنطقة (Area / Community)`** — (`مثلاً: دبي مارينا، الخليج التجاري، جزيرة الريم`). |
| **3. Street & Building Details** | **`اسم الشارع، رقم العقار، الدور، ورقم الشقة`** *(Single clear field with placeholder example)*. | **`اسم الشارع أو رقم المبنى (أو العنوان الوطني المختصر 4 حروف + 4 أرقام مثل ABCD1234 (format illustration only; not a real address))`**. | **`اسم المبنى / الفيلا، رقم الشقة أو المكتب، والشارع`** *(UAE has no standard zip code—auto-fill `00000` in hidden backend field if gateway requires it!)*. |
| **4. Delivery Landmark / Pin (`CRITICAL FOR FIRST-ATTEMPT DELIVERY`)** | **`علامة مميزة قريبة من العنوان (Landmark)`** — (`مثلاً: بجوار مسجد... / أمام صيدلية...`). | **Optional Map Pin / WhatsApp Location Pin after checkout (`AMP-448`)**. | **`ملاحظات التوصيل للمندوب (اختياري)`**. |
| **5. Postal / Zip Code (`الرمز البريدي`)** | **`HIDDEN OR OPTIONAL (Default = '00000')`** — Never block an Egyptian checkout on Zip Code! | **`OPTIONAL`** (Auto-filled if map pin or SPL short address is used). | **`HIDDEN (UAE does not use postal codes; pass '00000' silently to card processor)`**. |

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Multi-country Home & Kitchen Store on WooCommerce / Shopify selling in Egypt, KSA, and UAE.
- **Problem**:
  1. Checkout had `Postal Code` set to `Required` with a 5-digit regex; in UAE (which has no postal code system at all!) and Egypt, `22%` of users failed validation on the address step.
  2. Egyptian buyers typed only `"القاهرة - شارع عباس العقاد"` with no building/apartment or landmark, causing Bosta couriers to mark `19%` of parcels as `'Incomplete Address - Delayed'`.

### Step B: Initial Output (`المخرج الأولي`)
- **Checkout Address Reconfiguration**:
  1. Set `Postal Code` to **Hidden/Optional** (silently passing `"00000"` to 3DS card processors that require a non-null string).
  2. Added cascading `Governorate -> District` dropdown for Egypt synced with Bosta's zone IDs, plus explicit placeholder `"اسم الشارع، رقم العمارة، الدور، الشقة + أقرب علامة مميزة (مثال: بجوار...)"`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Arabic-Indic Numeral Normalization on Building/Apartment Fields (`AMP-388`)**: Ensured building and floor numbers typed in Arabic-Indic digits (`عمارة ١٤ الدور ٣ شقة ٧`) pass validation smoothly.
2. **Paired with Post-Checkout WhatsApp Location Pin (`AMP-448`)**: For KSA and Egypt COD orders, offered a 1-tap WhatsApp location pin confirmation after checkout.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Address-step abandonment dropped from `22%` to `3.4%`, and courier first-attempt delivery success rate increased by `14` percentage points.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A store removes the `Postal Code` field from the frontend HTML, but their credit-card gateway (e.g., Stripe/Checkout.com/Cybersource AVS check) rejects the backend API call because `billing_address.postal_code` was sent as `null`.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Hide the `Postal Code` input from the user on the frontend UI in Egypt and UAE, and **populate a hidden default value (`"00000"`) in the backend payload** so legacy payment-gateway schemas never throw a null-field error.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Bosta / Mylerz (Egypt), SPL / SMSA / Aramex (KSA & UAE) Courier Address Schemas** | `supported` | [Official Docs](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) (`2026-10-25`) | Egyptian couriers route by Governorate + District + Street/Building + Landmark, UAE has no postal codes, and KSA uses City + District + SPL National Address / Map Pin. | Always hide or make `Postal Code` optional on MENA checkouts and pass `'00000'` as the backend fallback. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Shipping Address Step Completion Rate (`%`) and Courier 'Incomplete Address' Exception Rate (`Target: <3%`).
- **Baseline**: Prior 30-day checkout shipping-step drop-off and courier exception log.
- **Observation Window**: 14–28 days post-deployment.
- **Interpretation Boundary**: Localizing address fields removes checkout friction and courier exceptions, while phone confirmation (`AMP-448`) ensures the customer is home at delivery time.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) — *23HubLab* (Published `2026-03-15`, Accessed `2026-10-25`): In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta.
- [Payment Gateways in Egypt 2026: Paymob, Fawry, InstaPay](https://nilexdigitalsystems.com/articles/payment-gateways-egypt-paymob-fawry-instapay) — *Nilex Digital Systems* (Published `2026-09-26`, Accessed `2026-10-25`): Details checkout UX, reconciliation, and conversion fixes for Paymob, Fawry reference codes, Meeza, InstaPay, and valU in Egypt.
