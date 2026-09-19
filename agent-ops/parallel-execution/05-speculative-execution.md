# Speculative Execution Pattern

## Prompt Template

For [CRITICAL_TASK], run speculative parallel execution:

1. Spawn [AGENT_COUNT] agents with different approaches:
   - Agent A: [APPROACH_A]
   - Agent B: [APPROACH_B]
   - Agent C: [APPROACH_C]

2. Race condition: first valid result wins
3. Cancel remaining agents when winner is confirmed
4. Validate winner against [VALIDATION_CRITERIA]

Selection criteria (in order):
1. Correctness: output passes validation
2. Speed: faster result preferred among correct ones
3. Resource cost: cheaper approach preferred among equal-speed results

Timeout: cancel all after [MAX_TIMEOUT], report partial results

## Variables

- `[CRITICAL_TASK]` — high-stakes task
- `[AGENT_COUNT]` — parallel attempts
- `[APPROACH_N]` — different strategies
- `[VALIDATION_CRITERIA]` — how to judge
- `[MAX_TIMEOUT]` — hard limit

## Example

For `resolve production incident: API returning 500s`, run speculative parallel execution:

1. Spawn `3` agents with different approaches:
   - Agent A: `Check recent deployments and rollback`
   - Agent B: `Analyze error logs and stack traces`
   - Agent C: `Check infrastructure metrics (CPU, memory, disk)`

2. Race condition: first valid diagnosis wins
3. Cancel remaining agents when winner is confirmed

## Tips

- Speculative execution trades cost for speed on critical paths
- Validation must be objective — "sounds right" isn't enough
- Always cancel losers to avoid wasting resources
