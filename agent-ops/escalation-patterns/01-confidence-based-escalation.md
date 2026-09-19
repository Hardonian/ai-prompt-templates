# Confidence-Based Escalation

## Prompt Template

Agent confidence for [ACTION]: [CONFIDENCE_SCORE]%

Escalation thresholds:
- ≥ 90%: execute autonomously
- 70-89%: execute with logging, flag for spot-check
- 50-69%: pause and request confirmation from [CONFIRMER]
- < 50%: escalate to [EXPERT] with full reasoning

Confidence factors:
- Task familiarity: [FAMILIARITY_SCORE]%
- Input quality: [INPUT_QUALITY_SCORE]%
- Tool reliability: [TOOL_RELIABILITY_SCORE]%
- Historical success rate: [HISTORY_SCORE]%

Low confidence actions:
1. Log reasoning and uncertainty factors
2. Prepare alternative approaches
3. Present options to human with recommendation
4. Wait for decision before proceeding

## Variables

- `[ACTION]` — what agent wants to do
- `[CONFIDENCE_SCORE]` — computed confidence
- `[CONFIRMER]` — who confirms
- `[EXPERT]` — who decides
- Various factor scores

## Example

Agent confidence for `delete all user sessions`: `35`%

Escalation thresholds:
- ≥ 90%: execute autonomously
- 70-89%: execute with logging, flag for spot-check
- 50-69%: pause and request confirmation from `team lead`
- < 50%: escalate to `admin` with full reasoning

Low confidence actions:
1. Log reasoning: `Bulk operation, irreversible, affecting all users`
2. Present options: `Delete all vs delete inactive only vs delete by age`

## Tips

- Confidence calibration is hard — err on side of escalation early on
- Factor scores make confidence explainable, not magic
- Over time, track if confidence correlates with actual success
