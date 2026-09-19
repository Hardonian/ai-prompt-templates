# Time-Based Escalation

## Prompt Template

Task [TASK] has been running for [ELAPSED_TIME]:

Time thresholds:
- [TIER_1_TIME]: normal operation, no action
- [TIER_2_TIME]: log warning, check for stuck state
- [TIER_3_TIME]: attempt [RECOVERY_ACTION]
- [TIER_4_TIME]: escalate to [ESCALATION_TARGET]

Stuck detection:
- No progress for [STALL_THRESHOLD]: likely stuck
- Same error repeated [ERROR_REPEAT_COUNT] times: stuck in loop
- Tool calls not producing output: tool failure

Recovery actions per tier:
- Tier 2: checkpoint current state, continue
- Tier 3: checkpoint, try alternative approach
- Tier 4: checkpoint, escalate with full state dump

## Variables

- `[TASK]` — what's running
- `[ELAPSED_TIME]` — how long it's been
- Time thresholds per tier
- Stuck detection parameters
- Recovery actions per tier

## Example

Task `database migration` has been running for `45 minutes`:

Time thresholds:
- `15 minutes`: normal operation
- `30 minutes`: log warning, check progress
- `45 minutes`: attempt `check migration locks, verify DB connections`
- `60 minutes`: escalate to `DBA on call`

## Tips

- Time-based escalation prevents runaway agents from burning resources
- Stuck detection is more nuanced than just elapsed time
- Checkpointing before escalation preserves work for the human
