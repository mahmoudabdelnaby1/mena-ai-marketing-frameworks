# Evidence Register & Source Boundaries — `FW-069` (`AMP-337`)

- **Framework Title (EN)**: ElevenLabs Arabic Voice Stability, `Style Exaggeration = 0` & Breath-Artifact Prevention Checklist
- **عنوان الأصل (AR)**: قائمة فحص إعدادات `ElevenLabs` للصوت العربي (تصفير `Style Exaggeration` ومنع تذبذب السرعة وأصوات التنفس الزائدة)
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements. | Voice synthesis requires clean mono reference audio and explicit phonetic/diacritic control. |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | ElevenLabs' official troubleshooting documentation states that setting Style Exaggeration to 0 and keeping Stability around 50–75% with shorter text segments resolves speed instability and breath artifacts. | Fallback: If a specific word still inflects oddly at `style: 0.0`, regenerate just that sentence using Request Stitching (`previous_request_ids`). |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements. | Voice synthesis requires clean mono reference audio and explicit phonetic/diacritic control. |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | ElevenLabs' official troubleshooting documentation states that setting Style Exaggeration to 0 and keeping Stability around 50–75% with shorter text segments resolves speed instability and breath artifacts. | Fallback: If a specific word still inflects oddly at `style: 0.0`, regenerate just that sentence using Request Stitching (`previous_request_ids`). |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never crank `Style Exaggeration` above `0.05` on Arabic scripts hoping to make the voice sound 'more excited'—it destabilizes Arabic consonant timing and injects gasping noises. / لا تقم برفع مؤشر `Style Exaggeration` فوق `0.05` في النصوص العربية بهدف زيادة الحماس؛ لأن ذلك يخل بتوقيت الحروف العربية ويولد شهيقاً مزعجاً بين الجمل.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
