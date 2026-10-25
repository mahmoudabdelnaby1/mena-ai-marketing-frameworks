# Evidence Register & Source Boundaries — `FW-050` (`AMP-238`)

- **Framework Title (EN)**: Arabic Email Typography, Web-Safe Font Stack & Line-Height Checklist (Preventing Tiny Times New Roman Fallback in Outlook)
- **عنوان الأصل (AR)**: قائمة فحص خطوط البريد الإلكتروني العربية (`Font Stack`) وتباعد الأسطر لمنع الارتداد لخط `Times New Roman` غير المقروء في Outlook
- **Channel**: Email Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-065` | [Top Arabic Content Writing Mistakes Hurting Your SEO Rankings](https://www.aiqalam.com/en/blog/top-arabic-content-writing-mistakes-hurting-your-seo-rankings) | AI Qalam | `2026-10-24` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents poor RTL text alignment, unnatural AI phrasing, and morphological keyword stuffing in Arabic content. | Arabic SEO content writing. |
| `SRC-085` | [Solving Right-to-Left Email Rendering Problems in Gmail and Outlook](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) | MailTester | `2026-09-24` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents how missing dir='rtl' attributes, inline CSS overrides, and mixed bidirectional strings cause broken Arabic email rendering in Outlook and Gmail across Klaviyo, HubSpot, and Mailchimp. | RTL email HTML/MJML rendering and deliverability. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-085` | [Solving Right-to-Left Email Rendering Problems in Gmail and Outlook](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) | MailTester | `2026-09-24` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`plan/region dependent`) | Windows Outlook ignores external `@font-face` web fonts and falls back to `Times New Roman` unless `<!--[if mso]>` specifies a system-installed Arabic sans-serif font (`Segoe UI` / `Tahoma`). | Fallback: Always include `'Segoe UI', Tahoma, Arial, sans-serif` in inline `font-family` and `<!--[if mso]>` blocks. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Email Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never set Arabic email body text smaller than `16px` or `line-height` smaller than `1.65`, and never use `letter-spacing` (`tracking > 0`) on Arabic text (positive `letter-spacing` breaks connected Arabic cursive ligatures!). / لا تجعل حجم خط المتن العربي في البريد أقل من `16px` ولا تباعد الأسطر أقل من `1.65`، ويُحظر تماماً وضع تباعد بين الحروف (`letter-spacing > 0`) لأنه يقطع اتصال الحروف العربية!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Email Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
