# Agent-Effort Estimation Matrix

## Prompt Template

Estimate effort for each task using this matrix:

| Task | Complexity (1-5) | Token Estimate | Tool Calls | Dependencies | Risk (H/M/L) |
|------|------------------|----------------|------------|--------------|---------------|
[TASK_ROWS]

Scoring guide:
- Complexity 1: simple read/format
- Complexity 3: multi-file edit with tests
- Complexity 5: cross-system integration

Output: sorted by (risk × complexity), with recommended execution order.

## Variables

- `[TASK_ROWS]` — one row per task

## Example

Estimate effort for each task using this matrix:

| Task | Complexity (1-5) | Token Estimate | Tool Calls | Dependencies | Risk (H/M/L) |
|------|------------------|----------------|------------|--------------|---------------|
| Add pagination | 2 | 5K | 8 | none | L |
| Implement auth | 4 | 15K | 25 | DB schema | H |
| Write tests | 3 | 10K | 15 | endpoints | M |

## Tips

- Token estimates help budget agent runs
- Risk × complexity sorting tackles hard things first (fail fast)
- Tool call estimates reveal tasks that need more autonomous agent runs
