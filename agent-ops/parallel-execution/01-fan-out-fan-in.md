# Fan-Out / Fan-In Pattern

## Prompt Template

Fan out [TASK] into [N] parallel subtasks:

Fan-out:
[SUBTASK_1] | [SUBTASK_2] | ... | [SUBTASK_N]

Each subtask runs independently with:
- Own context: [CONTEXT_PER_SUBTASK]
- Own timeout: [SUBTASK_TIMEOUT]
- Output to: [OUTPUT_LOCATION_N]

Fan-in (after ALL subtasks complete):
1. Collect all outputs from [OUTPUT_LOCATION]
2. Validate each output against [OUTPUT_SCHEMA]
3. Merge using [MERGE_STRATEGY]
4. Produce final result: [FINAL_OUTPUT]

Partial failure handling:
- If [FAILURE_THRESHOLD] subtasks fail → abort and report
- Successful partial results preserved for debugging

## Variables

- `[TASK]` — what to parallelize
- `[N]` — parallelism degree
- `[SUBTASK_N]` — individual work items
- `[CONTEXT_PER_SUBTASK]` — isolated context
- `[SUBTASK_TIMEOUT]` — per-task timeout
- `[OUTPUT_LOCATION_N]` — where to write
- `[OUTPUT_SCHEMA]` — expected format
- `[MERGE_STRATEGY]` — how to combine
- `[FINAL_OUTPUT]` — end result
- `[FAILURE_THRESHOLD]` — how many failures are ok

## Example

Fan out `analyze all Python files in src/` into `4` parallel subtasks:

Fan-out:
`Analyze src/api/` | `Analyze src/models/` | `Analyze src/services/` | `Analyze src/utils/`

Fan-in (after ALL subtasks complete):
1. Collect all outputs from `/tmp/analysis/`
2. Validate each output is valid JSON with `file_count` and `issues` fields
3. Merge using `concatenate and deduplicate by file path`
4. Produce final result: `full-analysis-report.json`

## Tips

- Fan-out degree should match available agents, not file count
- Always validate outputs before merging — one bad output poisons the merge
- Fan-in is where most parallel workflows break — invest in merge logic
