# Sound-Off Vertical Video Burned-In Arabic Captioning & RTL Subtitle Styling Checklist
## <span dir="rtl">قائمة فحص الكابشن العربي المدمج (`Burned-In Arabic Captions`) لإعلانات الفيديو العمودية في وضع الصامت (`Sound-Off`)</span>

> **Asset ID**: `FW-067` (`AMP-335`) | **Artifact Type**: `CHECKLIST` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Add high-contrast, properly shaped RTL burned-in Arabic captions (`<= 6` words per card) to 100% of vertical video ads so silent scrollers on Snapchat, TikTok, and Instagram Reels capture the full offer without turning sound on.
- **AR**: <span dir="rtl">دمج نصوص الكابشن العربية المتصلة وعالية التباين (`6 كلمات كحد أقصى لكل شريحة`) في جميع إعلانات الفيديو العمودية لضمان وصول العرض كاملاً للمتصفحين في الوضع الصامت على سناب شات وتيك توك وإنستغرام.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use on 100% of vertical (`9:16`) and square (`1:1`/`4:5`) paid and organic video ads across Snapchat, TikTok, Instagram Reels, Facebook, and YouTube Shorts.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم في جميع إعلانات ومقاطع الفيديو العمودية والمربعة عبر سناب شات وتيك توك وإنستغرام وفيسبوك ويوتيوب.</span>
- **When NOT to Use It (EN)**: Do not rely on platform auto-generated closed captions (`CC`) alone—many users have CC turned off, and automated ASR frequently mangles Saudi/Egyptian brand names and prices.
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تعتمد على الترجمة التلقائية للمنصة (`Auto CC`) وحدها؛ بل ادمج الكابشن العربي المصحح داخل ملف الفيديو نفسه (`Burned-In`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Clean Display Script (`Column B` from `AMP-332` — unvocalized clean Arabic + compact numerals `299 ر.س`)
- Arabic Display Font (`Cairo Bold`, `Tajawal ExtraBold`, or `IBM Plex Sans Arabic Bold`)
- Safe-Zone Overlay Coordinates (`AMP-338`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Burned-In Arabic Video Captioning QA Checklist

#### 1. The 6 Rules for High-Converting Arabic Video Captions
- [ ] **Rule 1 — Max 5 to 6 Words Per Caption Card (`Single-Glance Scannability`)**:
  - Never display a 3-line 20-word paragraph on a vertical video! Break captions into **1 to 2 short lines (`4–6 words max`, displayed for `1.2s–2.0s` each)**.
- [ ] **Rule 2 — Fix Dialect & Brand ASR Hallucinations Before Burning In**:
  - Speech-to-Text (`Whisper / CapCut Auto-Captions`) routinely mis-transcribes MENA commercial terms. Audit and fix these common errors:
    - `تبي` → **`تابي`** (`Tabby`) | `تمارة` → **`تمارا`** (`Tamara`) | `انستا باي` → **`إنستاباي`** (`InstaPay`) | `سله` → **`سلة`** (`Salla`).
- [ ] **Rule 3 — Use Clean Unvocalized Arabic + Compact Digits on Screen**:
  - Even though you fed full Tashkeel and spelled-out numbers (`مِيتِينْ وتِسْعَة وتِسْعِينْ`) to the TTS voice engine (`AMP-332`), display **`299 ر.س`** (clean digits + no cluttered Tashkeel) on the visual caption card so the eye reads the price in `0.2` seconds!
- [ ] **Rule 4 — High-Contrast Pill or Stroke (`WCAG >= 7:1`)**:
  - White text (`#FFFFFF`) or Brand Yellow (`#FACC15` for key numbers) inside a rounded semi-opaque dark background pill (`#0F172ACC`, `border-radius: 12px`, `padding: 10px 20px`)—never bare white text floating over a white thobe or bright desert sky.
- [ ] **Rule 5 — Strict RTL Punctuation & BiDi Check (`AMP-231`)**:
  - Confirm question marks are Arabic (`؟` not `?`), percent signs stick to the number (`خصم 30%`), and periods/exclamation marks appear on the **left** end of the Arabic line, never jumping to the right start of the line!
- [ ] **Rule 6 — Safe-Zone Placement (`Y: 1050px to 1320px` on `1080x1920` — `AMP-338`)**:
  - Never place burned-in captions in the bottom `450px` (`Y: 1470–1920`) where TikTok/Reels captions and Snapchat's CTA bar cover them!

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Video**: 15-second Egyptian & Saudi E-Commerce Gadget Reel.
- **Broken Auto-Caption Output from CapCut**:
  - Card 1 (`18` words on 3 tiny lines at the very bottom `Y: 1720px`, covered by Instagram username): `"لو بتدور على شاحن سريع للموبايل بتاعك في مصر والسعوديه جرب الشاحن ده دلوقتي ب ٢٠٠ ريال وتبي"` *(Spelled `Tabby` as `تبي`, used tiny unstroked font, and placed inside the dead UI zone).*

### Step B: Initial Output (`المخرج الأولي`)
- **Corrected Burned-In Caption Track (`Cairo ExtraBold 54pt`, Dark Pill at `Y: 1180px`)**:
  - `[00:00 – 00:02]`: **`شاحن جيب بحجم الكف.. يشحن جوالك 50% في 20 دقيقة ⚡`**
  - `[00:02 – 00:04]`: **`سعره 199 ر.س (شامل الضريبة)`**
  - `[00:04 – 00:06]`: **`قسّمه على 4 دفعات مع تابي وتمارا بدون فوائد`**

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Muted Playback Test**: Watched the entire 15-second export with laptop/phone audio **100% muted** to confirm a viewer in a quiet meeting understands the problem, demo, price (`199 ر.س`), and CTA without hearing a single word.
2. **Checked RTL Exclamation/Lightning Emoji**: Placed `⚡` at the left end of the RTL line so it didn't shift line centering.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Exported `1080x1920` master video with 100% legible, sound-off-complete Arabic captions positioned inside the safe zone.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A video editor burns in Arabic captions at `Y: 1650px` AND turns on TikTok/Instagram's automatic closed captions (`CC`); the platform overlays its white auto-captions directly on top of the burned-in captions, creating an unreadable double-text mess.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Position burned-in captions at **`Y: 1100px – 1280px`** (upper-lower-third safe zone) and disable redundant overlay auto-captions (or upload a clean `.srt` file only for platforms where burned-in text isn't used).

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **CapCut Pro / Adobe Premiere Pro Arabic Auto-Captions & RTL Text Engine** | `supported` | [Official Docs](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) (`2026-10-25`) | Auto-captioning ASR supports Arabic but requires manual proofreading for dialect terms, brand names (Tabby, Tamara, InstaPay, Salla), and compact price digits. | Always run the '100% Muted Playback Test' before approving any social video ad. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Average Video Watch Time, 6-Second Focused View Rate, and Sound-Off CTR across Snapchat, TikTok, and Meta Reels.
- **Baseline**: Uncaptioned (audio-only) vertical video control in the same ad set.
- **Observation Window**: 7–14 days.
- **Interpretation Boundary**: Burned-in captions capture silent scrollers, while visual hook quality in Second 1 (`AMP-333`) determines initial thumbstop.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) — *Esafqa* (Published `2026-10-09`, Accessed `2026-10-25`): Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks.
- [Top Arabic Content Writing Mistakes Hurting Your SEO Rankings](https://www.aiqalam.com/en/blog/top-arabic-content-writing-mistakes-hurting-your-seo-rankings) — *AI Qalam* (Published `2026-10-24`, Accessed `2026-10-25`): Documents poor RTL text alignment, unnatural AI phrasing, and morphological keyword stuffing in Arabic content.
