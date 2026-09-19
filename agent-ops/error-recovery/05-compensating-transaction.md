# Compensating Transaction Pattern

## Prompt Template

Execute multi-step operation with compensation:

Forward steps:
1. [STEP_1] → record compensation: [COMPENSATION_1]
2. [STEP_2] → record compensation: [COMPENSATION_2]
3. [STEP_3] → record compensation: [COMPENSATION_3]

If step N fails:
- Execute compensations in REVERSE order: N-1, N-2, ..., 1
- Each compensation must be idempotent
- Log each compensation execution
- Report: which steps completed, which were compensated, final state

Compensation rules:
- Each compensation undoes exactly its forward step
- Compensations must succeed (retry until they do)
- If compensation fails: escalate to human with partial state

## Variables

- `[STEP_N]` — forward operation
- `[COMPENSATION_N]` — undo operation

## Example

Execute multi-step operation with compensation:

Forward steps:
1. `Create user account` → record compensation: `Delete user account`
2. `Assign default role` → record compensation: `Remove role assignment`
3. `Send welcome email` → record compensation: `Send cancellation email`

If step 2 fails:
- Execute: `Remove role assignment` → `Delete user account`

## Tips

- Sagas > distributed transactions for agent workflows
- Compensations must be idempotent — they may be retried
- Not everything is compensatable (emails sent) — note those as non-undoable
