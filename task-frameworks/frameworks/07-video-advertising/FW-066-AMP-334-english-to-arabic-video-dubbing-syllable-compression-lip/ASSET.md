# FW-066: English-to-Arabic Video Dubbing Syllable Compression & Lip-Sync Alignment Workflow
## مسار عمل ضغط المقاطع الصوتية ومزامنة حركة الشفاه (`Lip-Sync`) عند دبلجة الإعلانات الإنجليزية إلى العربية (معالجة تمدد النص بنسبة 25%+)

- **Consolidated Contextual Child IDs (`MERGE_INTO_EXISTING`)**: `AMP-344`, `AMP-354`, `AMP-364`, `AMP-374`, `AMP-384`
- **Selected Artifact Type**: `OPERATING_FRAMEWORK`
- **Intended Audience**: Video Producer, Creative Strategist, Motion Designer, Performance Creative Lead
- **Target Markets & Languages**: Egypt & GCC (`Saudi Arabia, UAE, Kuwait, Qatar, Bahrain, Oman`) — Bilingual Arabic (`Egyptian Ammiya`, `Saudi/Gulf Khaleeji`, `White MSA`) + English
- **Version**: `1.2` | **Last Reviewed**: `2026-10-25` | **Status**: `READY_FOR_REVIEW`

## 1. Plain-Language Promise & Why This Artifact Form Fits the Job

- **What You Can Make or Decide (EN)**: Compress translated Arabic ad scripts by 25–30% in syllable count before running AI dubbing or lip-sync (`ElevenLabs Dubbing`, `HeyGen Video Translate`, `Sync Labs`) so the Arabic voiceover never speeds up into unnatural chipmunk cadence or overflows the video cut.
- **ما الذي يمكنك إنجازه أو حسمه بهذه الأداة (AR)**: ضغط عدد المقاطع الصوتية في النصوص العربية المترجمة بنسبة 25–30% قبل الدبلجة الآلية لمنع تسريع الصوت بشكل آلي مشوه أو تأخر الكلام عن حركة الشفاه ومشاهد الفيديو.
- **Why `OPERATING_FRAMEWORK` Fits This User Job (EN)**: Spoken Arabic translations of compact English ad copy (`'Shop now and save big'`) naturally take 20–35% more syllables and speaking duration (`'تسوّقوا الآن واحصلوا على توفير كبير'`); automated AI dubbing tools force-fit the longer Arabic audio into the original English timestamp window by speeding up the voice (`1.3x` robotic speed) or drifting out of lip-sync; a syllable-compression OPERATING_FRAMEWORK fixes the script before synthesis.
- **لماذا يناسب شكل `OPERATING_FRAMEWORK` هذه المهمة (AR)**: تستغرق الترجمة العربية المنطوقة جملاً ومقاطع صوتية أطول بنسبة 20–35% من الإنجليزية؛ فتقوم أدوات الدبلجة الآلية بضغط الصوت العربي عبر تسريعه بشكل آلي يفقد الوقار أو ينحرف عن حركة الشفاه؛ لذا يعالج هذا الإطار التشغيلي المشكلة بضغط المقاطع الصوتية قبل التوليد.

## 2. "Use It When" Trigger, Boundaries & Exact Inputs to Prepare

- **Use It When (EN)**: Use whenever localizing or dubbing global English TV/social video ads into Arabic (MSA, Saudi Khaleeji, or Egyptian Ammiya) using AI dubbing or human voiceover.
- **متى تستخدم هذه الأداة (AR)**: تُستخدم عند تعريب أو دبلجة إعلانات الفيديو الإنجليزية العالمية إلى العربية (سواء بأدوات الدبلجة بالذكاء الاصطناعي أو بالتعليق الصوتي البشري).
- **When NOT to Use It (EN)**: Never click '1-Click Auto-Translate & Dub' in HeyGen/ElevenLabs on a fast-paced English commercial without manually editing the intermediate Arabic transcript down to `<= 2.3` Arabic words per second first!
- **متى لا تستخدم هذه الأداة (AR)**: لا تعتمد خيار «الترجمة والدبلجة التلقائية بضغطة واحدة» للإعلانات الإنجليزية السريعة دون تقليص النص العربي الوسيط يدوياً إلى معدل `2.2 – 2.5 كلمة عربية في الثانية` أولاً.

### Exact Inputs to Prepare Before Starting (`المدخلات المطلوب تجهيزها`)
1. Source English Video with Timecoded Transcript (`[00:00.0 - 00:03.2]`, exact duration in seconds per phrase)
2. Target Arabic Register (`White MSA`, `Saudi Khaleeji`, or `Egyptian Ammiya`)
3. Phonetic Tashkeel rules (`AMP-332`)

### Privacy-Safe Data Handling (`ضوابط الخصوصية وحماية البيانات الشخصية PDPL`)
- **Strict PII Redaction Before Prompting**: Under Saudi PDPL (Art. 25), UAE Federal Decree-Law No. 45 of 2021, Qatar Law No. 13 of 2016, and Egypt Law No. 151 of 2020, **never paste raw customer names, unhashed mobile numbers (`+9665...` / `+201...`), email addresses, national IDs, or private WhatsApp transcripts into public/consumer LLM interfaces**. Use anonymized placeholders (`{first_name}`, `ORD_10045`) during prompt testing and restrict live customer data to zero-data-retention enterprise API endpoints or local deterministic scripts.

## 3. The Directly Usable Artifact (`الأداة التطبيقية الجاهزة للنسخ والتنفيذ`)

### 3-Step Timecode-Locked Arabic Dubbing Compression Workflow

#### Step 1: Calculate the Exact Arabic Word Ceiling per Timecode Slot
Natural commercial Arabic speech runs at **`2.2 to 2.5 words per second`** (compared to `3.2 to 3.8 words per second` in fast English ads!):
- **Formula**: `Max_Arabic_Words_In_Slot = floor(Slot_Duration_Seconds * 2.3)`
  - *Example*: A `3.0-second` English sentence containing `11` English words (`"Get instant relief from dry winter skin with our new formula"`) can hold **AT MOST `6 to 7` Arabic words** (`"ودّعي جفاف الشتاء فوراً بتركيبتنا الجديدة"` — `6` words), NEVER a 12-word literal translation (`"احصلي على راحة فورية من البشرة الجافة في فصل الشتاء مع تركيبتنا الجديدة"` — which overflows by 2.2 seconds!).

#### Step 2: Copy-Ready Dubbing Compression Prompt (With Labial Lip-Sync Matching)
```xml
<system_role>
You are an Arabic Dubbing & Lip-Sync Script Adapter for MENA Commercials.
CRITICAL TIMING RULE: Spoken Arabic takes 25–30% longer per word than English. For every timecode slot, your Arabic line MUST NOT EXCEED `floor(duration_seconds * 2.3)` words!
LIP-SYNC BONUS RULE: For on-camera speaking shots (`On-Camera Lip-Sync`), match bilabial closures (`ب / م / و` in Arabic corresponding to `B / M / P / W` in English) at the start and end of phrases so AI lip-sync looks effortless.
</system_role>

<timecoded_english_source>
{{PASTE_TIMECODED_ENGLISH_LINES_WITH_DURATION_AND_SHOT_TYPE}}
</timecoded_english_source>

<output_schema>
| Slot | Duration (s) | Shot Type (VO vs On-Camera) | English Source (Word Count) | Literal Translation (REJECTED - Too Long) | Compressed Dubbing Arabic (`<= 2.3 words/s` + Tashkeel `AMP-332`) | Arabic Word Count |
</output_schema>
```

## 4. Model & Platform Capability Branches (`فروع قدرات النماذج والمنصات والبدائل الاحتياطية`)

| System / Platform | Capability Status | Official Documentation & Access Date | Operational Constraint in Egypt & GCC | Fallback When Feature/Modality Is Unavailable |
| :--- | :--- | :--- | :--- | :--- |
| **ElevenLabs Dubbing Studio & HeyGen Video Translate Timecode Alignment** | `supported` | [Official Reference](https://elevenlabs.io/docs/eleven-creative/troubleshooting) (`2026-10-25`) | Both platforms allow manual editing of the translated target-language transcript per timecode segment before rendering final audio/lip-sync. | Always open the manual timeline editor and enforce `<= 2.3 Arabic words/second` before rendering the final dub. |

## 5. Consolidated Regional & Vertical Adaptation Matrix (`دمج الأنماط السياقية الفرعية بدون حشو`)

Per Agent 2 v1.2's anti-padding rule, the following **5 cross-verified contextual synthesis patterns** and **1 screened duplicate variants** share this core mechanism and are consolidated directly into this source-of-truth framework:

| Child Pattern ID | Disposition | Regional / Sector Operating Context | Specific Adaptation & Guardrail Integrated in This Asset | Evidence Tier |
| :--- | :--- | :--- | :--- | :--- |
| **`AMP-344`** | `MERGE_INTO_EXISTING` | Egyptian E-Commerce & Social Commerce (Shopify / WooCommerce / Cairo & Alexandria) | Pre-dubbing LLM syllable-condensation prompt targeting <=80% of English character length to fit native Arabic cadence.; Specifically impacts Egyptian brands operating in EGP where merchant-specific payment mix from recent order records, Mobile Wallets (Vodafone Cash), InstaPay, and Fawry dominate. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-354`** | `MERGE_INTO_EXISTING` | UAE & Multi-Market GCC Enterprise / Retail (Dubai, Abu Dhabi, Doha, Kuwait) | Pre-dubbing LLM syllable-condensation prompt targeting <=80% of English character length to fit native Arabic cadence.; Specifically impacts bilingual Arabic/English campaigns in high-CPM, expat-dense Gulf markets under UAE PDPL / TDRA and Qatari regulations. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-364`** | `MERGE_INTO_EXISTING` | High-Trust & Regulated Verticals (Healthcare/SFDA/EDA, Fintech/SAMA/FRA, Real Estate) | Pre-dubbing LLM syllable-condensation prompt targeting <=80% of English character length to fit native Arabic cadence.; Specifically impacts regulated claims requiring SFDA, EDA, MOH, SAMA, FRA, or RERA compliance pre-clearance and strict hallucination guardrails. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-374`** | `MERGE_INTO_EXISTING` | Seasonal Peak Operations (Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day) | Pre-dubbing LLM syllable-condensation prompt targeting <=80% of English character length to fit native Arabic cadence.; Specifically impacts high-velocity seasonal surges where CPMs jump 40-70%, prices change rapidly, and Hijri calendar cultural sensitivity is paramount. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-384`** | `MERGE_INTO_EXISTING` | Multi-Client Agency & MarTech API Automation Pipelines (LLM APIs, Webhooks, GA4, CAPI) | Pre-dubbing LLM syllable-condensation prompt targeting <=80% of English character length to fit native Arabic cadence.; Specifically impacts automated multi-SKU or multi-client LLM/API pipelines where schema validation, token cost, and attribution governance are required. | `TIER_2_CROSS_VERIFIED_SYNTHESIS` (`INFERENCE` from parent primary sources) |
| **`AMP-534`** | `REJECT_DUPLICATE` | Screened UI/Format Synonym (`Merged Variant: Minor UI/Format Synonym of AMP-364 (Video Advertising)`) | Consolidated into parent workflow without duplicate file inflation. | `SCREENED_DUPLICATE_VARIANT` |

### Context-Specific Execution Knobs Across the 5 MENA Operating Environments
1. **Saudi D2C E-Commerce (`Salla / Zid / Riyadh & Jeddah Retail`)**: Enforce `SAR` tax-inclusive pricing (`15% ZATCA VAT`), native `Mada / Apple Pay / Tabby / Tamara` visibility (`AMP-387`), `GAMR Mawthooq` creator verification (`AMP-281`), and White Saudi Khaleeji orthography (`AMP-002`, `AMP-177`).
2. **Egyptian E-Commerce & Social Commerce (`Shopify / WooCommerce / Cairo & Alexandria`)**: Use each merchant’s own order and payment data to assess Cash on Delivery (`COD`), mobile wallets, InstaPay, Fawry, `valU`, address fields, and pre-dispatch WhatsApp confirmation. Verify current provider terms and local requirements before implementation.
3. **UAE & Multi-Market GCC Enterprise / Retail (`Dubai, Abu Dhabi, Doha, Kuwait`)**: Separate high-CPM UAE/Qatar budgets from lower-CPM markets (`AMP-061`), enforce UAE `TDRA` `9 PM – 7 AM` SMS curfew + `AD-` prefix (`AMP-442`), UAE Media Council permits (`AMP-282`), and bilingual Arabic/English canonical & currency parity (`current applicable UAE VAT`, `current applicable Qatar/Kuwait tax rules`, 3-decimal `KWD` `AMP-239`).
4. **High-Trust & Regulated Verticals (`Healthcare SFDA/MOH/EDA, FinTech SAMA/FRA, Real Estate REGA/RERA`)**: Strip all therapeutic/cure verbs (`AMP-176`, `AMP-286`), display mandatory `MOH/SFDA/DHA/EDA/Fal/Trakheesi` permit numbers (`AMP-070`), and route budgets to high-credibility channels (`AMP-290`, `AMP-339`).
5. **Seasonal Peak Operations (`Ramadan, Eid, White/Yellow Friday, Saudi Founding/National Day`)**: Lock Hijri-Gregorian overlaps (`Feb 2027 Ramadan x Saudi Founding Day x Kuwait National Day` `AMP-125`), pre-schedule GMC `sale_price_effective_date` 48h ahead (`AMP-063`), verify 30-day baseline discount permits (`AMP-064`), and disable Meta Advantage+ auto-music (`AMP-065`).

## 6. Worked Example Summary & Failure Recovery (`ملخص المثال التطبيقي وخطة الإنقاذ`)

*(Full step-by-step worked example with annotated human edits is also provided in `EXAMPLE.md`)*

- **Sample Input Brief**: - **Source Video**: 10-second Global Skincare Commercial being dubbed into Arabic via `HeyGen / ElevenLabs Dubbing Studio`.
  - `Slot 1 (0.0s–2.5s | On-Camera)`: `"Tired of waking up with dull, dehydrated skin every single morning?"` (`11` English words in `2.5s`)
  - `Slot 2 (2.5s–6.0s | Product B-Roll VO)`: `"Our hyaluronic acid booster locks in moisture for seventy-two hours straight."` (`11` English words in `3.5s`)
  - `Slot 3 (6.0s–9.0s | On-Camera)`: `"Try it today and feel the glow."` (`7` English words in `3.0s`)
- **Human Review & Key Edits Applied**: 1. **Ingenious Syllable Swap (`72 Hours` -> `3 Days`)**: Replacing `"اثنتين وسبعين ساعة متواصلة"` (11 syllables) with `"ثلاث أيام كاملة"` (6 syllables) kept the exact factual meaning while matching the 3.5-second B-roll cut at `1.0x` natural voice speed!
2. **Checked Lip Closure on Slot 1 & 3**: Matched `"صَبَاحْ"` and `"بِنَفْسِكْ"` to the actress's labial closures.
- **Final Usable Output**: - 10-second Arabic dubbed commercial rendered at `1.00x` natural speaking speed with zero audio clipping and tight lip-sync alignment.
- **What Can Go Wrong**: An editor leaves the literal Arabic translation in ElevenLabs Dubbing with 'Auto-adjust speed to fit timecode' enabled; the voiceover plays at `1.38x` speed, sounding like a fast-forwarded legal disclaimer and ruining the luxury brand mood.
- **Correction & Fallback**: Lock playback speed in your dubbing tool to **`0.95x – 1.05x` maximum**; whenever a translated segment requires `>1.05x` speed to fit the timecode, **cut Arabic words/syllables in the script** rather than speeding up the audio.

## 7. Measurement Plan & Hypothesis Framing (`خطة القياس والضوابط الإحصائية`)

- **Primary Metric to Track**: Dubbed Audio Speed Ratio (`Target: 0.95x – 1.05x` across all segments), Zero clipped end-words, and Video Completion Rate.
- **Baseline Definition**: Prior auto-dubbed video completion rate and viewer negative comments on voice quality.
- **Observation Window**: Checked prior to exporting every dubbed video. *(Must span full 7/14-day weekly cycles and account for 25th–30th monthly salary windows per `AMP-391`)*.
- **What Cannot Be Concluded (Boundary)**: Syllable compression fixes audio naturalness and lip-sync, while culturally adapted visuals (`AMP-336`) determine local resonance.
