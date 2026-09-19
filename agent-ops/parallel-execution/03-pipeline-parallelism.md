# Pipeline Parallelism Pattern

## Prompt Template

Set up pipeline for [PROCESS]:

Stage 1: [STAGE_1_NAME] — agent: [AGENT_1] — processes: [BATCH_SIZE]
Stage 2: [STAGE_2_NAME] — agent: [AGENT_2] — processes: [BATCH_SIZE]
Stage 3: [STAGE_3_NAME] — agent: [AGENT_3] — processes: [BATCH_SIZE]

Pipeline flow:
```
[INPUT] → Stage1 → buffer → Stage2 → buffer → Stage3 → [OUTPUT]
```

Each stage:
- Reads from input buffer
- Processes [BATCH_SIZE] items
- Writes to output buffer
- Reports throughput every [MEASUREMENT_INTERVAL]

Bottleneck detection:
- If buffer depth > [BUFFER_THRESHOLD]: stage is bottleneck
- Solution: scale bottleneck stage with more agents

## Variables

- `[PROCESS]` — end-to-end process
- `[STAGE_N_NAME]` — pipeline stage
- `[AGENT_N]` — stage executor
- `[BATCH_SIZE]` — items per batch
- `[BUFFER_THRESHOLD]` — bottleneck signal
- `[MEASUREMENT_INTERVAL]` — metrics frequency

## Example

Set up pipeline for `content creation workflow`:

Stage 1: `Research` — agent: `researcher` — processes: `1 article`
Stage 2: `Write draft` — agent: `writer` — processes: `1 article`
Stage 3: `Edit and format` — agent: `editor` — processes: `1 article`

Pipeline flow:
`Topic list → Research → buffer → Writing → buffer → Editing → Published articles`

## Tips

- Pipeline parallelism = different stages work on different items simultaneously
- Buffer management prevents fast stages from overwhelming slow ones
- Measure throughput per stage to find bottlenecks
