# End-to-End Worked Example & Failure Recovery — `FW-026` (`AMP-124`)

- **Framework**: TikTok, Meta & Snapchat AIGC Disclosure & C2PA Metadata Compliance Checklist
- **العنوان بالعربية**: قائمة فحص الإفصاح الإلزامي عن المحتوى المولد بالذكاء الاصطناعي (`AIGC`) وبصمة `C2PA` على تيك توك وميتا وسناب شات
- **Selected Artifact Type**: `CHECKLIST`
- **Disclaimer**: *All scenarios, brand names, SKU codes, and metrics below are original, realistic illustrative examples for MENA practitioner training and are never represented as verified client outcomes.*

## 1. Realistic Sample Brief / Input (`المدخلات وموجز الحالة العملية`)

- **Campaign**: Dubai E-Commerce Electronics Store publishing a 15-second vertical ad generated with `Veo 3.1` (photorealistic lifestyle scene in Dubai Marina) and an `ElevenLabs` Gulf Arabic voiceover on TikTok and Instagram Reels.

## 2. Initial Generated / Completed Output (`المخرج الأولي عند تطبيق الأداة`)

- **Audit Classification**: Category A (`Photorealistic Scene + Synthetic Voiceover`).
- **Required Toggles**:
  - TikTok `AI-generated content` toggle: `ON`
  - Meta `Made with AI` toggle: `ON`
  - Commercial disclosure (`#إعلان` / Paid Ad header): `ON`

## 3. Human Review & Localization/Technical Edits (`المراجعة البشرية والتعديلات الرقابية والتقنية`)

1. **Verified Non-Deceptive Claim**: Confirmed the Veo 3.1 lifestyle clip shows atmospheric product context while the actual physical gadget close-up uses real studio photography so buyers see the exact physical ports and screen (`AMP-065`).
2. **Checked C2PA Retention**: Exported directly from Premiere without running any metadata-stripping tool.

## 4. Final Reviewed Example Outcome (`النتيجة النهائية الجاهزة للتنفيذ`)

- Video published across TikTok and Instagram Reels with native `AI-generated content` label enabled, passing automated moderation with zero reach penalties.

## 5. What Can Go Wrong & Specific Correction / Fallback (`حالة الفشل المحتملة وخطة الإنقاذ والبديل`)

- **Common Failure Mode (`ما الذي قد يسير بشكل خاطئ؟`)**:
  A creator uploads a realistic `HeyGen` avatar speaking Saudi dialect on TikTok Shop without toggling `AI-generated content` ON; TikTok's C2PA/audio detector flags the video within 2 hours, removes the audio/video, and issues an account strike.
- **Specific Correction & Non-AI / Platform Fallback (`الإصلاح المحدد والبديل الآمن`)**:
  Always toggle `AI-generated content` ON at upload time for any realistic AI face, scene, or cloned voice; if using TikTok Symphony Studio, leave the automatic Symphony AIGC badge intact.
