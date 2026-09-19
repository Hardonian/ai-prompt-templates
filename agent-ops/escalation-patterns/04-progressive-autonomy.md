# Progressive Autonomy Escalation

## Prompt Template

Agent [AGENT] is at autonomy level [CURRENT_LEVEL]:

Autonomy levels:
| Level | Permissions | Requires | Can Escalate To |
|-------|------------|----------|-----------------|
| L0: Observer | Read only | N/A | L1 |
| L1: Suggestor | Read + suggest | Human approval | L2 |
| L2: Executor | Read + write (scoped) | Self-validation | L3 |
| L3: Autonomous | Full scope | Periodic check-in | L4 |
| L4: Delegator | Can spawn sub-agents | Audit trail | Human |

Level-up criteria:
- [LEVEL_UP_CRITERIA] met for [CONSECUTIVE_SUCCESS_COUNT] tasks
- No escalations needed in last [STABLE_PERIOD]
- Peer review score ≥ [REVIEW_THRESHOLD]

Level-down triggers:
- [LEVEL_DOWN_TRIGGER] occurs
- Escalation rate > [ESCALATION_RATE_THRESHOLD]%
- Quality score drops below [QUALITY_THRESHOLD]

## Variables

- `[AGENT]` — which agent
- `[CURRENT_LEVEL]` — current autonomy
- Level definitions with permissions
- Level-up/down criteria

## Example

Agent `deployment-bot` is at autonomy level `L2: Executor`:

Level-up criteria:
- `5` consecutive successful deployments
- No escalations needed in last `7 days`
- Peer review score ≥ `4.0/5.0`

Level-down triggers:
- `Failed deployment` occurs
- Escalation rate > `20`%

## Tips

- Progressive autonomy builds trust incrementally
- Level-down is as important as level-up — don't promote on luck
- Audit trails at L4 are non-negotiable
