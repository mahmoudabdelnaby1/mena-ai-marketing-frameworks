# Arabic Creator Voice-Cloning Legal Consent & Acoustic Training Audio (`-23 to -18 dB RMS`) Operating Framework
## <span dir="rtl">الإطار التشغيلي القانوني والصوتي لاستنساخ أصوات المؤثرين والمعلقين بالعربية (عقد حقوق الذكاء الاصطناعي ومعيار `-23 إلى -18 dB RMS`)</span>

> **Asset ID**: `FW-072` (`AMP-340`) | **Artifact Type**: `OPERATING_FRAMEWORK` | **Channel**: Video Advertising | **Markets**: Egypt & GCC (`KSA, UAE, Kuwait, Qatar, Bahrain, Oman`) | **Version**: `1.2` (`Reviewed 2026-10-25`)

**What You Can Do With This (`ماذا يمكنك أن تنجز بهذه الأداة؟`)**:
- **EN**: Secure explicit contractual AI voice-cloning rights (scope, duration, ad usage, revocation) and prepare acoustically normalized training audio (`-23dB to -18dB RMS`, true peak `<-3dB`) before cloning any Arabic creator or voice actor.
- **AR**: <span dir="rtl">توثيق الموافقة التعاقدية الصريحة لاستنساخ الصوت بالذكاء الاصطناعي وتجهيز الملفات الصوتية التدريبية وفق المعيار الهندسي (`-23 إلى -18 dB RMS` وذروة أقل من `-3dB`) قبل استنساخ صوت أي مؤثر أو معلق عربي.</span>

## 1. Use It When & Required Inputs (`متى تستخدمها وما المدخلات المطلوبة؟`)

- **Use It When (EN)**: Use before creating any custom voice clone (`Instant` or `Professional Voice Clone`) in ElevenLabs, HeyGen, or Azure/OpenAI Custom Voice for Arabic commercial use.
- **متى تستخدمها (AR)**: <span dir="rtl">تُستخدم قبل إنشاء أي نسخة صوتية مستنسخة (`Voice Clone`) لمؤثر أو معلق صوتي أو متحدث باسم العلامة التجارية باللغة العربية.</span>
- **When NOT to Use It (EN)**: Never clone a creator's, employee's, or voice actor's voice from a standard one-off recording contract—standard recording rights do NOT grant generative AI voice-cloning rights!
- **متى لا تستخدمها (AR)**: <span dir="rtl">لا تقم أبداً باستنساخ صوت مؤثر أو معلق صوتي أو موظف استناداً إلى «عقد تسجيل إعلان عادي»؛ فعقد التسجيل التقليدي لا يمنح حق استنساخ البصمة الصوتية بالذكاء الاصطناعي.</span>

### Exact Inputs to Prepare (`المدخلات المطلوب تجهيزها قبل البدء`)
- Signed AI Voice Synthesis & Biometric Consent Rider (specifying allowed scripts, duration, compensation, and deletion date)
- Live Verification Recording (voice talent reading the platform's live verification captcha phrase)
- Raw 30–180 minute dry studio `.wav` (`48kHz / 24-bit`) recording across Arabic phonetic pangrams

## 2. The Working `OPERATING_FRAMEWORK` (`الأداة الكاملة الجاهزة للنسخ والتطبيق الفوري`)

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

## 3. Complete End-to-End Worked Example (`مثال تطبيقي متكامل من المدخلات حتى المراجعة البشرية والنتيجة النهائية`)

*(Illustrative scenario — original example for training, never represented as a verified client outcome)*

### Step A: Sample Brief / Input (`موجز المدخلات`)
- **Scenario**: Saudi E-Commerce Brand contracting a popular Saudi voiceover artist to create a licensed seasonal voice model for 50 personalized Ramadan city/product video variations.
- **Initial Defect**: Studio sent raw `.mp3` clips taken from old mixed commercials (containing background oud music, reverb, and peaks hitting `0.0 dB`), which produced a warbly, robotic voice clone.

### Step B: Initial Output (`المخرج الأولي`)
- **Executed Legal + Acoustic Pipeline**:
  1. Signed the 6-Point AI Voice Licensing Addendum (`90-day Ramadan/Eid term`, SAR royalty per batch, script pre-approval, and post-Eid deletion clause).
  2. Recorded 45 minutes of dry mono `48kHz/24-bit .wav` covering Saudi Khaleeji & White MSA phonetic pangrams (emphatic consonants `ص، ض، ط، ظ، ق، ع، غ، ح، خ`).
  3. Mastered via the FFmpeg pipeline to **`-20.1 dB RMS`** and **`-3.5 dBTP` true peak**.

### Step C: Human Review & Edits (`التدقيق البشري والتعديلات`)
1. **Talent Live Verification**: The voice artist completed ElevenLabs' live voice-captcha verification directly.
2. **Scheduled Deletion Reminder**: Created an automated calendar & webhook task on the contract end date to call `DELETE /v1/voices/{voice_id}` and email the deletion log to the artist.

### Step D: Final Reviewed Example Outcome (`النتيجة النهائية المعتمدة`)
- Legally licensed, studio-mastered (`-20 dB RMS`, `<-3.5 dBTP`) Saudi Arabic voice clone deployed with zero acoustic distortion and full contractual governance.

## 4. What Can Go Wrong & How to Fix It (`الأخطاء الشائعة وخطة الإنقاذ`)

- **Failure Case (`المشكلة المحتملة`)**: An employee uploads a creator's Instagram Reels audio (ripped from social media without permission) into an AI voice cloner to generate a new ad; the creator discovers their cloned voice running in a paid ad, triggering immediate legal action, GAMR/Media Council complaints, and public brand boycott.
- **Correction & Fallback (`الحل الإجرائي والبديل الآمن`)**: Enforce a **Zero-Tolerance Policy on Unconsented Voice Cloning**: never upload any third-party voice to a TTS cloning endpoint without a signed AI Voice Licensing Addendum and live speaker verification.

## 5. Model & Platform Capability Matrix (`مصفوفة قدرات النماذج والمنصات — 2026-10-25`)

| Platform / Model | Status | Official Documentation | MENA Operational Constraint | Fallback |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Professional Voice Cloning Acoustic Spec & Security Verification** | `supported` | [Official Docs](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | ElevenLabs documentation specifies training audio should be clean, noise-free, and leveled between -23dB and -18dB RMS with true peaks under -3dB, and enforces live speaker captcha verification for Professional Voice Clones. | If custom voice cloning rights are not secured, use pre-licensed stock Arabic voices from the verified commercial Voice Library. |

## 6. How to Measure Success (`خطة القياس والضوابط`)

- **Primary Metric**: 100% of active custom voice IDs backed by a signed AI Voice Addendum + Acoustic Check (`-23 to -18 dB RMS`, `TP < -3dB`).
- **Baseline**: Audit of all custom voices in the workspace.
- **Observation Window**: Audited prior to every voice clone creation and upon contract expiration.
- **Interpretation Boundary**: This framework structures operational and acoustic governance; have your local IP/data-privacy legal counsel approve the final talent contract.

## 7. Primary Sources & Evidence Boundaries (`المصادر الموثقة وحدود الأدلة`)

- [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) — *ElevenLabs* (Published `2026-06-01`, Accessed `2026-10-25`): Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements.
- [Licensing for Providing Advertising Content through Social Media Platforms (Mawthooq)](https://gmedia.gov.sa/en/services/licensing-for-providing-advertising-content-through-social-media-platforms-trusted) — *Saudi General Authority of Media Regulation (GAMR)* (Published `2026-09-14`, Accessed `2026-10-25`): Mandates the Mawthooq license for individuals publishing advertising content on social media targeting Saudi Arabia.
