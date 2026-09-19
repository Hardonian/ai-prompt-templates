# Delegation with Feedback Loop

## Prompt Template

Delegate [TASK] to [AGENT] with a built-in feedback loop:

1. Agent executes task → produces [DRAFT_OUTPUT]
2. Reviewer evaluates [DRAFT_OUTPUT] against [ACCEPTANCE_CRITERIA]
3. If criteria NOT met: return structured feedback [FEEDBACK_FORMAT]
4. Agent revises based on feedback
5. Repeat until [MAX_ITERATIONS] or criteria met

Feedback format:
```json
{
  "passed": [LIST_OF_MET_CRITERIA],
  "failed": [LIST_OF_FAILED_CRITERIA],
  "suggestions": [ACTIONABLE_FIXES],
  "severity": "critical|major|minor"
}
```

## Variables

- `[TASK]` — the delegated task
- `[AGENT]` — executing agent
- `[DRAFT_OUTPUT]` — initial deliverable
- `[ACCEPTANCE_CRITERIA]` — quality bar
- `[FEEDBACK_FORMAT]` — structured review output
- `[MAX_ITERATIONS]` — loop limit

## Example

Delegate `write API documentation for /users endpoints` to `tech-writer` with a built-in feedback loop:

1. Agent executes task → produces `draft-docs.md`
2. Reviewer evaluates `draft-docs.md` against `every endpoint documented, examples included, error codes listed`
3. If criteria NOT met: return structured feedback
4. Agent revises based on feedback
5. Repeat until `3` iterations or criteria met

## Tips

- Feedback loops prevent fire-and-forget delegation
- Structured feedback is 10x more effective than "improve this"
- Set max iterations — diminishing returns after 2-3 rounds
