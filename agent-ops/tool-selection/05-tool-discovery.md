# Dynamic Tool Discovery

## Prompt Template

For [UNKNOWN_TASK], discover available tools:

Discovery process:
1. List all available tools: [TOOL_REGISTRY]
2. For each tool, check:
   - Can it handle [TASK_TYPE]?
   - What are its input/output types?
   - What permissions does it need?
   - Is it currently available?
3. Rank by suitability
4. If no suitable tool found:
   a. Can tools be composed? → suggest chain
   b. Can a tool be configured differently? → suggest config
   c. Is a new tool needed? → suggest creation

Tool capability query format:
```
tool_search(query="[CAPABILITY_NEEDED]")
→ returns: matching tools with confidence scores
```

## Variables

- `[UNKNOWN_TASK]` — task without obvious tool
- `[TOOL_REGISTRY]` — available tools
- `[TASK_TYPE]` — category of work
- `[CAPABILITY_NEEDED]` — what's required

## Example

For `generate a PDF report from markdown`, discover available tools:

Discovery process:
1. List all available tools from registry
2. For each tool, check: can it convert markdown to PDF?
3. Rank by suitability
4. If no suitable tool found:
   a. Can `execute_code` + `pandoc` be composed?
   b. Can `terminal` run `wkhtmltopdf`?

## Tips

- Tool discovery prevents hardcoding tool assumptions
- Composition discovery (can tools be combined?) is often the answer
- New tool creation should be last resort
