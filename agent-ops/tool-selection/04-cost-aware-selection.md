# Cost-Aware Tool Selection

## Prompt Template

Select tool for [OPERATION] considering cost:

| Tool | Token Cost | Latency | Accuracy | Reliability |
|------|-----------|---------|----------|-------------|
[TOOL_TABLE]

Selection algorithm:
1. Filter tools that can accomplish [OPERATION]
2. Score each: `score = (accuracy × [ACC_WEIGHT]) + (reliability × [REL_WEIGHT]) - (cost × [COST_WEIGHT]) - (latency × [LAT_WEIGHT])`
3. Select highest scoring tool
4. If top 2 scores within [MARGIN]%: prefer cheaper option

Cost caps:
- Per-operation budget: [OP_BUDGET]
- Per-session budget: [SESSION_BUDGET]
- If cheapest option exceeds budget: escalate to human

## Variables

- `[OPERATION]` — what to do
- `[TOOL_TABLE]` — tool specs
- Weight parameters
- Budget constraints

## Example

Select tool for `search codebase for security vulnerabilities` considering cost:

| Tool | Token Cost | Latency | Accuracy | Reliability |
|------|-----------|---------|----------|-------------|
| search_files (grep) | Low | Fast | Medium | High |
| execute_code (semgrep) | Medium | Medium | High | High |
| browser_exec (SaaS scanner) | High | Slow | Very High | Medium |

## Tips

- Cost awareness prevents over-engineering simple tasks
- Weights are domain-specific: security work weights accuracy > cost
- Budget caps prevent runaway agent spending
