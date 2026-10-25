# AI-assisted marketing decisions & measurement

Keep campaign automation accountable by separating platform-reported signals from business outcomes, documenting decisions, and setting human review and rollback rules.

## When to use

Use when AI or platform automation recommends budgets, audiences, bids, creative, lead scoring, or campaign changes.

## Inputs

- Business objective and the actual downstream outcome that matters
- Current conversion definitions, data sources, attribution settings, unit economics, and known limitations
- Change permissions, budget guardrails, human owner, and rollback criteria

## Workflow

1. **Define the decision.** State what the system may recommend or change and what remains human-approved.
2. **Trace the measurement chain.** Map event → platform receipt → attribution → qualified outcome → revenue or contribution; do not treat these as interchangeable.
3. **Set decision guardrails.** Specify allowable budget movement, exclusions, frequency, audience or creative constraints, and approval thresholds.
4. **Check data quality.** Validate event meaning, deduplication, time zone, currency, consent, delayed outcomes, and CRM reconciliation before interpreting results.
5. **Evaluate the recommendation.** Compare against a relevant baseline or controlled test where feasible; note confounders and uncertainty rather than claiming causality.
6. **Release with rollback.** Use staged changes, named owner, monitoring window, stop conditions, and a documented way to restore the prior state.
7. **Review the business result.** Reconcile qualified leads, cancellations, returns, and realized contribution; feed verified learning back into the next decision.

## Expected output

> A decision log, measurement map, guardrail and rollback plan, experiment or comparison note, and reconciled business outcome.

## Boundaries and human review

> Platform dashboards and model recommendations are not independent proof of incremental or profitable business impact.

## Relationship to existing work

> Extends existing measurement and incrementality playbooks with an explicit governance layer for AI recommendations, automation permissions, and rollback.

## Primary sources

- https://www.nist.gov/itl/ai-risk-management-framework
- https://support.google.com/google-ads/answer/14697340?hl=en
- https://support.google.com/google-ads/answer/6325042?hl=en

Recheck source material and current policies before execution; these references are not legal approval.
