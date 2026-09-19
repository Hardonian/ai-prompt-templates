# Human Escalation Handoff

## Prompt Template

Escalate [ISSUE] to human operator:

Escalation package:
1. **Issue summary**: [ISSUE_SUMMARY] (≤[SUMMARY_LENGTH] words)
2. **Severity**: [SEVERITY] (P0/P1/P2/P3)
3. **What was tried**: [ATTEMPTS_MADE]
4. **Why it failed**: [FAILURE_REASONS]
5. **Impact**: [IMPACT_DESCRIPTION]
6. **Recommended action**: [RECOMMENDED_ACTION]
7. **Decision needed**: [DECISION_OPTIONS]
8. **Time sensitivity**: [TIME_PRESSURE]

Escalation rules:
- P0 (system down): escalate immediately, no retries
- P1 (feature broken): try [MAX_RETRIES] then escalate
- P2 (degraded): try [MAX_RETRIES] × 2 then escalate
- P3 (cosmetic): log for next review cycle

Human handoff format:
- Plain language, no jargon
- All context needed to decide in one read
- Clear options with pros/cons

## Variables

- `[ISSUE]` — what's wrong
- `[SEVERITY]` — priority level
- Various diagnostic fields
- `[DECISION_OPTIONS]` — what human needs to decide
- `[TIME_PRESSURE]` — urgency

## Example

Escalate `payment webhook failing silently` to human operator:

Escalation package:
1. **Issue summary**: `Stripe webhook for payment_success not triggering order fulfillment`
2. **Severity**: `P0`
3. **What was tried**: `Verified webhook URL, checked logs, tested with Stripe CLI`
4. **Why it failed**: `Webhook signature verification failing after key rotation`
5. **Impact**: `Orders paid but not fulfilled — affecting 47 customers`

## Tips

- Severity should drive escalation speed, not agent confidence
- "What was tried" prevents humans from repeating failed approaches
- Decision options with pros/cons enable fast human decisions
