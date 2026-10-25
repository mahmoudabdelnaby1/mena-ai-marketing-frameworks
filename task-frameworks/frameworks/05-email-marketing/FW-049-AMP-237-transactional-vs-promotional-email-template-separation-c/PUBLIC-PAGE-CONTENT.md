# Transactional vs. Promotional Email Template Separation Checklist (Saudi & UAE PDPL Compliance)
## <span dir="rtl">قائمة فحص الفصل بين رسائل المعاملات (`الفواتير وتأكيد الطلب`) والرسائل الترويجية (الامتثال لنظام `PDPL` السعودي والإماراتي)</span>

> **Asset ID**: `FW-049` (`AMP-237`) | **Artifact Type**: `CHECKLIST` | **Channel**: Email Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Keep transactional order confirmations, ZATCA/ETA tax invoices, and shipping updates strictly free of unconsented promotional upsell banners so they remain lawful under contract-fulfillment basis and stay in the Primary inbox tab.
- **AR**: <span dir="rtl">الفصل التام بين رسائل المعاملات التشغيلية (تأكيد الطلب، الفاتورة الضريبية، تتبع الشحنة) والعروض الترويجية لضمان مشروعيتها النظامية وعدم تصنيفها كرسائل تسويقية غير مصرح بها.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use when auditing automated `Order Confirmation`, `ZATCA/ETA e-Invoice`, `Shipping Dispatch`, `Password Reset`, or `Warranty Registration` email/SMS/WhatsApp templates.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند مراجعة قوالب تأكيد الطلب، الفواتير الضريبية الإلكترونية، تحديثات الشحن، أو استعادة كلمة المرور.</span>
- **When NOT to Use It (EN)**: Do not send a single template to all buyers if it contains cross-sell discounts; either strip promotional blocks from transactional receipts OR conditionally render them ONLY when `customer.marketing_consent == true`.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا ترسل قالباً موحداً يحتوي على عروض بيع متقاطع (`Cross-sell`) لجميع المشترين؛ إما أن تجعل رسالة الفاتورة خدمية خالصة بنسبة 100% أو تقصر ظهور العرض الإضافي بشرط برمجي (`if marketing_consent == true`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- All active Transactional Email & WhatsApp Templates (`Order Confirmed`, `Shipped`, `Delivered`, `Refunded`)
- ESP Conditional Rendering syntax (`{% if person.marketing_consent == true %}` in Klaviyo/Liquid)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Store**: Riyadh & Dubai Home Decor Store on Shopify + Klaviyo.
- **Problem**: The default AI-designed `Order Confirmation` email had a huge `"🔥 25% OFF YOUR NEXT ORDER + 4 RECOMMENDED SOFAS"` banner taking up 60% of the email above the fold, sent to 100% of buyers (including 62% who did not tick the marketing opt-in box). Gmail routed the store's tax receipts into the `Promotions` tab and unconsented buyers complained.

### Step B: Initial Output (`المخرج الأولي`)
- **Template Remediation**:
  1. Removed the top promotional hero banner and the 4-sofa upsell grid from the base `Order Confirmation` template.
  2. Moved the repeat-purchase offer into a separate `Post-Purchase Thank You` email triggered 3 days after delivery **strictly filtered to `marketing_consent == true`**.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **ZATCA e-Invoice QR Check**: Moved the itemized invoice summary and downloadable PDF link directly to the top of the `Order Confirmation` email so Saudi and UAE buyers see their receipt immediately.
2. **Verified Primary Tab Placement**: Tested the cleaned receipt on Gmail iOS/Web—landed 100% in the `Primary` inbox tab.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Pure transactional receipt template live for all buyers (`Primary` tab placement), with promotional cross-sells strictly isolated to opted-in subscribers (`marketing_consent == true`).

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A merchant adds `'تابعوا عروض الجمعة البيضاء بخصم 50% على الرابط...'` to the footer of their WhatsApp `UTILITY` shipping-update template; Meta automatically reclassifies the template from `UTILITY` to `MARKETING`, increasing per-message cost and blocking delivery to users capped on marketing messages (`AMP-441`).
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Keep transactional Email, SMS, and WhatsApp `UTILITY` templates **100% free of promotional links, discount codes, or cross-sell calls to action**.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Saudi PDPL Art. 25, UAE PDPL Art. 4/17 & Meta WhatsApp Utility Template Policy** | `supported` | [Official Docs](https://voctos.net/saudi-pdpl-marketing-compliance/) (`2026-10-25`) | Contract fulfillment allows sending order receipts and shipping notices without separate marketing consent ONLY if the communication remains strictly operational and non-promotional. | Send cross-sell offers in a separate marketing email filtered exclusively to `marketing_consent == true`. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Transactional Email Primary-Tab Placement Rate (`Target: 100%`), Order Receipt Open Rate, and Zero PDPL/Meta Utility-Template violations.
- **Baseline**: Pre-fix receipt open rate and Gmail tab placement.
- **Observation Window**: 7 days post-deployment.
- **Interpretation Boundary**: Separating transactional and promotional templates protects legal compliance and receipt deliverability; cross-sell revenue is captured safely via the dedicated opt-in flow.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Saudi PDPL for Marketers: Email, SMS and WhatsApp Rules](https://voctos.net/saudi-pdpl-marketing-compliance/) — *VOCTOS* (Published `2026-10-01`, Accessed `2026-10-25`): Saudi PDPL enforcement requires granular per-channel opt-in logs, clear sender identity, and immediate cessation upon withdrawal of consent across email, SMS, and WhatsApp.
- [UAE PDPL Marketing Rules for Email and SMS | Kaelo Global](https://kaeloglobal.com/digital-marketing/uae-data-protection-marketing/) — *Kaelo Global* (Published `2026-10-22`, Accessed `2026-10-25`): UAE PDPL (Decree-Law 45/2021 Art. 4 & 17) has no general legitimate-interest exception for direct marketing; TDRA Spam Policy v1.1 mandates opt-in, 'AD-' sender prefix, free opt-out, a strict 9:00 PM to 7:00 AM curfew on marketing SMS, and 2-year consent record retention.
