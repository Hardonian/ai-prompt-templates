# Task-Specific Context Injection

## Prompt Template

Inject relevant context for [TASK_TYPE]:

Context layers:
1. **Global** (always): [GLOBAL_CONTEXT]
2. **Project** (per project): [PROJECT_CONTEXT]
3. **Task** (per task): [TASK_CONTEXT]
4. **Dynamic** (computed): [DYNAMIC_CONTEXT]

Injection rules:
- Global context: include in system prompt, never modify
- Project context: load from [PROJECT_CONFIG] at session start
- Task context: load from [TASK_ARTIFACTS] per task
- Dynamic context: compute from [CONTEXT_COMMANDS] on demand

Context budget per layer:
- Global: [GLOBAL_BUDGET] tokens
- Project: [PROJECT_BUDGET] tokens
- Task: [TASK_BUDGET] tokens
- Dynamic: [DYNAMIC_BUDGET] tokens

## Variables

- `[TASK_TYPE]` — category of work
- `[GLOBAL_CONTEXT]` — universal instructions
- `[PROJECT_CONTEXT]` — project-specific
- `[TASK_CONTEXT]` — task-specific
- `[DYNAMIC_CONTEXT]` — computed at runtime
- Budgets per layer

## Example

Inject relevant context for `code review`:

Context layers:
1. **Global** (always): `coding standards, security rules`
2. **Project** (per project): `architecture decisions, tech stack`
3. **Task** (per task): `PR description, diff, related issues`
4. **Dynamic** (computed): `recent changes to same files, test coverage`

## Tips

- Layering prevents context bloat — only inject what's relevant
- Dynamic context (recent changes, coverage) is most valuable for reviews
- Budget per layer forces prioritization
