# Evidence Register & Source Boundaries — `FW-026` (`AMP-124`)

- **Framework Title (EN)**: TikTok, Meta & Snapchat AIGC Disclosure & C2PA Metadata Compliance Checklist
- **عنوان الأصل (AR)**: قائمة فحص الإفصاح الإلزامي عن المحتوى المولد بالذكاء الاصطناعي (`AIGC`) وبصمة `C2PA` على تيك توك وميتا وسناب شات
- **Channel**: Social Media Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-015` | [TikTok Support: AI-generated content labels](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) | TikTok | `2026-07-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Requires creators and advertisers to label realistic AIGC (synthetic faces, voices, scenes) and prohibits misleading unlabeled synthetic media. | Enforced via creator toggle and C2PA metadata detection. |
| `SRC-016` | [AI Safety Essentials for Advertisers on TikTok](https://ads.tiktok.com/business/library/AI_Safety_Essentials_for_Advertisers_on_TikTok.pdf) | TikTok for Business | `2026-10-06` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | TikTok Symphony Creative Studio auto-labels qualifying AI assets; third-party AI video/voice ads must carry explicit AI disclosure. | Applies to paid ads on TikTok. |
| `SRC-017` | [AI-Generated Content Restrictions and Requirements](https://seller-us.tiktok.com/university/essay?knowledge_id=491489038501663&lang=en) | TikTok Shop Academy | `2026-09-02` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Prohibits deceptive AI product demonstrations, fake before/after transformations, and unlabeled synthetic avatars in commerce videos. | TikTok Shop & e-commerce creative compliance. |
| `SRC-015` | [TikTok Support: AI-generated content labels](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) | TikTok | `2026-07-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | TikTok's official AIGC documentation and AI Safety Essentials PDF confirm mandatory disclosure for realistic AI media, automatic labeling for TikTok Symphony outputs, and C2PA metadata reading. | Fallback: Manually enable the `AI-generated content` toggle whenever uploading media created in external AI tools. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-015` | [TikTok Support: AI-generated content labels](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) | TikTok | `2026-07-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Requires creators and advertisers to label realistic AIGC (synthetic faces, voices, scenes) and prohibits misleading unlabeled synthetic media. | Enforced via creator toggle and C2PA metadata detection. |
| `SRC-016` | [AI Safety Essentials for Advertisers on TikTok](https://ads.tiktok.com/business/library/AI_Safety_Essentials_for_Advertisers_on_TikTok.pdf) | TikTok for Business | `2026-10-06` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | TikTok Symphony Creative Studio auto-labels qualifying AI assets; third-party AI video/voice ads must carry explicit AI disclosure. | Applies to paid ads on TikTok. |
| `SRC-017` | [AI-Generated Content Restrictions and Requirements](https://seller-us.tiktok.com/university/essay?knowledge_id=491489038501663&lang=en) | TikTok Shop Academy | `2026-09-02` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Prohibits deceptive AI product demonstrations, fake before/after transformations, and unlabeled synthetic avatars in commerce videos. | TikTok Shop & e-commerce creative compliance. |
| `SRC-015` | [TikTok Support: AI-generated content labels](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) | TikTok | `2026-07-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | TikTok's official AIGC documentation and AI Safety Essentials PDF confirm mandatory disclosure for realistic AI media, automatic labeling for TikTok Symphony outputs, and C2PA metadata reading. | Fallback: Manually enable the `AI-generated content` toggle whenever uploading media created in external AI tools. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Social Media Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not use realistic AI-generated human avatars to fabricate fake customer product testimonials or medical/financial endorsements—these are banned outright even with an AIGC label (`AMP-289` / `AMP-392`). / لا تستخدم شخصيات افتراضية واقعية مولدة بالذكاء الاصطناعي لفبركة شهادات عملاء أو توصيات طبية/مالية؛ فهذا محظور تماماً حتى مع وضع وسم الذكاء الاصطناعي (`AMP-289` / `AMP-392`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Social Media Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
