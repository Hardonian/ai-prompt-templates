# Intelligent Tool Routing

## Prompt Template

Route [INTENT] to the appropriate tool:

Intent → Tool mapping:
| Intent Pattern | Tool | Confidence Threshold |
|---------------|------|---------------------|
[INTENT_TABLE]

Routing logic:
1. Parse user intent from [USER_INPUT]
2. Match against intent patterns
3. If confidence > threshold: execute tool
4. If confidence in range [AMBIGUITY_RANGE]: ask for clarification
5. If no match: suggest closest tool or ask for more context

Multi-tool intents:
- If intent requires multiple tools: plan execution order
- Dependencies between tools: [TOOL_DEPENDENCIES]
- Parallel-safe tools: [PARALLEL_TOOLS]

## Variables

- `[INTENT]` — what the user wants
- `[INTENT_TABLE]` — pattern-to-tool mappings
- `[USER_INPUT]` — raw request
- `[AMBIGUITY_RANGE]` — e.g. `0.4-0.7`
- `[TOOL_DEPENDENCIES]` — which tools need others' output
- `[PARALLEL_TOOLS]` — which can run together

## Example

Route `find and fix the bug in user authentication` to the appropriate tool:

Intent → Tool mapping:
| Intent Pattern | Tool | Confidence Threshold |
|---------------|------|---------------------|
| find bug | search_files + read_file | 0.8 |
| fix code | patch + terminal | 0.7 |
| run tests | terminal | 0.9 |

## Tips

- Good routing prevents "I'll just read the whole codebase" waste
- Ambiguity handling is better than wrong tool selection
- Multi-tool plans should specify execution order
