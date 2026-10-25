# FW-026: TikTok, Meta & Snapchat AIGC Disclosure & C2PA Metadata Compliance Checklist
## قائمة فحص الإفصاح الإلزامي عن المحتوى المولد بالذكاء الاصطناعي (`AIGC`) وبصمة `C2PA` على تيك توك وميتا وسناب شات

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-134`, `AMP-144`, `AMP-154`, `AMP-164`, `AMP-174`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Social Media Manager, Community Manager, Brand Strategist, Account Director
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Apply mandatory platform AI-generated content (AIGC) labels and preserve C2PA metadata on realistic AI visuals/voices so TikTok and Meta do not suppress reach or remove ads.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: تطبيق وسم الإفصاح الإلزامي عن الذكاء الاصطناعي (`AIGC`) والحفاظ على بيانات `C2PA` للمشاهد والأصوات الواقعية لمنع تقييد الوصول أو حذف الإعلانات على تيك توك وميتا.
- **Why `CHECKLIST` Fits This User Job (EN)**: TikTok and Meta automatically detect C2PA Content Credentials and audio-visual signatures on realistic synthetic videos (Sora, Veo, Kling, HeyGen, ElevenLabs); unlabeled realistic AIGC faces suppression or removal under TikTok's 2026 AIGC policy—making a pre-publish CHECKLIST essential.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: ترصد منصات تيك توك وميتا تلقائياً بيانات `C2PA` والبصمات البصرية والصوتية للفيديوهات المولدة (Sora, Veo, Kling, HeyGen, ElevenLabs)؛ ويؤدي إغفال الوسم الإلزامي للمشاهد الواقعية إلى تقييد الوصول أو حذف المحتوى، مما يجعل قائمة الفحص هذه ضرورية قبل النشر.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever publishing organic or paid social videos/images created or edited with generative AI tools (Veo, Sora, Kling, Runway, Midjourney, HeyGen, ElevenLabs, TikTok Symphony).
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند نشر فيديوهات أو صور (عضوية أو ممولة) تم توليدها أو تعديلها بأدوات الذكاء الاصطناعي التوليدي.
- **When NOT to Use It (EN)**: Do not use realistic AI-generated human avatars to fabricate fake customer product testimonials or medical/financial endorsements—these are banned outright even with an AIGC label (`AMP-289` / `AMP-392`).
- **متى لا تستخدم هذه الأداة (AR)**: لا تستخدم شخصيات افتراضية واقعية مولدة بالذكاء الاصطناعي لفبركة شهادات عملاء أو توصيات طبية/مالية؛ فهذا محظور تماماً حتى مع وضع وسم الذكاء الاصطناعي (`AMP-289` / `AMP-392`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. List of AI tools used in the asset pipeline (`Image`, `Video`, `Voiceover`, or `Caption/Translation only`)
2. Platform destination (`TikTok Organic/Ads`, `Instagram/Facebook Reels & Ads`, `YouTube Shorts`, `Snapchat`)
3. Visual realism classification (`Photorealistic Human/Scene/Event` vs. `Stylized 3D/Cartoon/Text Overlay Only`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

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

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **TikTok AIGC Policy, TikTok Symphony Auto-Labeling & C2PA Detection** | `supported` | [Official Reference](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) (`2026-10-25`) | TikTok's official AIGC documentation and AI Safety Essentials PDF confirm mandatory disclosure for realistic AI media, automatic labeling for TikTok Symphony outputs, and C2PA metadata reading. | Manually enable the `AI-generated content` toggle whenever uploading media created in external AI tools. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-134`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Mandatory AIGC metadata inspection and disclosure labeling in the social publishing checklist.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-144`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Mandatory AIGC metadata inspection and disclosure labeling in the social publishing checklist.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-154`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Mandatory AIGC metadata inspection and disclosure labeling in the social publishing checklist.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-164`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Mandatory AIGC metadata inspection and disclosure labeling in the social publishing checklist.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-174`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Mandatory AIGC metadata inspection and disclosure labeling in the social publishing checklist.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-514`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-144 (Social Media Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: Dubai E-Commerce Electronics Store publishing a 15-second vertical ad generated with `Veo 3.1` (photorealistic lifestyle scene in Dubai Marina) and an `ElevenLabs` Gulf Arabic voiceover on TikTok and Instagram Reels.
- **Human Review & Key Edits Applied**: 1. **Verified Non-Deceptive Claim**: Confirmed the Veo 3.1 lifestyle clip shows atmospheric product context while the actual physical gadget close-up uses real studio photography so buyers see the exact physical ports and screen (`AMP-065`).
2. **Checked C2PA Retention**: Exported directly from Premiere without running any metadata-stripping tool.
- **Final Usable Output**: - Video published across TikTok and Instagram Reels with native `AI-generated content` label enabled, passing automated moderation with zero reach penalties.
- **What Can Go Wrong**: A creator uploads a realistic `HeyGen` avatar speaking Saudi dialect on TikTok Shop without toggling `AI-generated content` ON; TikTok's C2PA/audio detector flags the video within 2 hours, removes the audio/video, and issues an account strike.
- **Correction & Fallback**: Always toggle `AI-generated content` ON at upload time for any realistic AI face, scene, or cloned voice; if using TikTok Symphony Studio, leave the automatic Symphony AIGC badge intact.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% pass rate on platform moderation (`0` AIGC removals or strikes) and stable video completion rate.
- **Baseline Definition**: Pre-checklist moderation flag count.
- **Observation Window**: Checked on every AI-assisted video upload. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Enabling the AIGC disclosure prevents policy penalties and takedowns, while hook pacing (`AMP-333`) determines viewer retention.
