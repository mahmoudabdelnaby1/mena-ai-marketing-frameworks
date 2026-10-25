# Evidence Register & Source Boundaries — `FW-046` (`AMP-234`)

- **Framework Title (EN)**: Arabic Email Subject-Line Byte-Length & Anti-Spam Filter Prompt Template
- **عنوان الأصل (AR)**: قالب صياغة عناوين رسائل البريد الإلكتروني العربية (ضبط طول البايتات `UTF-8` وتجنب فلاتر السبام والوعود المضللة)
- **Channel**: Email Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-072` | [Translating Dialects between ChatGPT and DeepSeek](https://f1000research.com/articles/14-694) | F1000Research | `2025-07-16` | `2026-10-25` | `PEER_REVIEWED_RESEARCH` (`RESEARCH_FINDING`) | Demonstrates measurable accuracy drops and cultural/idiomatic errors when LLMs translate between English and regional Arabic dialects. | Peer-reviewed evaluation of ChatGPT and DeepSeek on Arabic dialects. |
| `SRC-085` | [Solving Right-to-Left Email Rendering Problems in Gmail and Outlook](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) | MailTester | `2026-09-24` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents how missing dir='rtl' attributes, inline CSS overrides, and mixed bidirectional strings cause broken Arabic email rendering in Outlook and Gmail across Klaviyo, HubSpot, and Mailchimp. | RTL email HTML/MJML rendering and deliverability. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-085` | [Solving Right-to-Left Email Rendering Problems in Gmail and Outlook](https://mailtester.com/blog/right-to-left-email-rendering-problems-gmail-outlook/) | MailTester | `2026-09-24` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Unicode BiDi standard (UAX #9) sets paragraph direction from the first strong directional character; starting an Arabic subject line with an Arabic word ensures proper RTL inbox alignment. | Fallback: If a subject line must begin with a Latin brand name, prepend the Unicode Right-to-Left Mark (`‏`) as the first character. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Email Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not put more than 1 emoji in an Arabic subject line, never use `RE:` / `رد:` or `FWD:` on a marketing email to fake a personal reply, and never exceed 42 Arabic characters. / لا تضع أكثر من رمز تعبيري واحد (`Emoji`) في العنوان، ولا تضف بادئة `رد:` أو `RE:` للإيهام بأنها مراسلة شخصية، ولا تتجاوز 42 حرفاً عربياً.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Email Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
