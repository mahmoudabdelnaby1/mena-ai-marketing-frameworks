# FW-061: Synthetic AI Virtual Influencer & Avatar Commercial Governance Checklist
## قائمة فحص حوكمة «المؤثرين الافتراضيين» والأفاتار المولد بالذكاء الاصطناعي (`Virtual Influencers` والإفصاح المزدوج)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-299`, `AMP-309`, `AMP-319`, `AMP-329`
- **Selected Artifact Type**: `CHECKLIST`
- **Intended Audience**: Influencer Marketing Manager, PR & Communications Lead, Talent Coordinator, Legal & Compliance Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Deploy synthetic AI brand mascots or virtual presenters safely by enforcing dual disclosure (`#إعلان` + `AIGC`), banning fabricated first-person physical product reviews, and respecting regional licensing rules.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: ضبط استخدام الشخصيات الافتراضية والأفاتار المولد بالذكاء الاصطناعي عبر الإفصاح المزدوج (`#إعلان` + `محتوى بالذكاء الاصطناعي`) ومنع فبركة تجارب الاستخدام الجسدية الكاذبة.
- **Why `CHECKLIST` Fits This User Job (EN)**: Brands experimenting with AI virtual influencers (`HeyGen`, `Midjourney + Kling/Veo`, `Synthesia`) frequently script the synthetic avatar to say `'أنا جربت هالعطر/الكريم على بشرتي لمدة أسبوعين والنتيجة خيال!'` without disclosing that the speaker is an AI program—violating TikTok's 2026 AIGC policy against deceptive synthetic endorsements as well as Saudi/UAE/Egyptian consumer protection laws; a governance CHECKLIST sets clear boundaries.
- **لماذا يناسب شكل `CHECKLIST` هذه المهمة (AR)**: تقع بعض العلامات التجارية في خطأ برمجة شخصية افتراضية مولدة بالذكاء الاصطناعي لتقول للمتابعين «أنا جربت هذا الكريم على بشرتي لمدة أسبوعين والنتيجة مذهلة!» دون الإفصاح عن كونها شخصية اصطناعية؛ وهو ما يخالف سياسات تيك توك وميتا لعام 2026 وقوانين حماية المستهلك ضد التضليل التجاري؛ وتحدد قائمة الفحص هذه الضوابط الإلزامية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever using an AI-generated avatar, virtual character, or synthetic presenter in social content or paid ads in MENA.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند الاستعانة بشخصية افتراضية (`Virtual Influencer`) أو مذيع ذكاء اصطناعي (`AI Avatar`) في المحتوى التسويقي أو الإعلانات.
- **When NOT to Use It (EN)**: Never script a synthetic AI human to claim personal physical consumption, medical recovery, or sensory skin/taste experience (`'جربته على بشرتي / ذقته بنفسي'`).
- **متى لا تستخدم هذه الأداة (AR)**: يُحظر تماماً كتابة نص لشخصية ذكاء اصطناعي تدعي فيه تجربة حسية أو جسدية شخصية للمنتج («جربته على بشرتي»، «شربته وحسيت بالفرق»).

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Synthetic Avatar Script & Visual Assets (`HeyGen`, `Veo 3.1`, `Sora 2`, `Kling 3.0`)
2. Account Bio & Video Disclosure Badges (`شخصية افتراضية بالذكاء الاصطناعي` + `#إعلان`)
3. Voice / Likeness Rights Documentation (`AMP-340`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Synthetic AI Influencer & Avatar Compliance Checklist (MENA)

#### 1. The 5 Non-Negotiable Virtual Influencer Rules
- [ ] **Check 1 — Explicit Bio & On-Screen Identity Disclosure**:
  - If running a dedicated virtual character account, the account bio MUST state clearly in Arabic & English: **`"شخصية افتراضية مولدة بالذكاء الاصطناعي تابعة لـ [اسم العلامة] | AI-Generated Virtual Persona"`**.
  - Every video MUST have the platform's native **`AI-Generated Content (AIGC)`** toggle turned ON (`AMP-124`) AND a visible **`#إعلان`** badge if commercial (`AMP-287`).
- [ ] **Check 2 — Zero Fake Personal Sensory / Physical Experience Claims (`CRITICAL`)**:
  - **PROHIBITED (`DECEPTIVE ENDORSEMENT`)**: `"أنا استخدمت هذا السيروم على وجهي لمدة شهر واختفت التصبغات!"` (An AI program does not have skin, stomach, or taste buds—claiming first-person physical experience is deceptive advertising under KSA/UAE/Egypt consumer laws and TikTok Shop policy!).
  - **ALLOWED (`EXPLAINER / BRAND CONCIERGE FRAMING`)**: `"أهلاً بكم! أنا «نورة»، المساعدة الافتراضية لعلامة [X]. اليوم بنستعرض تركيبة سيروم فيتامين سي الجديد بتركيز 15% وكيف تستخدمينه في روتينك اليومي..."`
- [ ] **Check 3 — Zero Unconsented Real-Person Likeness or Voice Cloning (`AMP-340`)**:
  - Never train or prompt an avatar/voice model to mimic a real Saudi, Emirati, or Egyptian celebrity, public figure, or creator without a signed, specific AI likeness/voice licensing agreement.
- [ ] **Check 4 — Real Footage for Physical Product Proof**:
  - Whenever showing product texture, fabric drape, food, or cosmetic application, cut to **100% real, unretouched studio/creator camera footage** (`لقطة حقيقية للمنتج الفعلي`) rather than an AI-hallucinated product render.

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **TikTok 2026 AIGC Policy & Saudi/UAE/Egypt Consumer Protection Laws on Deceptive Endorsements** | `supported` | [Official Reference](https://ads.tiktok.com/business/library/AI_Safety_Essentials_for_Advertisers_on_TikTok.pdf) (`2026-10-25`) | TikTok's AI Safety Essentials for Advertisers and AIGC policy require disclosure on realistic synthetic humans and prohibit deceptive synthetic product endorsements. | Frame virtual avatars explicitly as 'Your AI Brand Guide (مساعدك الافتراضي بالذكاء الاصطناعي)' rather than a real human customer. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-299`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Explicit AI disclosure labeling and avoiding fake first-person testimonial claims by synthetic avatars.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-309`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Explicit AI disclosure labeling and avoiding fake first-person testimonial claims by synthetic avatars.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-319`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Explicit AI disclosure labeling and avoiding fake first-person testimonial claims by synthetic avatars.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-329`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Explicit AI disclosure labeling and avoiding fake first-person testimonial claims by synthetic avatars.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-529`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-309 (Influencer Marketing)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Brand**: Dubai & Riyadh Skincare D2C Store creating a TikTok & Instagram Reels ad using a photorealistic `HeyGen` + `ElevenLabs` Gulf female avatar.
- **Draft Script (`VIOLATION`)**: `"بنات، أنا سارة! جربت هالكريم الكوري على بشرتي الجافة أسبوع كامل قبل العيد، والله بشرتي صارت قزاز!"` (With no AI disclosure and a fake personal trial claim).
- **Human Review & Key Edits Applied**: 1. **Added Real Hand Swatch Cutaway**: Inserted a 4-second real iPhone macro clip showing the actual cream texture on real skin at `0:04–0:08` so buyers see true physical consistency.
2. **Checked Cultural Dress Guardrails (`AMP-336`)**: Verified the avatar's modest Gulf styling and natural lip-sync timing (`AMP-334`).
- **Final Usable Output**: - Compliant AI Virtual Concierge ad approved on TikTok and Meta with full `AIGC` + `#إعلان` disclosure and real product macro footage.
- **What Can Go Wrong**: A TikTok Shop seller generates 20 fake 'customer UGC review videos' using 20 different AI avatars claiming they bought and loved the product; TikTok Shop detects the synthetic C2PA/audio signatures and permanently bans the storefront for deceptive synthetic endorsements.
- **Correction & Fallback**: Use AI avatars **only as transparent brand explainers/virtual concierges**; for customer testimonials and UGC reviews, always use **real human creators (`AMP-283`)**.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% Ad & Post Approval Rate (`0` AIGC deception flags) and Viewer Retention / CTR vs. real human creator baseline.
- **Baseline Definition**: Real creator UGC control ad in the same ad set.
- **Observation Window**: 14 days A/B test. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Transparent virtual concierges work well for educational/FAQ explainers, whereas high-trust physical categories (skincare, food, fashion) typically convert higher with real human creators.
