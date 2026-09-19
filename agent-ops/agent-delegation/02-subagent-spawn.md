# Subagent Spawn with Bounded Context

## Prompt Template

Spawn a [AGENT_TYPE] subagent with the following bounded context:

**Task:** [TASK_DESCRIPTION]
**Input artifacts:** [INPUT_FILES_OR_DATA]
**Expected output:** [OUTPUT_SPEC]
**Timeout:** [TIMEOUT]
**Max retries:** [MAX_RETRIES]

The subagent should NOT have access to [RESTRICTED_RESOURCES].
Pass only these context files: [CONTEXT_FILES].

## Variables

- `[AGENT_TYPE]` — type of subagent (e.g. `code-reviewer`, `test-writer`)
- `[TASK_DESCRIPTION]` — precise task
- `[INPUT_FILES_OR_DATA]` — what to pass in
- `[OUTPUT_SPEC]` — expected deliverable format
- `[TIMEOUT]` — max duration
- `[MAX_RETRIES]` — retry count
- `[RESTRICTED_RESOURCES]` — what to keep away from
- `[CONTEXT_FILES]` — minimal context to pass

## Example

Spawn a `test-writer` subagent with the following bounded context:

**Task:** `Write unit tests for the UserService class`
**Input artifacts:** `src/services/user.ts, src/models/user.ts`
**Expected output:** `src/services/__tests__/user.test.ts with >90% branch coverage`
**Timeout:** `5 minutes`
**Max retries:** `2`

The subagent should NOT have access to `production configs, .env files`.
Pass only these context files: `src/services/user.ts, src/models/user.ts, jest.config.ts`.

## Tips

- Smaller context = faster, more focused subagent output
- Always set timeouts — runaway subagents burn tokens
- Restricting resources prevents accidental prod access
