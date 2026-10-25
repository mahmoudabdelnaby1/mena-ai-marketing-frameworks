# Evidence Register & Source Boundaries — `FW-072` (`AMP-340`)

- **Framework Title (EN)**: Arabic Creator Voice-Cloning Legal Consent & Acoustic Training Audio (`-23 to -18 dB RMS`) Operating Framework
- **عنوان الأصل (AR)**: الإطار التشغيلي القانوني والصوتي لاستنساخ أصوات المؤثرين والمعلقين بالعربية (عقد حقوق الذكاء الاصطناعي ومعيار `-23 إلى -18 dB RMS`)
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-029` | [Licensing for Providing Advertising Content through Social Media Platforms (Mawthooq)](https://gmedia.gov.sa/en/services/licensing-for-providing-advertising-content-through-social-media-platforms-trusted) | Saudi General Authority of Media Regulation (GAMR) | `2026-09-14` | `2026-10-25` | `REGULATORY_POLICY` (`CONFIRMED_CAPABILITY`) | Mandates the Mawthooq license for individuals publishing advertising content on social media targeting Saudi Arabia. | Applies to paid, barter, and promotional influencer campaigns in KSA. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements. | Voice synthesis requires clean mono reference audio and explicit phonetic/diacritic control. |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | ElevenLabs documentation specifies training audio should be clean, noise-free, and leveled between -23dB and -18dB RMS with true peaks under -3dB, and enforces live speaker captcha verification for Professional Voice Clones. | Fallback: If custom voice cloning rights are not secured, use pre-licensed stock Arabic voices from the verified commercial Voice Library. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never clone a creator's, employee's, or voice actor's voice from a standard one-off recording contract—standard recording rights do NOT grant generative AI voice-cloning rights! / لا تقم أبداً باستنساخ صوت مؤثر أو معلق صوتي أو موظف استناداً إلى «عقد تسجيل إعلان عادي»؛ فعقد التسجيل التقليدي لا يمنح حق استنساخ البصمة الصوتية بالذكاء الاصطناعي.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
