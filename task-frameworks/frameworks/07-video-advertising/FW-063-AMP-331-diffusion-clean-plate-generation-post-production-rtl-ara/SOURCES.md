# Evidence Register & Source Boundaries — `FW-063` (`AMP-331`)

- **Framework Title (EN)**: Diffusion Clean-Plate Generation & Post-Production RTL Arabic Typography Workflow (Extending `video-prompt-architect`)
- **عنوان الأصل (AR)**: مسار عمل توليد المشاهد النظيفة (`Clean-Plate`) وإضافة النصوص العربية المتجهية في المونتاج (امتداد لمهارة `video-prompt-architect`)
- **Channel**: Video Advertising
- **Last Reviewed Date**: `2026-10-25`
- **Verification Gate Status**: `READY_FOR_REVIEW`

## 1. Problem & Empirical Evidence (What Proves the Failure Mechanism in Egypt & GCC)

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Type & Confidence | What This Source Supports | Support Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-076` | [Improving Arabic Text Rendering in AI Image Generation](https://community.openai.com/t/improving-arabic-text-rendering-in-ai-image-generation/1376545) | OpenAI Developer Community | `2026-03-13` | `2026-10-25` | `COMMUNITY_DISCUSSION` (`REPEATED_SIGNAL`) | Documents persistent spelling errors, disconnected Arabic letters, and reversed LTR glyph rendering inside AI-generated images. | Applies to diffusion/autoregressive image generation without external vector text compositing. |
| `SRC-077` | [Arabic text rendering in Image Generation: characters appear disconnected](https://support.google.com/gemini/thread/406579327/urgent-arabic-text-rendering-in-image-generation-is-broken-characters-appear-disconnected-and-no?hl=en) | Google Gemini Support Community | `2026-02-01` | `2026-10-25` | `COMMUNITY_DISCUSSION` (`REPEATED_SIGNAL`) | Confirms that prompting image generation models directly for embedded Arabic copy produces disconnected, unshaped RTL characters. | Community bug report confirming cross-vendor raster Arabic text limitation. |

## 2. Official Platform Capability, Regulatory & Advice Evidence

| Source ID | Title & Direct Link | Publisher | Published | Accessed | Status / Confidence | Official Capability or Rule Verified | Fallback / Operational Boundary |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `SRC-020` | [Images and vision | OpenAI API](https://developers.openai.com/api/docs/guides/images-vision) | OpenAI | `2026-07-01` | `2026-10-25` | `OFFICIAL_DOCUMENTATION` (`CONFIRMED_CAPABILITY`) | Distinguishes multimodal vision input understanding from raster image generation endpoints. | Raster image models do not produce editable vector/RTL typography layers. |
| `SRC-020` | [Images and vision | OpenAI API](https://developers.openai.com/api/docs/guides/images-vision) | OpenAI | `2026-07-01` | `2026-10-25` | `OFFICIAL_CAPABILITY_CHECK` (`unsupported`) | OpenAI and Google Gemini developer/support documentation and community bug trackers confirm diffusion image/video models frequently disconnect or reverse right-to-left Arabic ligatures. | Fallback: Always generate text-free clean plates with negative space and overlay Arabic typography as vector text in post-production. |

## 3. Counterevidence, Exceptions & When This Pattern Does NOT Apply

- In strictly single-language English B2B niches or fully prepaid digital-product flows, the severity of this Video Advertising mismatch is lower provided manual QA is still performed.
- ** Operational Boundary**: Never ask DALL·E, Midjourney, Sora, Veo, or Kling to 'write the Arabic sentence `خصم 50% بمناسبة اليوم الوطني` on a neon sign or storefront board' inside the diffusion prompt. / لا تطلب أبداً من نماذج التوليد البصري كتابة جملة عربية داخل البرومبت (`Write the Arabic text "..." on the sign`).

## 4. Claims Remaining Uncertain & Update Triggers

- **Verification Requirement**: Verify live store/account configuration and current 2026/2027 platform UI settings for Video Advertising before deploying changes.
- **Verification Requirement**: Confirm current statutory penalty thresholds and licensing rules with qualified local counsel in KSA, UAE, or Egypt.
- **No Guaranteed Outcomes**: Per Agent 2 v1.2 boundaries, this asset defines operational controls and testable measurement hypotheses; it does not promise guaranteed rankings, virality, or fixed ROAS lift.
- **Update Triggers**: Re-verify this framework whenever platform UI/API schemas change, prior to major Hijri/seasonal peaks (Ramadan/White Friday), or within 90 days of `2026-10-25`.
