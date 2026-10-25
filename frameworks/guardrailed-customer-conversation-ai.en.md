# Guardrailed customer conversation AI

Design customer-facing assistants around approved knowledge, limited actions, safe failure, privacy, and a visible route to a human.

## When to use

Use for website chat, messaging channels, support assistants, lead qualification, and post-purchase conversations that use a language model or automated workflow.

## Inputs

- Approved source of truth for product, price, availability, delivery, returns, and service limits
- Permitted actions, authentication requirements, and data the assistant must not collect
- Escalation owner, hours, service-level expectation, and current channel policies

## Workflow

1. **Define the job and boundary.** List supported intents, prohibited decisions, and actions requiring a person or verified system.
2. **Ground answers.** Use approved, dated content; show uncertainty or ask a clarifying question when the record is incomplete.
3. **Constrain tools and data.** Give the assistant only the minimum data and permissions needed; require confirmation before consequential actions.
4. **Design safe recovery.** Create clear behavior for unsupported requests, complaints, payment disputes, safety concerns, prompt injection, and system outages.
5. **Make handoff real.** Offer an accessible human route, pass relevant context with consent, and avoid claiming a handoff has happened until it has.
6. **Test before release.** Test common tasks, ambiguous wording, Arabic dialect and mixed-script input, adversarial instructions, privacy leakage, and failure recovery.
7. **Monitor and update.** Review sampled conversations, escalation and correction reasons, approved-content changes, access logs, and channel policy updates.

## Expected output

> A bounded assistant specification, approved knowledge set, escalation map, test cases, and an owner for ongoing review.

## Boundaries and human review

> Do not let generated text set prices, promise outcomes, access accounts, or execute irreversible actions without a trusted control and human-approved policy.

## Relationship to existing work

> Builds on the WhatsApp Commerce Conversations playbook; this framework adds model-specific security, tool permissions, evaluation, and safe failure design.

## Primary sources

- https://genai.owasp.org/llm-top-10/
- https://business.whatsapp.com/policy
- https://www.nist.gov/itl/ai-risk-management-framework

Recheck source material and current policies before execution; these references are not legal approval.
