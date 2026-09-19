# Tool Fallback Chains

## Prompt Template

When [PRIMARY_TOOL] fails or is unavailable:

Fallback chain:
1. [PRIMARY_TOOL] — preferred for [REASON_1]
   ↓ if unavailable/fails
2. [FALLBACK_1] — alternative for [REASON_2]
   ↓ if unavailable/fails
3. [FALLBACK_2] — last resort for [REASON_3]
   ↓ if unavailable/fails
4. [MANUAL_STRATEGY] — human completes the step

Selection criteria for fallback:
- Capability match: does fallback support the operation?
- Data format: is output compatible with downstream steps?
- Performance: is latency acceptable?
- Reliability: historical success rate?

## Variables

- `[PRIMARY_TOOL]` — ideal choice
- `[FALLBACK_N]` — alternatives
- `[REASON_N]` — why each is preferred
- `[MANUAL_STRATEGY]` — human backup

## Example

When `terminal (run pytest)` fails or is unavailable:

Fallback chain:
1. `terminal (pytest)` — preferred for `full test suite with plugins`
   ↓ if unavailable/fails
2. `execute_code (subprocess.run pytest)` — alternative for `more control over output`
   ↓ if unavailable/fails
3. `terminal (python -m unittest discover)` — last resort for `no pytest dependency`
   ↓ if unavailable/fails
4. `Manual: ask user to run tests locally`

## Tips

- Fallback chains prevent single-point-of-failure in tool usage
- Not all fallbacks produce identical output — adjust downstream parsing
- Track fallback frequency to justify tool improvements
