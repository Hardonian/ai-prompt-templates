# Retry with Exponential Backoff

## Prompt Template

Operation [OPERATION] failed with error: [ERROR_MESSAGE]

Retry strategy:
- Max retries: [MAX_RETRIES]
- Base delay: [BASE_DELAY] seconds
- Backoff multiplier: [MULTIPLIER]
- Max delay: [MAX_DELAY] seconds
- Retryable errors: [RETRYABLE_ERRORS]
- Fatal errors (no retry): [FATAL_ERRORS]

On each retry:
1. Log attempt number and error
2. Adjust approach if [ADAPTIVE_CONDITION]
3. Wait calculated delay
4. Retry with same or modified parameters

If all retries exhausted:
1. Collect all error messages
2. Attempt [FALLBACK_STRATEGY]
3. Report failure with full context

## Variables

- `[OPERATION]` — what was attempted
- `[ERROR_MESSAGE]` — actual error
- `[MAX_RETRIES]` — e.g. `3`
- `[BASE_DELAY]` — e.g. `1`
- `[MULTIPLIER]` — e.g. `2`
- `[MAX_DELAY]` — e.g. `30`
- `[RETRYABLE_ERRORS]` — transient errors
- `[FATAL_ERRORS]` — don't retry
- `[ADAPTIVE_CONDITION]` — when to change approach
- `[FALLBACK_STRATEGY]` — last resort

## Example

Operation `deploy to staging` failed with error: `connection timeout`

Retry strategy:
- Max retries: `3`
- Base delay: `2` seconds
- Backoff multiplier: `2`
- Max delay: `30` seconds
- Retryable errors: `timeout, connection refused, 503`
- Fatal errors (no retry): `auth failure, 404, invalid config`

## Tips

- Always distinguish transient from fatal errors — retrying a 404 wastes tokens
- Adaptive retries (change approach on retry) beat blind retries
- Fallback strategies prevent total failure — degrade gracefully
