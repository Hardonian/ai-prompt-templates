# Regression Output Validation

## Prompt Template

Validate [NEW_OUTPUT] against [BASELINE_OUTPUT]:

Comparison checks:
1. Behavioral equivalence: same inputs → same outputs for [TEST_CASES]?
2. Performance delta: latency/throughput within [PERF_THRESHOLD]%?
3. Output diff: only expected changes in [DIFF_CRITERIA]?
4. Backward compatibility: [OLD_CONSUMERS] still work with new output?
5. API contract: [API_CONTRACT] maintained?

Diff analysis:
```json
{
  "expected_changes": [...],
  "unexpected_changes": [...],
  "missing_outputs": [...],
  "new_outputs": [...]
}
```

Regression gate: BLOCK if any unexpected changes or missing outputs.

## Variables

- `[NEW_OUTPUT]` — what to validate
- `[BASELINE_OUTPUT]` — reference
- `[TEST_CASES]` — regression tests
- `[PERF_THRESHOLD]` — acceptable degradation
- `[DIFF_CRITERIA]` — what should have changed
- `[OLD_CONSUMERS]` — downstream users
- `[API_CONTRACT]` — interface spec

## Example

Validate `new API response format` against `current production responses`:

Comparison checks:
1. Behavioral equivalence: same inputs → same outputs for `existing test suite`?
2. Performance delta: latency within `10`%?
3. Output diff: only expected changes in `added pagination fields`?
4. Backward compatibility: `existing API clients` still work?

## Tips

- Regression validation is essential for any output that replaces existing output
- "Unexpected changes" are the most valuable finding
- Backward compatibility checks prevent breaking downstream consumers
