# Evidence Register & Source Boundaries — `FW-081` (`AMP-394`)

- **Framework Title (EN)**: WhatsApp Floating-Button Placement & Prepaid-Checkout Protection Decision Aid
- **عنوان الأصل (AR)**: أداة قرار ضبط ظهور زر «واتساب العائم» لمنع خطف متسوقي الدفع الإلكتروني الجاهزين للشراء (`Prepaid Checkout Hijack`)
- **Channel**: CRO - Conversion Rate Optimization
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-045` | [How GA4 Classifies AI Traffic for Arab Websites: What Saudi, UAE and Egyptian Sites Lose (2026 Study)](https://voctos.net/ga4-ai-traffic-arab-markets/) | VOCTOS | `2026-10-18` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | GA4's AI Assistant channel (launched 13 May 2026) misses 96.9% of AI search citations (which come from Google AI Overviews and AI Mode and land in Organic Search), sends ChatGPT links with rel='noreferrer' or WhatsApp shares to Direct, and sends Perplexity, Claude, HUMAIN Chat (KSA), Fanar (Qatar), and Gulf marketplaces (amazon.sa, noon.com) to Referral. | Based on GA4 channel rules, StatCounter Sep 2026 Arab market data, and Delta Medical Labs KSA case study. |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Self-serve prepaid checkouts convert at significantly higher net margin and lower RTO than manual chat orders for standard <1,000 SAR / <4,000 EGP retail items. | Fallback: Always hide floating chat launchers when the slide-out cart drawer or checkout step is active, revealing them only on error/idle timeout. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this CRO - Conversion Rate Optimization mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never display a floating `'Order on WhatsApp'` button on the `/checkout` page unless an actual payment failure or idle timeout (`>90 seconds` stalled on an error) has occurred! / لا تُظهر زر «اطلب عبر واتساب» العائم داخل صفحة إتمام الدفع (`/checkout`) إلا في حالة تعثر عملية الدفع فعلياً أو توقف المستخدم لأكثر من 90 ثانية!

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for CRO - Conversion Rate Optimization before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
