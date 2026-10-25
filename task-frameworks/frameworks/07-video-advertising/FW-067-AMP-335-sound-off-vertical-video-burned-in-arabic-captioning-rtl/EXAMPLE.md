# End-to-End Worked Example & Failure Recovery — `FW-067` (`AMP-335`)

- **Framework**: Sound-Off Vertical Video Burned-In Arabic Captioning & RTL Subtitle Styling Checklist
- **العنوان بالعربية**: قائمة فحص الكابشن العربي المدمج (`Burned-In Arabic Captions`) لإعلانات الفيديو العمودية في وضع الصامت (`Sound-Off`)
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Video**: 15-second Egyptian & Saudi E-Commerce Gadget Reel.
- **Broken Auto-Caption Output from CapCut**:
  - Card 1 (`18` words on 3 tiny lines at the very bottom `Y: 1720px`, covered by Instagram username): `"لو بتدور على شاحن سريع للموبايل بتاعك في مصر والسعوديه جرب الشاحن ده دلوقتي ب ٢٠٠ ريال وتبي"` *(Spelled `Tabby` as `تبي`, used tiny unstroked font, and placed inside the dead UI zone).*

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Corrected Burned-In Caption Track (`Cairo ExtraBold 54pt`, Dark Pill at `Y: 1180px`)**:
  - `[00:00 – 00:02]`: **`شاحن جيب بحجم الكف.. يشحن جوالك 50% في 20 دقيقة ⚡`**
  - `[00:02 – 00:04]`: **`سعره 199 ر.س (شامل الضريبة)`**
  - `[00:04 – 00:06]`: **`قسّمه على 4 دفعات مع تابي وتمارا بدون فوائد`**

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Muted Playback Test**: Watched the entire 15-second export with laptop/phone audio **100% muted** to confirm a viewer in a quiet meeting understands the problem, demo, price (`199 ر.س`), and CTA without hearing a single word.
2. **Checked RTL Exclamation/Lightning Emoji**: Placed `⚡` at the left end of the RTL line so it didn't shift line centering.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Exported `1080x1920` master video with 100% legible, sound-off-complete Arabic captions positioned inside the safe zone.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A video editor burns in Arabic captions at `Y: 1650px` AND turns on TikTok/Instagram's automatic closed captions (`CC`); the platform overlays its white auto-captions directly on top of the burned-in captions, creating an unreadable double-text mess.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Position burned-in captions at **`Y: 1100px – 1280px`** (upper-lower-third safe zone) and disable redundant overlay auto-captions (or upload a clean `.srt` file only for platforms where burned-in text isn't used).
