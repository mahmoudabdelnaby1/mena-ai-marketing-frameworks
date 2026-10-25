# Evidence Register & Source Boundaries — `FW-056` (`AMP-284`)

- **Framework Title (EN)**: Clean Master Creator Video Sourcing & Cross-Platform Watermark Stripping Prevention Checklist
- **عنوان الأصل (AR)**: قائمة فحص استلام النسخ الخام (`Clean Master`) لفيديوهات المؤثرين ومنع إعادة نشر العلامات المائية في إعلانات سناب شات وتيك توك
- **Channel**: Influencer Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-059` | [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) | Esafqa | `2026-10-09` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks. | Snapchat e-commerce ads in KSA and GCC. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-013` | [Snap Advertising Policies - Snap Inc.](https://www.snap.com/ad-policies) | Snap Inc. | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Enforces country-specific creative, cultural sensitivity, financial, and health/cosmetic claim rules across Saudi Arabia, UAE, and Egypt. | Covers both ad creative and landing page content. |
| `SRC-014` | [Commercials - Snap for Developers](https://developers.snap.com/marketing-api/Ads-API/commercials) | Snap Inc. | `2026-05-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Technical creative eligibility constraints for non-skippable Snap Commercials and AdSquad targeting. | API and format specification. |
| `SRC-013` | [Snap Advertising Policies - Snap Inc.](https://www.snap.com/ad-policies) | Snap Inc. | `2026-06-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Snapchat Ad Policies and Meta/Instagram Reels guidelines prohibit or demote creatives containing third-party social platform watermarks or low-resolution re-uploads. | Fallback: Always collect `Clean_Raw_Master_1080x1920.mp4` via cloud link before publishing. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Influencer Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never screen-record a creator's published Snapchat/TikTok story or use a 'TikTok video downloader' to grab the file for paid ads—always collect the original pre-upload `.mp4`/`.mov` master file. / لا تقم أبداً بتسجيل الشاشة (`Screen Record`) لسنابة المؤثر أو تحميل الفيديو من تيك توك لاستخدامه في الإعلانات الممولة؛ اطلب دائماً الملف الأصلي قبل الرفع (`.mp4 / .mov`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Influencer Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
