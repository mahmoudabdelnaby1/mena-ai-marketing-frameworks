# FW-091 — LLM Model Selection & Routing Decision Aid
## أداة قرار لاختيار نماذج اللغة وتوجيه المهام بينها

### Define the task
Record the required input/output modalities, language coverage, reasoning level, tool access, context size, latency, privacy constraints, and acceptable error modes.

### Compare candidates
1. Read the current official model catalog and availability for the intended provider, region, and account.
2. Build a representative evaluation set with permitted, non-sensitive or synthetic data.
3. Score output quality against task-specific criteria; separately record unsupported claims, formatting failures, and unsafe behavior.
4. Measure end-to-end latency and estimated cost using current published pricing and realistic request sizes.
5. Confirm data handling, retention, and contractual controls for the chosen deployment.
6. Define a fallback or human-review path for unavailable, uncertain, or low-confidence outputs.
7. Re-evaluate when provider model names, capabilities, limits, or pricing change.

### Output
A versioned decision record with task requirements, candidate models, evaluation results, cost/latency assumptions, privacy review, fallback, and reassessment date.

### Boundary
Model names, capabilities, availability, context windows, and pricing change. This decision aid does not recommend a permanently superior model or guarantee output quality.
