# End-to-End Worked Example & Failure Recovery — `FW-070` (`AMP-338`)

- **Framework**: 9:16 Vertical Video UI Safe-Zone & RTL Price/CTA Placement Checklist (TikTok, Reels & Snapchat)
- **العنوان بالعربية**: قائمة فحص «المناطق الآمنة» (`9:16 Safe Zones`) لمواضع النصوص والأسعار والشعارات في إعلانات تيك توك وريلز وسناب شات
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Asset**: `1080x1920` TikTok & Instagram Reels Ad for a Cairo & Riyadh Sneaker Store.
- **Problem**: Editor placed the promo code box `"استخدم كود KICKS20 لخصم 20%"` at `Y: 1680px` (bottom of frame) and right-aligned the Arabic benefit bullets at `X: 1040px` (`40px` from the right edge). On live TikTok and Reels, the Shop Now button completely hid the promo code and the Like/Comment buttons covered the word `"استخدم"` and `"مجاناً"` on the right edge!

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Coordinate Adjustment**:
  1. Moved Promo Code & Price card up from `Y: 1680px` to **`Y: 1260px`**.
  2. Centered the benefit pills inside `X: 120px – 900px` (leaving `180px` clearance on the right edge for TikTok/Reels icons).
  3. Placed `#إعلان` pill at `X: 540px, Y: 250px`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Created Reusable Transparent Safe-Zone PNG**: Exported a semi-transparent red-bordered `1080x1920_MENA_RTL_SafeZone_Guide.png` template layer locked as the top guide track in CapCut and Premiere Pro (toggled hidden before final export).
2. **Verified Across All 3 Placements**: Checked in Meta Ads Manager, TikTok Ads Manager, and Snapchat Ad Preview tools—`0%` text occlusion.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- `100%` of on-screen Arabic headlines, prices, and promo codes unobstructed across TikTok, Instagram Reels, YouTube Shorts, and Snapchat.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A designer uses a standard Western LTR safe-zone template where the left margin is wide and the right margin is narrow (assuming short LTR ragged-right line endings on the right); when RTL Arabic is typed into that box, the critical beginning of every Arabic line starts on the right edge right underneath the heart/comment icons.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Remember the **RTL Mirror Asymmetry**: in English LTR, the right edge only holds trailing line-ends; in **Arabic RTL, the right edge (`X: 930–1080px`) is where every single line BEGINS**! Always keep a minimum **`150px–160px` right margin** on vertical Arabic videos.
