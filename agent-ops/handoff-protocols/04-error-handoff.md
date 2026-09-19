# Error State Handoff

## Prompt Template

Error occurred in [AGENT] during [OPERATION]:

Error handoff package:
1. **Error**: [ERROR_MESSAGE]
2. **Stack trace**: [STACK_TRACE]
3. **Context at error**: [CONTEXT_SNAPSHOT]
4. **Input that caused error**: [FAULTY_INPUT]
5. **State before error**: [PRE_ERROR_STATE]
6. **Partial results**: [PARTIAL_RESULTS]
7. **Recovery attempted**: [RECOVERY_ATTEMPTS]

Handoff to [RECOVERY_AGENT]:
- If recoverable: pass error context + partial results for continuation
- If not recoverable: pass to human with full diagnostic package
- Always preserve: files modified before error, decisions made before error

## Variables

- `[AGENT]` — where error occurred
- `[OPERATION]` — what was being done
- Error details
- State snapshots
- `[RECOVERY_AGENT]` — who handles it

## Example

Error occurred in `test-runner` during `integration test suite execution`:

Error handoff package:
1. **Error**: `AssertionError: Expected 200, got 500 on POST /api/users`
2. **Context at error**: `Test: test_create_user, Line: 142`
3. **State before error**: `15 of 23 tests passed`
4. **Partial results**: `test-results-partial.json`

## Tips

- Error handoffs should be actionable, not just "it broke"
- Partial results prevent losing successful work before the error
- Context snapshots are essential for reproduction
