# Context Compression for Long Tasks

## Prompt Template

Compress context for [LONG_RUNNING_TASK]:

Compression levels:
1. **Full**: raw context, all details (budget: [FULL_BUDGET])
2. **Working**: key facts + recent actions (budget: [WORKING_BUDGET])
3. **Summary**: high-level state only (budget: [SUMMARY_BUDGET])

Compression triggers:
- Context > [FULL_BUDGET]: compress to working
- Context > [WORKING_BUDGET]: compress to summary
- Task phase change: reset to working level

Compression rules:
- Never lose: decisions made, files modified, blockers found
- Safe to lose: intermediate reasoning, exploration steps, failed attempts
- Always preserve: task objective, acceptance criteria, current phase

## Variables

- `[LONG_RUNNING_TASK]` — extended operation
- Budgets per compression level
- Trigger thresholds

## Example

Compress context for `large-scale refactoring across 20 files`:

Compression levels:
1. **Full**: raw context, all details (budget: `12000` tokens)
2. **Working**: key facts + recent actions (budget: `4000` tokens)
3. **Summary**: high-level state only (budget: `1500` tokens)

Compression rules:
- Never lose: decisions made, files modified, blockers found
- Safe to lose: intermediate reasoning, exploration steps, failed attempts

## Tips

- Compression is essential for tasks that span many tool calls
- The "never lose" list is critical — wrong compression loses state
- Phase-change resets prevent carrying stale context forward
