# End-to-End Worked Example & Failure Recovery — `FW-065` (`AMP-333`)

- **Framework**: Short-Form Gulf Snapchat Creative Hypothesis & Storyboard Template
- **العنوان بالعربية**: قالب فرضية إبداعية ولوحة مشاهد قصيرة لإعلانات سناب شات في الخليج
- **Selected Artifact Type**: `EXTEND_EXISTING`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Brand**: Saudi Home Fragrance & Diffuser Store on Salla (`Smart Waterless Car & Majlis Diffuser`, `179 SAR` incl. VAT).
- **Previous 25-Second Ad**: Opened with 3 seconds of a spinning gold logo, followed by 10 seconds of slow B-roll before mentioning the product at Second 14. Result: `89%` of Snapchat viewers swiped away before Second 3 (`Average Watch Time: 1.4s`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Re-Engineered 5.5-Second Gulf Snapchat Ad**:
  - **`[0.0s–1.2s]`**: Instant dense aromatic mist burst from the anodized diffuser placed in a luxury car cupholder (`VO: "فواحة ذكية بدون موية تغير جو سيارتك ومجلسك!"`).
  - **`[1.2s–3.5s]`**: Hand taps the digital intensity button (`VO: "بـ مية وتسعة وسبعين ريال بس ومع تابي وتمارا."` | Overlay: `179 ر.س شامل الضريبة | 4 دفعات تابي`).
  - **`[3.5s–5.5s]`**: Clean hero hold (`VO: "ارفع الشاشة واطلبها الحين!"`).

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Word Count Trim**: Confirmed spoken script is exactly `16` short Arabic words (`5.2 seconds` spoken at energetic Gulf cadence).
2. **Right-Hand Etiquette Check (`AMP-336`)**: Confirmed the hand holding/tapping the diffuser in the prompt is explicitly the **right hand**.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- 5.5-second Snapchat Gulf Commercial & Story Ad pack delivered with Sec 1 action hook, Sec 2–3 SAR/Tabby offer, and 3x improvement in Offer-View Rate.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An editor exports a 6-second Snapchat video where the first `0.5` seconds is a black frame (`Fade from Black`); Snapchat uses Frame 0 as the preload thumbnail, causing viewers to see a black screen as the story loads and immediately tap past it.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Enforce the **Frame-Zero Rule**: Frame `00:00:00` (the very first frame of the video file) MUST be a bright, fully lit action frame showing the product in motion—zero black frames, zero fade-ins!
