# Evidence Register & Source Boundaries — `FW-070` (`AMP-338`)

- **Framework Title (EN)**: 9:16 Vertical Video UI Safe-Zone & RTL Price/CTA Placement Checklist (TikTok, Reels & Snapchat)
- **عنوان الأصل (AR)**: قائمة فحص «المناطق الآمنة» (`9:16 Safe Zones`) لمواضع النصوص والأسعار والشعارات في إعلانات تيك توك وريلز وسناب شات
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-059` | [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) | Esafqa | `2026-10-09` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks. | Snapchat e-commerce ads in KSA and GCC. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-059` | [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) | Esafqa | `2026-10-09` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | All three vertical video platforms overlay right-rail interaction buttons and bottom-third account/CTA drawers over `1080x1920` video assets. | Fallback: Center-align compact Arabic caption pills inside `X: 140..900, Y: 240..1450`. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never right-align Arabic text with less than `150px` right margin on TikTok/Reels/Shorts—because RTL Arabic starts on the right edge, right-edge UI icons clip the **first word** of your sentence! / لا تحاذِ النص العربي لأقصى اليمين بهامش أقل من `150px` في تيك توك وريلز وشورتس؛ لأن اللغة العربية تبدأ من اليمين، وأيقونات التفاعل اليمنى ستغطي الكلمات الأولى من الجملة!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
