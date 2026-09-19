# Agent-to-Agent Handoff Protocol

## Prompt Template

Hand off [TASK] from [SOURCE_AGENT] to [TARGET_AGENT]:

Handoff package:
1. **Context summary**: [CONTEXT_SUMMARY] (≤[SUMMARY_LENGTH] words)
2. **Work completed**: [COMPLETED_WORK]
3. **Current state**: [CURRENT_STATE]
4. **Remaining work**: [REMAINING_WORK]
5. **Blockers**: [BLOCKERS]
6. **Decisions made**: [DECISIONS]
7. **Files in progress**: [FILES]
8. **Recommended next steps**: [NEXT_STEPS]

Handoff protocol:
1. Source agent prepares handoff package
2. Target agent reviews and acknowledges
3. Target agent asks clarifying questions (max [MAX_QUESTIONS])
4. Source agent answers
5. Target agent accepts handoff
6. Source agent marks task as handed off

## Variables

- `[TASK]` — what's being handed off
- `[SOURCE_AGENT]` — handing off
- `[TARGET_AGENT]` — receiving
- `[CONTEXT_SUMMARY]` — compressed context
- Various state fields
- `[MAX_QUESTIONS]` — clarification limit

## Example

Hand off `user authentication implementation` from `backend-engineer` to `security-specialist`:

Handoff package:
1. **Context summary**: `Implementing OAuth2 + JWT auth for /api/v2`
2. **Work completed**: `OAuth2 flow, token generation, middleware`
3. **Current state**: `Working but needs security review`
4. **Remaining work**: `Rate limiting, token refresh, audit logging`
5. **Blockers**: `Unsure about token expiry best practices`
6. **Decisions made**: `JWT over session tokens, RS256 signing`

## Tips

- Good handoffs prevent the "starting from scratch" problem
- Context summaries should be actionable, not narrative
- Clarifying questions catch misunderstandings before they compound
