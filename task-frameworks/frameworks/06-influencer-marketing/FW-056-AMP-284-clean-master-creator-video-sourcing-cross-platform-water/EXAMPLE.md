# End-to-End Worked Example & Failure Recovery — `FW-056` (`AMP-284`)

- **Framework**: Clean Master Creator Video Sourcing & Cross-Platform Watermark Stripping Prevention Checklist
- **العنوان بالعربية**: قائمة فحص استلام النسخ الخام (`Clean Master`) لفيديوهات المؤثرين ومنع إعادة نشر العلامات المائية في إعلانات سناب شات وتيك توك
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: UAE & KSA Modest Fashion Brand repurposing 8 creator TikTok videos into paid Snapchat Commercials and Instagram Reels Ads.
- **Problem**: Media buyer downloaded the 8 videos from TikTok (`with bouncing @handle TikTok watermark`) and uploaded them to Snapchat Ads Manager; Snapchat rejected `6 of 8` ads for `Third-party platform watermark / branding` and the remaining 2 had terrible CTR because the TikTok watermark covered the price overlay.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Remediation**:
  1. Collected the original `Clean_Raw_Master_1080x1920.mp4` files via Google Drive from all 8 creators.
  2. Trimmed a 1.5-second CapCut logo tail discovered at the end of Creator #4's video.
  3. Replaced a trending copyrighted TikTok song on Creator #6's video with a clean voice-only track (`AMP-065`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Blocked WhatsApp Video Transfers**: Instructed account managers that creators sending videos via regular WhatsApp chat (`which downscales 1080p to 480p/720p low bitrate`) must resend as a **Google Drive link** or **WhatsApp Document (`مستند`)** to preserve full `1080x1920` resolution.
2. **Added Safe-Zone Native Overlays**: Placed Snapchat-native swipe-up price stickers on the clean master files.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `8 / 8` clean master `1080x1920` videos approved on Snapchat Ads Manager and Meta Reels Ads with zero watermark rejections and crisp HD quality.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A media buyer uses an AI watermark-inpainting tool to blur out a TikTok logo in the top-left and bottom-right corners; Snapchat's ad review still flags the blurry pulsing smudge as a modified watermark and rejects the ad.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Never use AI blur/inpainting to hide platform watermarks on paid ads; tie final creator invoice settlement strictly to delivery of the pre-upload `Clean_Raw_Master_1080x1920.mp4` file.
