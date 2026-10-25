# Evidence Register & Source Boundaries — `FW-059` (`AMP-287`)

- **Framework Title (EN)**: MENA Creator Commercial Disclosure (`#إعلان` / `#Ad`) & Native Paid-Partnership Tagging Checklist
- **عنوان الأصل (AR)**: قائمة فحص الإفصاح الإعلاني الإلزامي للمؤثرين (`#إعلان` / `#Ad` ووسم الشراكة المدفوعة) في قصص وفيديوهات التواصل الاجتماعي
- **Channel**: Influencer Marketing
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-029` | [Licensing for Providing Advertising Content through Social Media Platforms (Mawthooq)](https://gmedia.gov.sa/en/services/licensing-for-providing-advertising-content-through-social-media-platforms-trusted) | Saudi General Authority of Media Regulation (GAMR) | `2026-09-14` | `2026-10-25` | `REGULATORY_POLICY` (`CONFIRMED_CAPABILITY`) | Mandates the Mawthooq license for individuals publishing advertising content on social media targeting Saudi Arabia. | Applies to paid, barter, and promotional influencer campaigns in KSA. |
| `SRC-046` | [Influencer and Advertiser Permits in Arab Markets: What Brands Must Check Before White Friday Creator Campaigns](https://voctos.net/influencer-advertiser-permits-arab-markets-white-friday/) | VOCTOS | `2026-10-18` | `2026-10-25` | `LEGAL_ANALYSIS` (`RESEARCH_FINDING`) | Saudi Arabia (GAMR Mawthooq) and UAE (Media Council permit) require creator licensing before publishing ads, whereas Egypt relies on general consumer protection/tax/media rules without an equivalent creator ad permit. | Cross-market creator compliance comparison. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-015` | [TikTok Support: AI-generated content labels](https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content) | TikTok | `2026-07-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Requires creators and advertisers to label realistic AIGC (synthetic faces, voices, scenes) and prohibits misleading unlabeled synthetic media. | Enforced via creator toggle and C2PA metadata detection. |
| `SRC-030` | [Laws and Executive Regulations - General Authority for Media Regulation](https://gmedia.gov.sa/en/executive-regulations) | Saudi General Authority of Media Regulation (GAMR) | `2026-09-14` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Both Saudi GAMR Executive Regulations and UAE Media Council guidelines require clear, unambiguous commercial disclosure (`#إعلان` / `مادة إعلانية`) on all advertising content. | Fallback: Always combine the native platform `Paid Partnership` toggle with a visible `#إعلان` text badge. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Influencer Marketing mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not accept ambiguous tags like `#تعاون` (`#Collab`), `#شكراً_[اسم_البراند]`, or `#دعم` as substitutes for explicit `#إعلان` or `#مادة_إعلانية`. / لا تقبل عبارات مبهمة مثل `#تعاون` أو `#هدية` أو `#دعم` كبديل عن الوسم النظامي الصريح `#إعلان` أو `#مادة_إعلانية`.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Influencer Marketing before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
