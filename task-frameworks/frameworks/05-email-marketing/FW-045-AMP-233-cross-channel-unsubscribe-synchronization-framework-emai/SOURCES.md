# Evidence Register & Source Boundaries — `FW-045`

This is a technical design workflow. Legal and platform requirements must be verified independently for each market and channel.

| Evidence area | Review |
|---|---|
| CRM and messaging-vendor API documentation | Confirm event fields, authentication, retries, idempotency, rate limits, and failure behavior in current docs. |
| Internal preference and suppression records | Confirm the source, timestamp, scope, and system of record for each preference event. |
| Market-specific privacy and communications rules | Ask a qualified reviewer which preferences must be captured, how they apply, and how long records must be retained. |

Do not treat one vendor's default behavior as a universal legal rule.
