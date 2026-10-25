# Evidence Register & Source Boundaries — `FW-066` (`AMP-334`)

- **Framework Title (EN)**: English-to-Arabic Video Dubbing Syllable Compression & Lip-Sync Alignment Workflow
- **عنوان الأصل (AR)**: مسار عمل ضغط المقاطع الصوتية ومزامنة حركة الشفاه (`Lip-Sync`) عند دبلجة الإعلانات الإنجليزية إلى العربية (معالجة تمدد النص بنسبة 25%+)
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-073` | [AI Translation Errors in Arabic, With Real Examples](https://locstars.com/ai-translation-errors-arabic/) | Locstars | `2026-10-22` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Documents concrete English-to-Egyptian and Gulf Arabic LLM translation failures including register mixing, gender agreement errors, and literal idioms. | Arabic localization QA. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Documents audio cloning inconsistencies, style exaggeration artifacts, mispronunciation triggers, and dynamic range compression requirements. | Voice synthesis requires clean mono reference audio and explicit phonetic/diacritic control. |
| `SRC-025` | [Troubleshooting | ElevenLabs Documentation](https://elevenlabs.io/docs/eleven-creative/troubleshooting) | ElevenLabs | `2026-06-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Both platforms allow manual editing of the translated target-language transcript per timecode segment before rendering final audio/lip-sync. | Fallback: Always open the manual timeline editor and enforce `<= 2.3 Arabic words/second` before rendering the final dub. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never click '1-Click Auto-Translate & Dub' in HeyGen/ElevenLabs on a fast-paced English commercial without manually editing the intermediate Arabic transcript down to `<= 2.3` Arabic words per second first! / لا تعتمد خيار «الترجمة والدبلجة التلقائية بضغطة واحدة» للإعلانات الإنجليزية السريعة دون تقليص النص العربي الوسيط يدوياً إلى معدل `2.2 – 2.5 كلمة عربية في الثانية` أولاً.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
