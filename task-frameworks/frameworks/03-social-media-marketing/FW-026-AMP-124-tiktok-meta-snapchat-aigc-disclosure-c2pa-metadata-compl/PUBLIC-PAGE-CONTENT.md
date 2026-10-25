# TikTok, Meta & Snapchat AIGC Disclosure & C2PA Metadata Compliance Checklist
## <span dir="rtl">قائمة فحص الإفصاح الإلزامي عن المحتوى المولد بالذكاء الاصطناعي (`AIGC`) وبصمة `C2PA` على تيك توك وميتا وسناب شات</span>

> **Asset ID**: `FW-026` (`AMP-124`) | **Artifact Type**: `CHECKLIST` | **Channel**: Social Media Marketing | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Apply mandatory platform AI-generated content (AIGC) labels and preserve C2PA metadata on realistic AI visuals/voices so TikTok and Meta do not suppress reach or remove ads.
- **AR**: <span dir="rtl">تطبيق وسم الإفصاح الإلزامي عن الذكاء الاصطناعي (`AIGC`) والحفاظ على بيانات `C2PA` للمشاهد والأصوات الواقعية لمنع تقييد الوصول أو حذف الإعلانات على تيك توك وميتا.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use whenever publishing organic or paid social videos/images created or edited with generative AI tools (Veo, Sora, Kling, Runway, Midjourney, HeyGen, ElevenLabs, TikTok Symphony).
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم عند نشر فيديوهات أو صور (عضوية أو ممولة) تم توليدها أو تعديلها بأدوات الذكاء الاصطناعي التوليدي.</span>
- **When NOT to Use It (EN)**: Do not use realistic AI-generated human avatars to fabricate fake customer product testimonials or medical/financial endorsements—these are banned outright even with an AIGC label (`AMP-289` / `AMP-392`).
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تستخدم شخصيات افتراضية واقعية مولدة بالذكاء الاصطناعي لفبركة شهادات عملاء أو توصيات طبية/مالية؛ فهذا محظور تماماً حتى مع وضع وسم الذكاء الاصطناعي (`AMP-289` / `AMP-392`).</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- List of AI tools used in the asset pipeline (`Image`, `Video`, `Voiceover`, or `Caption/Translation only`)
- Platform destination (`TikTok Organic/Ads`, `Instagram/Facebook Reels & Ads`, `YouTube Shorts`, `Snapchat`)
- Visual realism classification (`Photorealistic Human/Scene/Event` vs. `Stylized 3D/Cartoon/Text Overlay Only`)

## 2. The Working `CHECKLIST` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

### Platform AIGC Labeling & C2PA Governance Checklist (Verified 2026-10-25)

#### 1. Decision Matrix: When Is the Platform `AI-Generated Content` Toggle Mandatory?
| Asset AI Usage Type | TikTok (`AI-Generated Content` Toggle) | Meta (`Made with AI` / Ad Disclosure) | YouTube (`Altered or Synthetic Content`) | Action Rule |
| :--- | :--- | :--- | :--- | :--- |
| **A. Realistic AI Human, Avatar, Clone Voice, or Photorealistic Scene** (`Veo 3.1`, `Sora 2`, `Kling 3.0`, `HeyGen`, `ElevenLabs` voice clone) | **`MANDATORY ON`** (Auto-labeled if made in `TikTok Symphony`; manual toggle required for external tools). | **`MANDATORY ON`** (C2PA auto-detected on images/videos; manual toggle in post/ad menu). | **`MANDATORY ON`** in YouTube Studio upload flow. | Turn ON the platform disclosure toggle BEFORE publishing; never strip C2PA metadata headers to evade detection! |
| **B. Obviously Stylized / Non-Realistic 3D Animation or Motion Graphics** | Optional (Recommended if human voices are synthetic). | Optional unless regulated category. | Not required for clearly unrealistic animation. | Keep visual style clearly artistic; disclose if synthetic voiceover mimics a real person. |
| **C. AI Used Only for Scriptwriting, Subtitles, Color Grading, or Background Noise Removal** | **NOT Required** (`OFF`). | **NOT Required** (`OFF`). | **NOT Required** (`OFF`). | Do not turn on AIGC labels for standard script assistance or captioning. |

#### 2. Pre-Publish Compliance Checklist
- [ ] **Check 1 — Enable the Native Platform Toggle**:
  - **TikTok**: On the post screen -> `More options (المزيد من الخيارات)` -> Toggle ON **`AI-generated content (محتوى مولد بالذكاء الاصطناعي)`**.
  - **Meta (IG/FB)**: On the upload screen -> `Add AI label / وسم الذكاء الاصطناعي` -> Toggle ON.
- [ ] **Check 2 — Do Not Strip C2PA Metadata with Re-Encoding Scripts**:
  - TikTok and Meta inspect both embedded `C2PA` manifests and invisible watermarking/pixel signatures. Attempting to strip metadata via FFmpeg while publishing realistic AI humans triggers policy violations.
- [ ] **Check 3 — Commercial + AI Dual Disclosure for Paid/Creator Posts**:
  - Note that the **AIGC Label** (`محتوى بالذكاء الاصطناعي`) does **NOT** replace the mandatory **Commercial Ad Label** (`#إعلان` / `Paid Partnership` — `AMP-287`). When running a sponsored AI post, enable BOTH disclosures.

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Campaign**: Dubai E-Commerce Electronics Store publishing a 15-second vertical ad generated with `Veo 3.1` (photorealistic lifestyle scene in Dubai Marina) and an `ElevenLabs` Gulf Arabic voiceover on TikTok and Instagram Reels.

### Step B: Initial Output (`المخرج الأولي`)
- **Audit Classification**: Category A (`Photorealistic Scene + Synthetic Voiceover`).
- **Required Toggles**:
  - TikTok `AI-generated content` toggle: `ON`
  - Meta `Made with AI` toggle: `ON`
  - Commercial disclosure (`#إعلان` / Paid Ad header): `ON`

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Verified Non-Deceptive Claim**: Confirmed the Veo 3.1 lifestyle clip shows atmospheric product context while the actual physical gadget close-up uses real studio photography so buyers see the exact physical ports and screen (`AMP-065`).
2. **Checked C2PA Retention**: Exported directly from Premiere without running any metadata-stripping tool.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Video published across TikTok and Instagram Reels with native `AI-generated content` label enabled, passing automated moderation with zero reach penalties.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: A creator uploads a realistic `HeyGen` avatar speaking Saudi dialect on TikTok Shop without toggling `AI-generated content` ON; TikTok's C2PA/audio detector flags the video within 2 hours, removes the audio/video, and issues an account strike.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Always toggle `AI-generated content` ON at upload time for any realistic AI face, scene, or cloned voice; if using TikTok Symphony Studio, leave the automatic Symphony AIGC badge intact.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **TikTok AIGC Policy, TikTok Symphony Auto-Labeling & C2PA Detection** | `supported` | [Official Docs](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) (`2026-10-25`) | TikTok's official AIGC documentation and AI Safety Essentials PDF confirm mandatory disclosure for realistic AI media, automatic labeling for TikTok Symphony outputs, and C2PA metadata reading. | Manually enable the `AI-generated content` toggle whenever uploading media created in external AI tools. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% pass rate on platform moderation (`0` AIGC removals or strikes) and stable video completion rate.
- **Baseline**: Pre-checklist moderation flag count.
- **Observation Window**: Checked on every AI-assisted video upload.
- **Interpretation Boundary**: Enabling the AIGC disclosure prevents policy penalties and takedowns, while hook pacing (`AMP-333`) determines viewer retention.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [TikTok Support: AI-generated content labels](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) — *TikTok* (Published `2026-07-01`, Accessed `2026-10-25`): Requires creators and advertisers to label realistic AIGC (synthetic faces, voices, scenes) and prohibits misleading unlabeled synthetic media.
- [AI Safety Essentials for Advertisers on TikTok](https://ads.tiktok.com/business/library/AI_Safety_Essentials_for_Advertisers_on_TikTok.pdf) — *TikTok for Business* (Published `2026-10-06`, Accessed `2026-10-25`): TikTok Symphony Creative Studio auto-labels qualifying AI assets; third-party AI video/voice ads must carry explicit AI disclosure.
- [AI-Generated Content Restrictions and Requirements](https://seller-us.tiktok.com/university/essay?knowledge_id=491489038501663&lang=en) — *TikTok Shop Academy* (Published `2026-09-02`, Accessed `2026-10-25`): Prohibits deceptive AI product demonstrations, fake before/after transformations, and unlabeled synthetic avatars in commerce videos.
