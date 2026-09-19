# Regression Detection Gate

## Prompt Template

Before and after [CHANGE], run regression detection:

1. Capture baseline: [BASELINE_COMMAND] → save as baseline.json
2. Apply change
3. Capture post-change: [BASELINE_COMMAND] → save as post.json
4. Diff baseline vs post:
   - New failures: tests that passed before, fail now
   - Performance delta: [PERF_METRICS] degradation > [THRESHOLD]%
   - Output changes: unexpected diffs in [CANARY_OUTPUTS]
5. Decision: PASS if no regressions, BLOCK if any critical regression

## Variables

- `[CHANGE]` — description of what changed
- `[BASELINE_COMMAND]` — command to capture state
- `[PERF_METRICS]` — latency, throughput, memory
- `[THRESHOLD]` — acceptable degradation %
- `[CANARY_OUTPUTS]` — outputs that shouldn't change

## Example

Before and after `refactor user service`, run regression detection:

1. Capture baseline: `pytest --json-report` → save as baseline.json
2. Apply change
3. Capture post-change: `pytest --json-report` → save as post.json
4. Diff baseline vs post:
   - New failures: tests that passed before, fail now
   - Performance delta: `response_time` degradation > `10`%
   - Output changes: unexpected diffs in `API response snapshots`

## Tips

- Canary outputs catch silent behavioral changes that tests miss
- Performance regression is the sneakiest — always measure before/after
- Store baselines in CI, not just locally
