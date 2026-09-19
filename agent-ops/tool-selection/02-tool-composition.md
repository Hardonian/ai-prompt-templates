# Tool Composition Chains

## Prompt Template

For [COMPLEX_TASK], compose tools into a chain:

Chain definition:
```
Step 1: [TOOL_1]([INPUT_1]) → [OUTPUT_1]
Step 2: [TOOL_2]([OUTPUT_1]) → [OUTPUT_2]
Step 3: [TOOL_3]([OUTPUT_2]) → [FINAL_OUTPUT]
```

Composition rules:
- Each step's input must match previous step's output type
- Intermediate results stored in [STORAGE_LOCATION]
- If any step fails: [CHAIN_FAILURE_STRATEGY]
- Timeout per step: [STEP_TIMEOUT]

Reusable chains:
- Save successful chains as [CHAIN_NAME] for reuse
- Parameterize inputs for different contexts

## Variables

- `[COMPLEX_TASK]` — multi-tool task
- `[TOOL_N]` — tool at each step
- `[INPUT_N]` / `[OUTPUT_N]` — data flow
- `[STORAGE_LOCATION]` — temp storage
- `[CHAIN_FAILURE_STRATEGY]` — error handling
- `[STEP_TIMEOUT]` — per-step limit
- `[CHAIN_NAME]` — reusable chain name

## Example

For `find all TODO comments and create issues for them`, compose tools into a chain:

Chain definition:
```
Step 1: search_files("TODO|FIXME|HACK") → todo_list.json
Step 2: execute_code(parse todo_list.json, extract context) → structured_todos.json
Step 3: terminal(gh issue create for each) → issue_urls.json
```

## Tips

- Tool composition turns ad-hoc workflows into repeatable processes
- Type checking between steps prevents runtime failures
- Save proven chains — they're valuable organizational knowledge
