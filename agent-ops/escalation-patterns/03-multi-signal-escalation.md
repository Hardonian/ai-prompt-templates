# Multi-Signal Escalation

## Prompt Template

Monitor [TASK] for escalation signals:

Signal types:
| Signal | Weight | Threshold | Source |
|--------|--------|-----------|--------|
[SIGNAL_TABLE]

Escalation scoring:
```
score = Σ (signal_triggered × weight)
if score ≥ [ESCALATION_THRESHOLD]:
    escalate()
```

Signal categories:
- **Performance**: latency, throughput, resource usage
- **Quality**: error rate, test failures, validation failures
- **Behavioral**: loops, retries, unexpected patterns
- **External**: API failures, service degradation

When escalation triggers:
1. Snapshot all signal values
2. Compute contributing factors
3. Determine escalation level from score
4. Prepare diagnostic package
5. Escalate to appropriate handler

## Variables

- `[TASK]` — what to monitor
- `[SIGNAL_TABLE]` — signals with weights
- `[ESCALATION_THRESHOLD]` — trigger point

## Example

Monitor `API deployment` for escalation signals:

Signal types:
| Signal | Weight | Threshold | Source |
|--------|--------|-----------|--------|
| Error rate > 5% | 3 | 1 occurrence | logs |
| Latency > 2s | 2 | 3 occurrences | metrics |
| Test failures | 4 | 1 failure | CI |
| Retry count > 3 | 2 | 1 occurrence | agent |

## Tips

- Multi-signal escalation catches issues that single metrics miss
- Weighting prevents noise from low-importance signals
- Signal snapshot at escalation time enables fast diagnosis
