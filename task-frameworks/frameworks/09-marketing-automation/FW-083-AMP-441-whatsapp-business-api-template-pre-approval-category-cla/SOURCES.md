# Evidence Register & Source Boundaries — `FW-083` (`AMP-441`)

- **Framework Title (EN)**: WhatsApp Business API Template Pre-Approval & Category Classification Checklist (`MARKETING` vs. `UTILITY`)
- **عنوان الأصل (AR)**: قائمة فحص اعتماد قوالب `WhatsApp Business API` ومنع الرفض الآلي (تصنيف `Marketing` مقابل `Utility` وأمثلة المتغيرات `{{1}}`)
- **Channel**: Marketing Automation
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-079` | [WhatsApp templates rejected: 7 errors Meta sees](https://asisteclick.com/en/blog/plantillas-whatsapp-rechazadas-meta-7-errores/) | AsisteClick | `2026-04-30` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Reports that roughly 1 in 3 WhatsApp Business API templates fail review due to category mismatch, adjacent/trailing variables, URL shorteners, or vague promotional copy. | WhatsApp Business API template approval. |
| `SRC-080` | [Why WhatsApp Rejects Your Message Templates — and How to Get Approved on the First Try](https://www.tenreply.com/blog/whatsapp-template-rejected-how-to-get-approved) | Tenreply | `2026-07-19` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details technical Meta review checks: mandatory realistic sample values for {{1}}, domain-verified URLs, single clear purpose, and post-approval quality monitoring. | WhatsApp Cloud API operations. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-009` | [Template messages - Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) | Meta for Developers | `2026-04-23` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Business-initiated WhatsApp messages outside the 24-hour customer service window require pre-approved templates with strict variable syntax and category matching. | Applies to WhatsApp Business Platform / Cloud API. |
| `SRC-010` | [Pricing on the WhatsApp Business Platform | Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing) | Meta for Developers | `2026-09-30` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Differentiates rates across Marketing, Utility, Authentication, and Service messages by recipient country code (including Egypt and Saudi Arabia). | Misclassifying Marketing copy as Utility causes rejection or enforcement blocks. |
| `SRC-011` | [Marketing templates | Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/marketing-templates) | Meta for Developers | `2026-06-17` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Defines required components, headers, body variables, and CTA button constraints for promotional WhatsApp templates. | Requires opt-in and quality rating maintenance. |
| `SRC-009` | [Template messages - Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages) | Meta for Developers | `2026-04-23` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Meta enforces automated template review checking category alignment (Marketing vs Utility vs Authentication), sequential variable syntax, mandatory sample values, and domain transparency. | Fallback: Never mix promotional copy into `UTILITY` templates; create two separate templates instead. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Marketing Automation mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never submit a template containing a discount code, cross-sell offer, cart recovery nudge, or win-back message under the `UTILITY` category—Meta's classifier will reject it or force-reclassify it to `MARKETING`. / لا تقم أبداً بتصنيف رسالة تحتوي على كود خصم أو استرداد سلة متروكة أو عرض ترويجي تحت فئة `UTILITY`؛ لأن نظام ميتا سيرفضها فوراً أو يحولها قسرياً إلى `MARKETING`.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Marketing Automation before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
