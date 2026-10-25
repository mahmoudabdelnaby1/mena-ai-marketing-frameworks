# FW-045 — Worked Example

**Illustrative technical scenario only.** A customer unsubscribes from email while a marketing audience is also synced to an SMS provider and an ad platform.

The team maps each connection, records the preference event in the CRM system of record, verifies that downstream systems receive a suppression update, and tests duplicate and delayed webhook delivery. A reconciliation report flags any destination that failed to update so an operator can hold affected sends while resolving it.

The example describes an integration check, not a claim about any law or provider's default behavior.
