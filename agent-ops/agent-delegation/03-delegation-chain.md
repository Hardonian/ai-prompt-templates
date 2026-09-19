# Multi-Level Delegation Chain

## Prompt Template

You are the orchestrator. Delegate [TASK] through this chain:

Level 1: [AGENT_1] — [RESPONSIBILITY_1] → outputs [ARTIFACT_1]
Level 2: [AGENT_2] — [RESPONSIBILITY_2] (takes [ARTIFACT_1] as input) → outputs [ARTIFACT_2]
Level 3: [AGENT_3] — [RESPONSIBILITY_3] (takes [ARTIFACT_2] as input) → outputs [FINAL_OUTPUT]

If any level fails, retry [RETRY_COUNT] times then escalate to [FALLBACK_HANDLER].
Validate each artifact before passing to the next level using [VALIDATION_CRITERIA].

## Variables

- `[TASK]` — top-level task description
- `[AGENT_N]` — agent role at each level
- `[RESPONSIBILITY_N]` — what each agent does
- `[ARTIFACT_N]` — intermediate deliverable
- `[FINAL_OUTPUT]` — end deliverable
- `[RETRY_COUNT]` — retry limit per level
- `[FALLBACK_HANDLER]` — human or agent fallback
- `[VALIDATION_CRITERIA]` — gate between levels

## Example

You are the orchestrator. Delegate `build a REST API for task management` through this chain:

Level 1: `architect` — `design the API schema and endpoints` → outputs `api-design.md`
Level 2: `backend-dev` — `implement endpoints per design` (takes `api-design.md` as input) → outputs `src/api/`
Level 3: `qa-engineer` — `write integration tests` (takes `src/api/` as input) → outputs `tests/api/`

If any level fails, retry `2` times then escalate to `tech-lead`.
Validate each artifact before passing to the next level using `schema lint + type checking`.

## Tips

- Chain delegation mirrors real team workflows — agents specialize
- Validation gates between levels prevent garbage-in-garbage-out
- Fallback handlers are essential — never let a chain deadlock
