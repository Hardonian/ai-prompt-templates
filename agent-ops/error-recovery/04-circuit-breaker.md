# Circuit Breaker Pattern

## Prompt Template

Track failures for [OPERATION]:

State machine:
- CLOSED (normal): execute normally, count failures
- OPEN (tripped): [FAILURE_THRESHOLD] failures in [WINDOW] → block all calls for [COOL_OFF]
- HALF-OPEN (testing): after cool-off, allow [PROBE_COUNT] test calls

Transitions:
- CLOSED → OPEN: failures hit threshold
- OPEN → HALF-OPEN: cool-off expires
- HALF-OPEN → CLOSED: probe calls succeed
- HALF-OPEN → OPEN: probe calls fail → reset cool-off

When circuit is OPEN:
1. Return cached/default response [DEFAULT_RESPONSE]
2. Log circuit trip with context
3. Alert [ALERT_TARGET]
4. Queue failed operations for retry when circuit closes

## Variables

- `[OPERATION]` — what to protect
- `[FAILURE_THRESHOLD]` — e.g. `5`
- `[WINDOW]` — e.g. `60 seconds`
- `[COOL_OFF]` — e.g. `5 minutes`
- `[PROBE_COUNT]` — e.g. `1`
- `[DEFAULT_RESPONSE]` — fallback
- `[ALERT_TARGET]` — who to notify

## Example

Track failures for `external API calls to payment gateway`:

State machine:
- CLOSED (normal): execute normally, count failures
- OPEN (tripped): `5` failures in `60 seconds` → block all calls for `5 minutes`
- HALF-OPEN (testing): after cool-off, allow `1` test calls

## Tips

- Circuit breakers prevent cascade failures in multi-agent systems
- Default responses should be safe, not just empty
- Cool-off prevents thundering herd when service recovers
