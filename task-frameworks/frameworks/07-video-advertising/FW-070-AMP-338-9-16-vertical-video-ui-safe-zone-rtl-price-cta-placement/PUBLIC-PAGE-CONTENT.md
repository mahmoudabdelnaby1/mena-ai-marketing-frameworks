# 9:16 Vertical Video UI Safe-Zone & RTL Price/CTA Placement Checklist (TikTok, Reels & Snapchat)
## <span dir="rtl">قائمة فحص «المناطق الآمنة» (`9:16 Safe Zones`) لمواضع النصوص والأسعار والشعارات في إعلانات تيك توك وريلز وسناب شات</span>

> **Asset ID**: `FW-070` (`AMP-338`) | **Artifact Type**: `CHECKLIST` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Place all Arabic headlines, prices (`SAR/AED/EGP`), promo codes, and `#إعلان` badges strictly inside the unobstructed `1080x1310` central safe canvas so platform UI buttons, captions, and profile icons never cover your offer.
- **AR**: <span dir="rtl">وضع جميع العناوين والأسعار وأكواد الخصم ووسم `#إعلان` داخل المساحة المركزية الآمنة (`1080x1310`) في الفيديو العمودي لمنع أزرار التفاعل وأسماء الحسابات في تيك توك وريلز وسناب شات من تغطية العرض.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before exporting any `9:16` (`1080x1920`) vertical video or static story ad for TikTok, Instagram Reels, Facebook Reels, YouTube Shorts, or Snapchat.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل تصدير أي فيديو عمودي أو تصميم قصة (`1080x1920`) لإعلانات تيك توك أو إنستغرام ريلز أو سناب شات أو يوتيوب شورتس.</span>
- **When NOT to Use It (EN)**: Never right-align Arabic text with less than `150px` right margin on TikTok/Reels/Shorts—because RTL Arabic starts on the right edge, right-edge UI icons clip the **first word** of your sentence!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تحاذِ النص العربي لأقصى اليمين بهامش أقل من `150px` في تيك توك وريلز وشورتس؛ لأن اللغة العربية تبدأ من اليمين، وأيقونات التفاعل اليمنى ستغطي الكلمات الأولى من الجملة!</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- `1080x1920` (`9:16`) Video / Story Composition in Premiere, After Effects, CapCut, or Canva
- Transparent PNG Safe-Zone Guide Overlay (`Top 220px`, `Bottom 420px`, `Right 150px`, `Left 90px` blocked)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Universal `1080x1920` (`9:16`) MENA RTL Safe-Zone Pixel Map

#### 1. Blocked Dead Zones vs. Universal Safe Canvas (`1080px × 1920px`)
```text
+---------------------------------------------------+ Y = 0px (Top Edge)
|          DEAD ZONE TOP (Y: 0 to 220px)            | <- Blocked by Snapchat Header, Story Progress Bars,
|   [Place NOTHING above Y: 220px! Put #إعلان at    |    IG/TikTok Search/Live Icons & Dynamic Island.
|    Y: 230–280px inside the top safe border]       |
+------+------------------------------------+-------+ Y = 220px
|      |                                    |       |
| DEAD |     UNIVERSAL RTL SAFE CANVAS      | DEAD  | <- CRITICAL RTL TRAP:
| LEFT |     Width: 840px (X: 90 to 930)    | RIGHT |    Right 150px (X: 930–1080) is covered by
| 90px |     Height: 1280px (Y: 220 to 1500)| 150px |    TikTok / Reels / Shorts Like, Comment,
|      |                                    |       |    Save & Share buttons!
|      |  * Top Hook Text: Y = 300–520px    | (NO   |    If you flush RTL Arabic to X=1020, the
|      |  * Hero Product:  Y = 520–1080px   | TEXT  |    FIRST WORD of every Arabic line is hidden!
|      |  * Captions/Price:Y = 1080–1420px  | HERE!)|
|      |                                    |       |
+------+------------------------------------+-------+ Y = 1500px
|        DEAD ZONE BOTTOM (Y: 1500 to 1920px)       | <- Blocked by TikTok/Reels Caption, Audio Ticker,
|   [Bottom 420px: Covered by 'Shop Now / اطلب الآن'|    and Snapchat Swipe-Up / Sponsored Pill!
|    CTA Button, Account Handle & Ad Description]   |
+---------------------------------------------------+ Y = 1920px (Bottom Edge)
```

#### 2. Pre-Export 4-Point Safe-Zone Checklist
- [ ] **Check 1 — Right-Edge RTL Margin (`X <= 920px`)**: Confirm all right-aligned or centered Arabic text boxes stay strictly left of `X = 920px` (at least `160px` inset from the right border of a `1080px` frame) so right-rail engagement icons never cover the start of the Arabic sentence.
- [ ] **Check 2 — Bottom Offer & Subtitle Ceiling (`Y <= 1450px`)**: Confirm all burned-in subtitles (`AMP-335`), price tags (`299 ر.س`), and promo codes (`SARA10`) sit between `Y = 1080px` and `Y = 1440px`—never below `Y = 1500px`.
- [ ] **Check 3 — Top Disclosure Placement (`Y = 230px to 290px`)**: Place `#إعلان` (`AMP-287`) and brand logo at `Y = 240px` (safely below Snapchat/IG top story bars at `Y: 0–210px`).

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Asset**: `1080x1920` TikTok & Instagram Reels Ad for a Cairo & Riyadh Sneaker Store.
- **Problem**: Editor placed the promo code box `"استخدم كود KICKS20 لخصم 20%"` at `Y: 1680px` (bottom of frame) and right-aligned the Arabic benefit bullets at `X: 1040px` (`40px` from the right edge). On live TikTok and Reels, the Shop Now button completely hid the promo code and the Like/Comment buttons covered the word `"استخدم"` and `"مجاناً"` on the right edge!

### Step B: Initial Output (`المخرج الأولي`)
- **Coordinate Adjustment**:
  1. Moved Promo Code & Price card up from `Y: 1680px` to **`Y: 1260px`**.
  2. Centered the benefit pills inside `X: 120px – 900px` (leaving `180px` clearance on the right edge for TikTok/Reels icons).
  3. Placed `#إعلان` pill at `X: 540px, Y: 250px`.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Created Reusable Transparent Safe-Zone PNG**: Exported a semi-transparent red-bordered `1080x1920_MENA_RTL_SafeZone_Guide.png` template layer locked as the top guide track in CapCut and Premiere Pro (toggled hidden before final export).
2. **Verified Across All 3 Placements**: Checked in Meta Ads Manager, TikTok Ads Manager, and Snapchat Ad Preview tools—`0%` text occlusion.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- `100%` of on-screen Arabic headlines, prices, and promo codes unobstructed across TikTok, Instagram Reels, YouTube Shorts, and Snapchat.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A designer uses a standard Western LTR safe-zone template where the left margin is wide and the right margin is narrow (assuming short LTR ragged-right line endings on the right); when RTL Arabic is typed into that box, the critical beginning of every Arabic line starts on the right edge right underneath the heart/comment icons.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Remember the **RTL Mirror Asymmetry**: in English LTR, the right edge only holds trailing line-ends; in **Arabic RTL, the right edge (`X: 930–1080px`) is where every single line BEGINS**! Always keep a minimum **`150px–160px` right margin** on vertical Arabic videos.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **TikTok, Instagram Reels & Snapchat 9:16 UI Overlay Specifications** | `supported` | [Official Docs](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) (`2026-10-25`) | All three vertical video platforms overlay right-rail interaction buttons and bottom-third account/CTA drawers over `1080x1920` video assets. | Center-align compact Arabic caption pills inside `X: 140..900, Y: 240..1450`. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero UI-occluded text elements in pre-launch ad preview QA and improved Promo-Code Redemption & CTR.
- **Baseline**: Audit of active vertical video ads in Ads Manager preview.
- **Observation Window**: Enforced on 100% of vertical video exports.
- **Interpretation Boundary**: Safe-zone placement guarantees the viewer can read your offer and code, while offer strength drives redemption.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) — *Esafqa* (Published `2026-10-09`, Accessed `2026-10-25`): Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks.
