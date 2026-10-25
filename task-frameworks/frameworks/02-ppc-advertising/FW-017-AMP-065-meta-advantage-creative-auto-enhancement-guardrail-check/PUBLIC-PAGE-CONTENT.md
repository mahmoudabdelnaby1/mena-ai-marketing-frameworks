# Meta Advantage+ Creative Auto-Enhancement Guardrail Checklist for Arab & Ramadan Campaigns
## <span dir="rtl">قائمة فحص وضبط التحسينات التلقائية (`Meta Advantage+ Creative`) لحماية الهوية البصرية والنصوص العربية وحملات رمضان</span>

> **Asset ID**: `FW-017` (`AMP-065`) | **Artifact Type**: `CHECKLIST` | **Channel**: Pay-Per-Click (PPC) Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Disable destructive Meta Advantage+ Creative auto-enhancements that inject unapproved music during Ramadan, warp Arabic typography, or shift luxury brand colors.
- **AR**: <span dir="rtl">تعطيل التحسينات التلقائية الضارة في `Meta Advantage+ Creative` التي تضيف موسيقى غير ملائمة في حملات رمضان أو تشوه الخطوط العربية أو تغير ألوان العلامة التجارية.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use at the Ad level in Meta Ads Manager before publishing any image, video, or catalog ad in KSA, UAE, Egypt, or wider MENA.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم على مستوى الإعلان (`Ad Level`) في مدير إعلانات Meta قبل نشر أي إعلان مصور أو فيديو أو كتالوج في أسواق المنطقة.</span>
- **When NOT to Use It (EN)**: Do not leave 'All optimizations ON' when advertising culturally sensitive categories (Ramadan/Hajj, Islamic finance, luxury fashion, SFDA-regulated healthcare/cosmetics).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تترك خيار «تفعيل كافة التحسينات» مفعلاً في حملات المواسم الدينية (رمضان/الحج) أو التمويل الإسلامي أو المنتجات الفاخرة أو القطاع الصحي الخاضع لهيئة الغذاء والدواء.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Meta Ads Manager Ad-Level Creative Setup screen
- Brand Audio & Cultural Policy (e.g., voiceover/nasheed/percussion-only rule for KSA/Ramadan campaigns)
- Native 9:16 (`1080x1920`) and 1:1 (`1080x1080`) Arabic creative assets

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Meta Advantage+ Creative Toggle Governance Matrix (Ad Level)

| Advantage+ Creative Toggle in Meta Ads Manager | Default Meta State | Mandatory MENA Action (`TURN OFF` vs `SAFE`) | Why (MENA & Arabic Failure Mechanism) |
| :--- | :--- | :--- | :--- |
| **1. Add Music (`إضافة موسيقى`)** | Often `ON` | **`TURN OFF (حرج جداً)`** | Automatically overlays Western pop/electronic tracks onto silent or voice-only Arabic graphics—provoking severe audience backlash in Saudi Arabia, Ramadan/Eid campaigns, and Islamic finance/charity ads. |
| **2. Image Expansion / Outpainting (`توسيع الصورة`)** | `ON` | **`TURN OFF` (Supply native 9:16 & 1:1 instead)** | AI outpainting hallucinates distorted borders, extra fingers, or garbled pseudo-Arabic calligraphy around product packaging. |
| **3. Visual Touch-ups / Brightness & Contrast (`اللمسات المرئية وتعديل الألوان`)** | `ON` | **`TURN OFF` for Fashion, Cosmetics, Jewelry & Real Estate** | Alters true fabric/skin/gold shades, causing high COD return rates (`"اللون في الحقيقة غير الإعلان"`). |
| **4. Text Improvements / Headline Swaps (`تحسينات النص وتبديل العناوين`)** | `ON` | **`TURN OFF` for Regulated Copy (`SFDA/EDA/PDPL/Discounts`)** | Moves disclaimers or pulls random comment/caption fragments into the headline slot, breaking Arabic grammar or detaching statutory permit numbers (`AMP-064`). |
| **5. Add Overlays / Info Labels (`إضافة طبقات نصية / شارات`)** | `ON` | **`TURN OFF` if image already contains Arabic price/offer badges** | Renders awkward LTR overlays on top of existing Arabic typography or covers `Tabby/Tamara` badges. |
| **6. Relevant Comments (`التعليقات ذات الصلة`)** | `ON` | **Review / `TURN OFF` if unmoderated dialectal sarcasm exists** | Can pin a sarcastic Egyptian or Gulf comment below the ad. |

#### Pre-Publish Verification Steps
- [ ] Click **`Edit` (`تعديل`)** inside the `Advantage+ creative` panel on every ad (and inside Catalog Dynamic Templates).
- [ ] Click **`Preview all enhancements`** and inspect both Instagram Reels (`9:16`) and Facebook Feed (`1:1`/`4:5`) previews with audio unmuted.
- [ ] When cloning ad sets or importing via bulk sheet, re-verify toggles (Meta frequently resets enhancements to `ON` on new placements).

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Campaign**: Saudi Ramadan Oud & Gift Box Campaign on Instagram Reels & Facebook Feed (`SAR 150,000` budget).
- **Incident Prevented**: Media buyer uploaded a serene 1:1 static graphic with Arabic calligraphy (`"رمضان يجمعنا على الطيب"`). Meta Advantage+ Creative defaulted `Add Music` (`ON`) with an upbeat Western dance track and `Image Expansion` (`ON`) which stretched the top of the Oud bottle into a crooked shape.

### Step B: Initial Output (`المخرج الأولي`)
- Ad-Level Audit prior to launch:
  - `Add Music`: `ON` (`FAIL` — Western dance beat attached to Ramadan Oud graphic)
  - `Expand Image`: `ON` (`FAIL` — distorted bottle cap in 9:16 preview)
  - `Visual Touch-ups`: `ON` (`FAIL` — oversaturated dark mahogany wood box into bright orange)

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Disabled All 3 Destructive Toggles**: Turned OFF `Add Music`, `Expand Image`, and `Visual Touch-ups`.
2. **Uploaded Native Placement Assets**: Supplied a dedicated `1080x1920` (9:16) graphic and a `1080x1080` (1:1) graphic created by the design team so no AI outpainting was needed.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Campaign launched across KSA with 100% brand-faithful colors, native 9:16/1:1 geometry, and zero unapproved audio tracks.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An agency turns off Advantage+ Creative toggles on Ad #1, then uses 'Duplicate Ad' and changes the media file—Meta Ads Manager silently re-enables `Expand Image` and `Visual Touch-ups` when new media is selected.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always make the Advantage+ Creative toggle check the **very last step after uploading final media**, immediately before clicking the green `Publish` button.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **Meta Ads Manager Advantage+ Creative Enhancements** | `supported` | [Official Docs](https://www.hyperfx.ai/blog/meta-advantage-creative-enhancements-issues) (`2026-10-25`) | Meta enables multiple generative creative enhancements by default; individual toggles must be manually disabled at the Ad level. | Always supply native 1:1, 4:5, and 9:16 placement ratios so `Expand Image` is never required. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: Zero negative brand/audio sentiment comments on ads and reduced post-delivery 'item looks different from photo' COD return rate.
- **Baseline**: Comment sentiment and return reason log from prior campaigns.
- **Observation Window**: Checked at launch + day 3 of every campaign.
- **Interpretation Boundary**: Disabling destructive auto-enhancements protects brand trust and compliance, while creative hook quality drives CTR.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Meta Advantage+ Creative Enhancements Issues: How to Disable](https://www.hyperfx.ai/blog/meta-advantage-creative-enhancements-issues) — *HyperFX* (Published `2026-04-07`, Accessed `2026-10-25`): Meta Advantage+ Creative Enhancements turn on by default and alter color tones, crop boundaries, music, and text overlays without advertiser approval.
- [Meta's AI Is Rewriting Your Ads Without Permission](https://mintec.co/blog/meta-advantage-plus-ad-creative-auto-enhancements/) — *Mintec* (Published `2026-07-21`, Accessed `2026-10-25`): Auto-enabled Advantage+ music, background expansion, and AI copy variations can violate strict brand guidelines and cultural norms.
- [Meta Advantage+ Mistakes: Common Errors and How Agencies Avoid Them](https://alienroad.com/meta-advantage-mistakes-common-errors-and-how-agencies-avoid-them/) — *Alien Road* (Published `2026-03-19`, Accessed `2026-10-25`): Identifies 7 Advantage+ failures: weak conversion signals, low creative variety, premature edits during learning, paying for existing customers, trusting in-platform numbers without holdouts, ignoring brand safety, and unhealthy product feeds.
