# Swarm Escalation Pattern

## Prompt Template

When [SINGLE_AGENT] can't resolve [ISSUE]:

Swarm escalation:
1. Broadcast issue to [SWARM_AGENTS] with full context
2. Each agent proposes approach: [APPROACH_FORMAT]
3. Score approaches: [SCORING_CRITERIA]
4. Top [TOP_N] approaches execute in parallel
5. First successful result wins
6. Losing approaches provide learning data

Swarm rules:
- Max swarm size: [MAX_SWARM_SIZE]
- Timeout per approach: [APPROACH_TIMEOUT]
- Total swarm timeout: [SWARM_TIMEOUT]
- Resource cap: [RESOURCE_CAP]

Learning from swarm:
- Record all approaches and outcomes
- Update [KNOWLEDGE_BASE] with what worked
- Improve routing for similar future issues

## Variables

- `[SINGLE_AGENT]` — initial agent
- `[ISSUE]` — what's wrong
- `[SWARM_AGENTS]` — available agents
- `[APPROACH_FORMAT]` — proposal structure
- `[SCORING_CRITERIA]` — how to rank
- Various limits

## Example

When `debug-agent` can't resolve `intermittent test failure in CI`:

Swarm escalation:
1. Broadcast to `[log-analyzer, env-checker, test-specialist]` with full context
2. Each proposes approach
3. Score by `relevance to error pattern, historical success rate`
4. Top `2` approaches execute in parallel

## Tips

- Swarm escalation is expensive — use for genuinely hard problems
- Scoring prevents wasting resources on unlikely approaches
- Learning from swarm results improves future single-agent routing
