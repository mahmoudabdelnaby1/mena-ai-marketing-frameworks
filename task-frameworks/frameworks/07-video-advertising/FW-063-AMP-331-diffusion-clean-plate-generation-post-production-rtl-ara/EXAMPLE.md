# End-to-End Worked Example & Failure Recovery — `FW-063` (`AMP-331`)

- **Framework**: Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Workflow (Extending `video-prompt-architect`)
- **العنوان بالعربية**: مسار عمل توليد المشاهد النظيفة (`Clean-Plate`) وإضافة النصوص العربية المتجهية في المونتاج (امتداد لمهارة `video-prompt-architect`)
- **Selected Artifact Type**: `EXTEND_EXISTING`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Scenario**: Riyadh Luxury Perfume Launch (`15s` vertical ad on Kling 3.0 / Veo 3.1).
- **Previous Failure**: Prompt asked the video model for `'A golden neon sign in a Riyadh desert camp reading عطر الفخامة الملكي'`. The model rendered disconnected, reversed LTR letters (`ي ك ل م ل ا ة م ا خ ف ل ا`).

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Stage 1 Clean-Plate Prompt**:
  `Cinematic 9:16 vertical commercial shot in a luxury Riyadh desert camp at twilight. A minimalist matte-black glass perfume flacon rests on a warm sandstone plinth in the lower-center frame, leaving clean, moody amber-lit negative space in the upper-middle third of the frame. Volumetric desert breeze, warm tungsten lanterns (2800K) in soft bokeh background. Zero text, zero signage, blank glass surface ready for post-production composite. --ar 9:16`
- **Stage 2 Vector Overlay Spec**: Exported clean `.srt` / CapCut text layer with `"عطر الفخامة الملكي — إصدار الرياض الخاص"` in `IBM Plex Sans Arabic Bold` positioned at `Y: 360px`.

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified Adobe Premiere / CapCut RTL Setting**: Added reminder to enable **`World-Ready Layout / Middle Eastern & South Asian Text Engine (تفعيل محرك النصوص العربية من اليمين لليسار)`** in Premiere/After Effects before pasting the overlay table.
2. **Product Label Composite**: Composited the real vector `.png` bottle label onto the Start Frame keyframe before running Image-to-Video so the bottle label stayed 100% sharp.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Delivered cinema-grade 9:16 video ad with zero hallucinated Arabic glyphs and razor-sharp vector Arabic headlines and bottle branding.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  An editor pastes the clean Arabic text from Stage 2 into Adobe Premiere/After Effects on a machine where 'Default Composer' is set to Latin instead of 'Middle Eastern Composer'—causing Premiere itself to render the Arabic letters disconnected from left to right!
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  In Adobe Premiere Pro / After Effects: open `Preferences -> Type (أو Graphics)` -> Switch Text Engine to **`Middle Eastern and South Asian`** and set paragraph direction to `Right-to-Left` before creating the text layer.
