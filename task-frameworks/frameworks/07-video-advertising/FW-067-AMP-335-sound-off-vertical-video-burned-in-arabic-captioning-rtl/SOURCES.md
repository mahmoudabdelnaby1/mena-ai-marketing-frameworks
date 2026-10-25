# Evidence Register & Source Boundaries — `FW-067` (`AMP-335`)

- **Framework Title (EN)**: Sound-Off Vertical Video Burned-In Arabic Captioning & RTL Subtitle Styling Checklist
- **عنوان الأصل (AR)**: قائمة فحص الكابشن العربي المدمج (`Burned-In Arabic Captions`) لإعلانات الفيديو العمودية في وضع الصامت (`Sound-Off`)
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-059` | [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) | Esafqa | `2026-10-09` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks. | Snapchat e-commerce ads in KSA and GCC. |
| `SRC-065` | [Top Arabic Content Writing Mistakes Hurting Your SEO Rankings](https://www.aiqalam.com/en/blog/top-arabic-content-writing-mistakes-hurting-your-seo-rankings) | AI Qalam | `2026-10-24` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents poor RTL text alignment, unnatural AI phrasing, and morphological keyword stuffing in Arabic content. | Arabic SEO content writing. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-059` | [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) | Esafqa | `2026-10-09` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Auto-captioning ASR supports Arabic but requires manual proofreading for dialect terms, brand names (Tabby, Tamara, InstaPay, Salla), and compact price digits. | Fallback: Always run the '100% Muted Playback Test' before approving any social video ad. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not rely on platform auto-generated closed captions (`CC`) alone—many users have CC turned off, and automated ASR frequently mangles Saudi/Egyptian brand names and prices. / لا تعتمد على الترجمة التلقائية للمنصة (`Auto CC`) وحدها؛ بل ادمج الكابشن العربي المصحح داخل ملف الفيديو نفسه (`Burned-In`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
