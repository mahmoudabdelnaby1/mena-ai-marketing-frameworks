# FW-049: Transactional vs. Promotional Email Template Separation Checklist (Saudi & UAE PDPL Compliance)
## قائمة فحص الفصل بين رسائل المعاملات (`الفواتير وتأكيد الطلب`) والرسائل الترويجية (الامتثال لنظام `PDPL` السعودي والإماراتي)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-247`, `AMP-257`, `AMP-267`, `AMP-277`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: CRM Manager, Email Marketing Specialist, Lifecycle Marketer, Data Privacy Officer
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Keep transactional order confirmations, ZATCA/ETA tax invoices, and shipping updates strictly free of unconsented promotional upsell banners so they remain lawful under contract-fulfillment basis and stay in the Primary inbox tab.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: الفصل التام بين رسائل المعاملات التشغيلية (تأكيد الطلب، الفاتورة الضريبية، تتبع الشحنة) والعروض الترويجية لضمان مشروعيتها النظامية وعدم تصنيفها كرسائل تسويقية غير مصرح بها.
- **Why `CHECKLIST` Fits This User Job (EN)**: E-commerce plugins and AI lifecycle builders frequently inject 'Buy 2 More at 30% Off!' promotional carousels into transactional Order Confirmation and Shipping Update emails sent to customers who NEVER opted into marketing; under Saudi PDPL Art. 25 and UAE PDPL Art. 4/17, adding predominant promotional content converts a contract-fulfillment notice into unlawful unconsented direct marketing (and pushes receipts into Gmail's Promotions tab).
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تضيف العديد من القوالب الجاهزة عروضاً ترويجية («اشترِ قطعتين إضافيتين بخصم 30%!») داخل رسائل تأكيد الطلب والفواتير المرسلة لعملاء لم يوافقوا على الرسائل التسويقية؛ مما يحول الرسالة نظامياً إلى تسويق مباشر غير مصرح به وينقل الفواتير إلى تبويب العروض الترويجية في Gmail.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when auditing automated `Order Confirmation`, `ZATCA/ETA e-Invoice`, `Shipping Dispatch`, `Password Reset`, or `Warranty Registration` email/SMS/WhatsApp templates.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند مراجعة قوالب تأكيد الطلب، الفواتير الضريبية الإلكترونية، تحديثات الشحن، أو استعادة كلمة المرور.
- **When NOT to Use It (EN)**: Do not send a single template to all buyers if it contains cross-sell discounts; either strip promotional blocks from transactional receipts OR conditionally render them ONLY when `customer.marketing_consent == true`.
- **متى لا تستخدم هذه الأداة (AR)**: لا ترسل قالباً موحداً يحتوي على عروض بيع متقاطع (`Cross-sell`) لجميع المشترين؛ إما أن تجعل رسالة الفاتورة خدمية خالصة بنسبة 100% أو تقصر ظهور العرض الإضافي بشرط برمجي (`if marketing_consent == true`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. All active Transactional Email & WhatsApp Templates (`Order Confirmed`, `Shipped`, `Delivered`, `Refunded`)
2. ESP Conditional Rendering syntax (`{% if person.marketing_consent == true %}` in Klaviyo/Liquid)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Transactional Email Purity & Conditional Consent Checklist

#### 1. The 4-Point Transactional Purity Audit
- [ ] **Check 1 — Primary Purpose & Content Ratio (`100% Operational for Unconsented Buyers`)**:
  - For any customer where `marketing_consent != true`, the Order Confirmation and Shipping Receipt MUST contain **zero promotional discount codes, zero 'Recommended Products to Buy Next' carousels, and zero seasonal sale banners**.
  - Allowed content: Order number, itemized receipt, VAT breakdown (`15% ZATCA` / `5% UAE` / `14% Egypt`), delivery address, courier tracking link, and customer support / return instructions.
- [ ] **Check 2 — Separate Sending Stream & Subdomain (`transactional.brand.sa` vs. `offers.brand.sa`)**:
  - Route transactional receipts through a dedicated transactional IP/subdomain (`Postmark` / `SendGrid Transactional` / `Klaviyo Transactional Flag`) so a promotional campaign spike never delays OTPs or ZATCA tax invoices.
- [ ] **Check 3 — Liquid Conditional Gate (If You Want to Show a Post-Purchase Offer ONLY to Opted-In Subscribers)**:
```liquid
{% if person.marketing_consent == true and person.consent_timestamp != blank %}
  <!-- This block renders ONLY for buyers with verified prior marketing consent -->
  <table role="presentation" dir="rtl" width="100%" style="margin-top:24px; border-top:1px solid #E5E7EB; padding-top:16px;">
    <tr>
      <td dir="rtl" align="right" style="direction:rtl; text-align:right; font-size:14px;">
        لأنك مشترك في قائمتنا البريدية: استخدم كود <bdi>{{ vip_repeat_code }}</bdi> لخصم 10% على طلبك القادم.
        <a href="{{ unsubscribe_url }}">إلغاء اشتراك العروض</a>
      </td>
    </tr>
  </table>
{% endif %}
```
- [ ] **Check 4 — WhatsApp Utility vs. Marketing Separation (`AMP-441`)**:
  - Never add a promotional upsell line inside a WhatsApp `UTILITY` order-confirmation template—Meta's automated reviewer will reject the template or reclassify it to the higher-priced `MARKETING` category!

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi PDPL Art. 25, UAE PDPL Art. 4/17 & Meta WhatsApp Utility Template Policy** | `supported` | [Official Reference](https://voctos.net/saudi-pdpl-marketing-compliance/) (`2026-10-25`) | Contract fulfillment allows sending order receipts and shipping notices without separate marketing consent ONLY if the communication remains strictly operational and non-promotional. | Send cross-sell offers in a separate marketing email filtered exclusively to `marketing_consent == true`. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-247`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Strict separation of transactional vs marketing sender domains and template payloads.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-257`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Strict separation of transactional vs marketing sender domains and template payloads.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-267`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Strict separation of transactional vs marketing sender domains and template payloads.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-277`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Strict separation of transactional vs marketing sender domains and template payloads.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Store**: Riyadh & Dubai Home Decor Store on Shopify + Klaviyo.
- **Problem**: The default AI-designed `Order Confirmation` email had a huge `"🔥 25% OFF YOUR NEXT ORDER + 4 RECOMMENDED SOFAS"` banner taking up 60% of the email above the fold, sent to 100% of buyers (including 62% who did not tick the marketing opt-in box). Gmail routed the store's tax receipts into the `Promotions` tab and unconsented buyers complained.
- **Human Review & Key Edits Applied**: 1. **ZATCA e-Invoice QR Check**: Moved the itemized invoice summary and downloadable PDF link directly to the top of the `Order Confirmation` email so Saudi and UAE buyers see their receipt immediately.
2. **Verified Primary Tab Placement**: Tested the cleaned receipt on Gmail iOS/Web—landed 100% in the `Primary` inbox tab.
- **Final Usable Output**: - Pure transactional receipt template live for all buyers (`Primary` tab placement), with promotional cross-sells strictly isolated to opted-in subscribers (`marketing_consent == true`).
- **What Can Go Wrong**: A merchant adds `'تابعوا عروض الجمعة البيضاء بخصم 50% على الرابط...'` to the footer of their WhatsApp `UTILITY` shipping-update template; Meta automatically reclassifies the template from `UTILITY` to `MARKETING`, increasing per-message cost and blocking delivery to users capped on marketing messages (`AMP-441`).
- **Correction & Fallback**: Keep transactional Email, SMS, and WhatsApp `UTILITY` templates **100% free of promotional links, discount codes, or cross-sell calls to action**.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Transactional Email Primary-Tab Placement Rate (`Target: 100%`), Order Receipt Open Rate, and Zero PDPL/Meta Utility-Template violations.
- **Baseline Definition**: Pre-fix receipt open rate and Gmail tab placement.
- **Observation Window**: 7 days post-deployment. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Separating transactional and promotional templates protects legal compliance and receipt deliverability; cross-sell revenue is captured safely via the dedicated opt-in flow.
