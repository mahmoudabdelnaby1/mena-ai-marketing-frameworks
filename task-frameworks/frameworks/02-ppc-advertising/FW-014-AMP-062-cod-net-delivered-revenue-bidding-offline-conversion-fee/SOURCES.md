# Evidence Register & Source Boundaries — `FW-014` (`AMP-062`)

- **Framework Title (EN)**: COD Net-Delivered Revenue Bidding & Offline Conversion Feedback Workflow (Egypt & KSA)
- **عنوان الأصل (AR)**: مسار عمل تدريب خوارزميات الإعلانات على «طلبات الدفع عند الاستلام المسلّمة فعلياً» بدلاً من الطلبات الوهمية (مصر والسعودية)
- **Channel**: Pay-Per-Click (PPC) Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-050` | [Digital Advertising Landscape in Egypt (2026)](https://23hublab.com/digital-advertising-landscape-in-egypt/) | 23HubLab | `2026-03-15` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | In Egypt, standard Meta Pixel captures only 60-75% of conversions (25-40% lost to in-app browsers, iOS ATT, and ad blockers), while platform-reported conversions overstate actual revenue by 20-40% due to COD cancellations and last-click inflation; provides 2026 EGP CPM/CPC/CPL benchmarks and notes Snapchat is niche in Egypt vs TikTok/Meta. | Egyptian digital advertising market 2026. |
| `SRC-052` | [E-commerce Growth in Egypt vs. Saudi Arabia vs. UAE](https://23hublab.com/e-commerce-growth-in-egypt-vs-saudi-arabia-vs-uae/) | 23HubLab | `2026-05-01` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Contrasts Egypt's high raw volume and high COD return risk with KSA/UAE higher AOV and digital payment adoption; highlights underexploited Egyptian Arabic SEO vs paid-only dependence. | MENA e-commerce structural comparison. |
| `SRC-083` | [Payment Gateway Egypt: Fees, Comparison & Best Providers (2026)](https://digitology.co/payment-gateway-egypt/) | Digitology Egypt | `2026-08-07` | `2026-10-25` | `MARKET_BENCHMARK` (`RESEARCH_FINDING`) | Secondary payment-provider article; not treated as representative national payment-share evidence. | Use current merchant order and session records to assess payment mix and checkout decisions. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-007` | [Conversions API - Meta for Developers](https://developers.facebook.com/documentation/ads-commerce/conversions-api) | Meta for Developers | `2026-09-28` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | Both Meta CAPI and Google Ads support dynamic `value` payloads at checkout and offline conversion adjustments up to 7 days (Meta) / 55–90 days (Google Ads). | Fallback: If server-side courier webhook integration is unavailable, apply the checkout JS payment-method multiplier in Google Tag Manager immediately. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Pay-Per-Click (PPC) Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not delay the primary browser/CAPI `Purchase` signal by 5–7 days waiting for physical courier delivery if that starves Meta's 7-day attribution window—use the Dual-Signal Expected-Value Multiplier below instead. / لا تقم بإلغاء حدث `Purchase` الفوري تماماً والانتظار 5–7 أيام حتى تسليم المندوب إذا كان ذلك سيكسر نافذة الإحالة (7 أيام)؛ استخدم نظام المعامل الموزون المزدوج أدناه.

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Pay-Per-Click (PPC) Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
