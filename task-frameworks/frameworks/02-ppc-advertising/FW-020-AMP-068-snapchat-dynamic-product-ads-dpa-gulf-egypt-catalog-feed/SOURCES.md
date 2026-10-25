# Evidence Register & Source Boundaries — `FW-020` (`AMP-068`)

- **Framework Title (EN)**: Snapchat Dynamic Product Ads (DPA) Gulf & Egypt Catalog Feed Validator Checklist
- **عنوان الأصل (AR)**: قائمة فحص وتدقيق كتالوجات إعلانات المنتجات الديناميكية في سناب شات (`Snapchat DPA`) لأسواق الخليج ومصر
- **Channel**: Pay-Per-Click (PPC) Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-042` | [Snapchat Product Ads in Arab Markets: Catalog Rules for Arabic Titles and White Friday](https://voctos.net/snapchat-product-ads-arab-markets/) | VOCTOS | `2026-10-08` | `2026-10-25` | `EMPIRICAL_AUDIT` (`RESEARCH_FINDING`) | Snap catalog feeds require explicit ISO currency codes ('199 SAR', '199 AED', '199 EGP'—never bare numbers), strict ID parity with Snap Pixel item IDs (<=128 chars), and front-loaded Arabic titles within the 40-character display guide. | Snapchat Dynamic Product Ads in KSA, UAE, and Egypt. |
| `SRC-059` | [Snapchat Ads Guide for Online Stores in Saudi Arabia and the Gulf](https://esafqa.com/en/blog/snapchat-ads-guide-saudi-gulf/) | Esafqa | `2026-10-09` | `2026-10-25` | `PRACTITIONER_GUIDE` (`REPEATED_SIGNAL`) | Details Snapchat's official creative rules for Gulf stores: 9:16 native shoot, hero message in second 1, brand before second 2 (no static logo opening), 5-6s duration with offer in seconds 2-3, natural Saudi/Gulf dialect + captions, and zero recycled TikTok/Reels watermarks. | Snapchat e-commerce ads in KSA and GCC. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-042` | [Snapchat Product Ads in Arab Markets: Catalog Rules for Arabic Titles and White Friday](https://voctos.net/snapchat-product-ads-arab-markets/) | VOCTOS | `2026-10-08` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`supported`) | VOCTOS Oct 2026 Snapchat product ads study confirms Snap requires explicit 3-letter ISO currency codes for non-USD prices and English enum strings (`in stock`, `new`) alongside Arabic titles. | Fallback: Run `format_snap_price()` on all price columns before feed upload. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Pay-Per-Click (PPC) Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Do not assume Salla's native Snapchat catalog link has identical `item_ids` to your custom GTM Snap Pixel without inspecting a live `PAGE_VIEW`/`ADD_CART` event (`AMP-544`). / لا تفترض تطابق معرفات `item_ids` بين ربط سلة التلقائي وبكسل سناب شات المخصص دون فحص حي لحدث `VIEW_CONTENT` و`ADD_CART` (`AMP-544`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Pay-Per-Click (PPC) Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
