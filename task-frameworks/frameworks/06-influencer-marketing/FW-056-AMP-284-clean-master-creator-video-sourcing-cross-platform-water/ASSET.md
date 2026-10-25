# FW-056: Clean Master Creator Video Sourcing & Cross-Platform Watermark Stripping Prevention Checklist
## قائمة فحص استلام النسخ الخام (`Clean Master`) لفيديوهات المؤثرين ومنع إعادة نشر العلامات المائية في إعلانات سناب شات وتيك توك

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-294`, `AMP-304`, `AMP-314`, `AMP-324`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Require clean, unwatermarked `1080x1920` raw master files in creator contracts so paid media teams never upload TikTok-watermarked or handle-stamped videos into Snapchat Commercials or Meta Reels Ads.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: إلزام المؤثرين بتسليم النسخة الأصلية النظيفة (`Clean Master 1080x1920`) بدون علامات مائية أو شعارات منصات أخرى لضمان عدم رفض الإعلانات أو تقييد وصولها في سناب شات وتيك توك وإنستغرام.
- **Why `CHECKLIST` Fits This User Job (EN)**: Snapchat's official ad policies and Esafqa's Gulf guide explicitly prohibit or penalize uploading videos bearing third-party platform watermarks (e.g., bouncing TikTok logo, CapCut end-card, or IG handle stickers), and AI watermark-blurring tools leave ugly smudged patches that fail ad review; a deliverable-intake CHECKLIST solves this at handoff.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تحظر سياسات إعلانات سناب شات وإنستغرام وتيك توك رفع فيديوهات تحمل شعارات أو علامات مائية لمنصات منافسة (مثل شعار تيك توك المتحرك أو خاتمة CapCut)، كما أن أدوات طمس العلامة المائية بالذكاء الاصطناعي تترك تشوهاً بصرياً يؤدي لرفض الإعلان؛ لذا تحسم قائمة الفحص هذه استلام الملف الخام النظيف من المصدر.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use when contracting UGC creators or influencers whose videos will be amplified as paid ads on Snapchat, TikTok, Instagram Reels, or YouTube Shorts.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند التعاقد مع صناع المحتوى (`UGC`) أو المؤثرين الذين سيتم ترويج فيديوهاتهم كإعلانات ممولة عبر سناب شات وتيك توك وإنستغرام ويوتيوب.
- **When NOT to Use It (EN)**: Never screen-record a creator's published Snapchat/TikTok story or use a 'TikTok video downloader' to grab the file for paid ads—always collect the original pre-upload `.mp4`/`.mov` master file.
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً بتسجيل الشاشة (`Screen Record`) لسنابة المؤثر أو تحميل الفيديو من تيك توك لاستخدامه في الإعلانات الممولة؛ اطلب دائماً الملف الأصلي قبل الرفع (`.mp4 / .mov`).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Creator Deliverable Handover Link (Google Drive / Frame.io / WeTransfer — NEVER WhatsApp standard video compression!)
2. FFprobe / Media Inspector check on the delivered `.mp4` / `.mov` file
3. Paid Amplification Whitelisting / Spark Ads / Snap Commercials spec

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Creator Video Master Deliverable Intake Checklist (`Zero Watermarks, Zero WhatsApp Compression`)

#### 1. Mandatory 2-File Delivery Clause (Insert into Every Creator Brief & PO)
Every contracted creator MUST upload **2 separate files** to a cloud drive folder (Google Drive / Dropbox / WeTransfer — **NEVER sent as standard compressed media inside WhatsApp chat**):
1. **File A — `Clean_Raw_Master_1080x1920.mp4`** (Required before releasing final payment):
   - Exported directly from iPhone camera / Premiere / CapCut Pro **BEFORE** uploading to TikTok, Snapchat, or Instagram.
   - **Zero platform watermarks** (No bouncing TikTok logo, no Snapchat username header/reply bar, no Instagram Reels watermark, no CapCut 2-second logo tail!).
   - **Zero burned-in platform stickers** (so the paid media team can add platform-native captions inside the safe zone per `AMP-335` & `AMP-338`).
   - Resolution: `1080x1920` (`9:16`), `30fps` or `60fps`, H.264/AAC, bitrate `>= 8 Mbps`.
2. **File B — `Captioned_Cut_1080x1920.mp4`**:
   - Version with clean Arabic captions inside the central `1080x1350` safe zone (`AMP-338`) and `#إعلان` badge (`AMP-287`).

#### 2. Pre-Ad-Upload QA Checklist
- [ ] **Check 1 — Visual Corner & Tail Inspection**: Play the first 2 seconds and the final 3 seconds of the video; confirm zero CapCut/InShot outro cards and zero corner platform watermarks.
- [ ] **Check 2 — Audio Copyright Clearance**: Confirm background audio contains **zero copyrighted commercial music tracks** pulled from TikTok/IG personal libraries (which cannot be legally boosted in paid Snapchat/Meta ads and trigger audio muting or copyright blocks!).

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **Snapchat Ad Policies, TikTok Spark Ads & Meta Reels Ad Quality Guidelines** | `supported` | [Official Reference](https://www.snap.com/ad-policies) (`2026-10-25`) | Snapchat Ad Policies and Meta/Instagram Reels guidelines prohibit or demote creatives containing third-party social platform watermarks or low-resolution re-uploads. | Always collect `Clean_Raw_Master_1080x1920.mp4` via cloud link before publishing. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-294`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Requiring clean, unwatermarked raw 9:16 footage deliverables in all creator contracts.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-304`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Requiring clean, unwatermarked raw 9:16 footage deliverables in all creator contracts.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-314`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Requiring clean, unwatermarked raw 9:16 footage deliverables in all creator contracts.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-324`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Requiring clean, unwatermarked raw 9:16 footage deliverables in all creator contracts.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Campaign**: UAE & KSA Modest Fashion Brand repurposing 8 creator TikTok videos into paid Snapchat Commercials and Instagram Reels Ads.
- **Problem**: Media buyer downloaded the 8 videos from TikTok (`with bouncing @handle TikTok watermark`) and uploaded them to Snapchat Ads Manager; Snapchat rejected `6 of 8` ads for `Third-party platform watermark / branding` and the remaining 2 had terrible CTR because the TikTok watermark covered the price overlay.
- **Human Review & Key Edits Applied**: 1. **Blocked WhatsApp Video Transfers**: Instructed account managers that creators sending videos via regular WhatsApp chat (`which downscales 1080p to 480p/720p low bitrate`) must resend as a **Google Drive link** or **WhatsApp Document (`مستند`)** to preserve full `1080x1920` resolution.
2. **Added Safe-Zone Native Overlays**: Placed Snapchat-native swipe-up price stickers on the clean master files.
- **Final Usable Output**: - `8 / 8` clean master `1080x1920` videos approved on Snapchat Ads Manager and Meta Reels Ads with zero watermark rejections and crisp HD quality.
- **What Can Go Wrong**: A media buyer uses an AI watermark-inpainting tool to blur out a TikTok logo in the top-left and bottom-right corners; Snapchat's ad review still flags the blurry pulsing smudge as a modified watermark and rejects the ad.
- **Correction & Fallback**: Never use AI blur/inpainting to hide platform watermarks on paid ads; tie final creator invoice settlement strictly to delivery of the pre-upload `Clean_Raw_Master_1080x1920.mp4` file.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% First-Pass Ad Approval Rate on Snapchat/Meta/TikTok (`0` watermark or resolution rejections) and Paid UGC Thumbstop / CTR.
- **Baseline Definition**: Prior watermark-related ad rejection count.
- **Observation Window**: Checked at asset handover for every creator campaign. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Clean master files prevent ad rejection and algorithm demotion, while hook pacing (`AMP-333`) drives ad ROAS.
