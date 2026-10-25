# FW-072: Arabic Creator Voice-Cloning Legal Consent & Acoustic Training Audio (`-23 to -18 dB RMS`) Operating Framework
## الإطار التشغيلي القانوني والصوتي لاستنساخ أصوات المؤثرين والمعلقين بالعربية (عقد حقوق الذكاء الاصطناعي ومعيار `-23 إلى -18 dB RMS`)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-350`, `AMP-360`, `AMP-370`, `AMP-380`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Secure explicit contractual AI voice-cloning rights (scope, duration, ad usage, revocation) and prepare acoustically normalized training audio (`-23dB to -18dB RMS`, true peak `<-3dB`) before cloning any Arabic creator or voice actor.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: توثيق الموافقة التعاقدية الصريحة لاستنساخ الصوت بالذكاء الاصطناعي وتجهيز الملفات الصوتية التدريبية وفق المعيار الهندسي (`-23 إلى -18 dB RMS` وذروة أقل من `-3dB`) قبل استنساخ صوت أي مؤثر أو معلق عربي.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Agencies and brands sometimes upload a creator's past Snapchat/Reels audio into ElevenLabs Instant Voice Cloning without explicit AI voice-cloning consent (a severe legal, biometric PDPL, and GAMR violation) and feed noisy, music-backed clips that violate ElevenLabs' acoustic training spec (`-23dB to -18dB RMS`, true peak `<-3dB`), resulting in metallic, unstable clones; a dual Legal + Acoustic OPERATING_FRAMEWORK governs both risks.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تقوم بعض الوكالات برفع مقاطع صوتية سابقة لمؤثر أو معلق في أدوات استنساخ الصوت دون عقد صريح يبيح الاستنساخ بالذكاء الاصطناعي (وهو خرق قانوني وبيومتري جسيم)، كما تستخدم تسجيلات مشوشة تخالف المعيار الهندسي لـ `ElevenLabs` (`-23 إلى -18 dB RMS`)؛ لذا يجمع هذا الإطار التشغيلي بين العقد النظامي والمعالجة الصوتية.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use before creating any custom voice clone (`Instant` or `Professional Voice Clone`) in ElevenLabs, HeyGen, or Azure/OpenAI Custom Voice for Arabic commercial use.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم قبل إنشاء أي نسخة صوتية مستنسخة (`Voice Clone`) لمؤثر أو معلق صوتي أو متحدث باسم العلامة التجارية باللغة العربية.
- **When NOT to Use It (EN)**: Never clone a creator's, employee's, or voice actor's voice from a standard one-off recording contract—standard recording rights do NOT grant generative AI voice-cloning rights!
- **متى لا تستخدم هذه الأداة (AR)**: لا تقم أبداً باستنساخ صوت مؤثر أو معلق صوتي أو موظف استناداً إلى «عقد تسجيل إعلان عادي»؛ فعقد التسجيل التقليدي لا يمنح حق استنساخ البصمة الصوتية بالذكاء الاصطناعي.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Signed AI Voice Synthesis & Biometric Consent Rider (specifying allowed scripts, duration, compensation, and deletion date)
2. Live Verification Recording (voice talent reading the platform's live verification captcha phrase)
3. Raw 30–180 minute dry studio `.wav` (`48kHz / 24-bit`) recording across Arabic phonetic pangrams

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### Dual Legal Consent & Acoustic Mastering Framework for Arabic Voice Cloning

#### Pillar 1: Mandatory Contractual AI Voice-Cloning Rider (Biometric & IP Compliance)
Before uploading a single second of audio to any AI voice platform, execute a written addendum covering these 6 points:
1. **Explicit Biometric & Synthetic Voice Consent**: Talent explicitly authorizes training a private generative AI voice model solely inside the brand's isolated enterprise account.
2. **Script Pre-Approval Right**: Every generated script must be pre-approved by the talent (or strictly restricted to approved product categories—zero political, medical, religious, or competitor endorsements).
3. **Territory, Term & Compensation**: Exact duration (e.g., `6 months` or `12 months` in KSA/UAE/Egypt) and per-campaign or monthly licensing royalty.
4. **Live Voice Captcha Verification**: The talent personally records the platform's live security verification challenge (`ElevenLabs Professional Voice Clone Verification`).
5. **Mandatory AIGC Disclosure (`AMP-124`, `AMP-289`)**: Ads using the cloned voice carry required platform synthetic-media disclosures.
6. **Model Deletion & Revocation Certificate**: Upon contract expiry, the voice clone ID is permanently deleted via API (`DELETE /v1/voices/{voice_id}`) with written confirmation sent to the talent.

#### Pillar 2: Acoustic Mastering Spec for Training Audio (Official ElevenLabs Standard — Verified 2026-10-25)
Per ElevenLabs' official voice-cloning documentation (`https://elevenlabs.io/docs/eleven-creative/troubleshooting`), raw training files MUST meet these exact acoustic targets before upload:
- **Loudness / RMS Level**: **`-23 dB to -18 dB RMS`**
- **True Peak Ceiling**: **`Strictly below -3.0 dBTP`** (Zero clipping!)
- **Signal-to-Noise Floor**: Noise floor `<= -60 dB`, **zero background music, zero room reverb/echo**, and uniform mic distance (`15–20 cm` with pop filter).
- **Copy-Ready FFmpeg Mastering Command (Normalize Raw `.wav` to Exact Training Spec)**:
```bash
# High-pass filter at 80Hz (removes rumble) + dynamic compression + normalize to -20 LUFS / -3.5 dB True Peak
ffmpeg -i raw_arabic_voice.wav   -af "highpass=f=80,acompressor=threshold=-20dB:ratio=3:attack=5:release=50,loudnorm=I=-20:TP=-3.5:LRA=7"   -ar 48000 -ac 1 -c:a pcm_s24le   mastered_training_arabic_48k.wav
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Professional Voice Cloning Acoustic Spec & Security Verification** | `supported` | [Official Reference](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | ElevenLabs documentation specifies training audio should be clean, noise-free, and leveled between -23dB and -18dB RMS with true peaks under -3dB, and enforces live speaker captcha verification for Professional Voice Clones. | If custom voice cloning rights are not secured, use pre-licensed stock Arabic voices from the verified commercial Voice Library. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **4 cross-verified contextual synthesis patterns** and **0 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-350`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Signed AI Voice Licensing Addendum + studio-grade mono WAV recording checklist.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-360`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Signed AI Voice Licensing Addendum + studio-grade mono WAV recording checklist.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-370`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Signed AI Voice Licensing Addendum + studio-grade mono WAV recording checklist.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-380`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Signed AI Voice Licensing Addendum + studio-grade mono WAV recording checklist.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Scenario**: Saudi E-Commerce Brand contracting a popular Saudi voiceover artist to create a licensed seasonal voice model for 50 personalized Ramadan city/product video variations.
- **Initial Defect**: Studio sent raw `.mp3` clips taken from old mixed commercials (containing background oud music, reverb, and peaks hitting `0.0 dB`), which produced a warbly, robotic voice clone.
- **Human Review & Key Edits Applied**: 1. **Talent Live Verification**: The voice artist completed ElevenLabs' live voice-captcha verification directly.
2. **Scheduled Deletion Reminder**: Created an automated calendar & webhook task on the contract end date to call `DELETE /v1/voices/{voice_id}` and email the deletion log to the artist.
- **Final Usable Output**: - Legally licensed, studio-mastered (`-20 dB RMS`, `<-3.5 dBTP`) Saudi Arabic voice clone deployed with zero acoustic distortion and full contractual governance.
- **What Can Go Wrong**: An employee uploads a creator's Instagram Reels audio (ripped from social media without permission) into an AI voice cloner to generate a new ad; the creator discovers their cloned voice running in a paid ad, triggering immediate legal action, GAMR/Media Council complaints, and public brand boycott.
- **Correction & Fallback**: Enforce a **Zero-Tolerance Policy on Unconsented Voice Cloning**: never upload any third-party voice to a TTS cloning endpoint without a signed AI Voice Licensing Addendum and live speaker verification.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: 100% of active custom voice IDs backed by a signed AI Voice Addendum + Acoustic Check (`-23 to -18 dB RMS`, `TP < -3dB`).
- **Baseline Definition**: Audit of all custom voices in the workspace.
- **Observation Window**: Audited prior to every voice clone creation and upon contract expiration. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: This framework structures operational and acoustic governance; have your local IP/data-privacy legal counsel approve the final talent contract.
