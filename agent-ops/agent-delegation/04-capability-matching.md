# Capability-Based Agent Selection

## Prompt Template

Given this task: [TASK_DESCRIPTION]

Select the best agent from this registry based on capability match:

| Agent | Capabilities | Tools | Cost Tier |
|-------|-------------|-------|-----------|
[AGENT_TABLE]

Selection criteria (weighted):
1. Capability match: [CAPABILITY_WEIGHT]%
2. Tool availability: [TOOL_WEIGHT]%
3. Cost efficiency: [COST_WEIGHT]%
4. Current load: [LOAD_WEIGHT]%

Output: selected agent name, justification, and delegation prompt.

## Variables

- `[TASK_DESCRIPTION]` — what needs to be done
- `[AGENT_TABLE]` — rows of agent specs
- `[CAPABILITY_WEIGHT]` etc. — priority weights

## Example

Given this task: `Refactor the authentication middleware to use JWT`

Select the best agent from this registry based on capability match:

| Agent | Capabilities | Tools | Cost Tier |
|-------|-------------|-------|-----------|
| code-reviewer | review, lint, suggest | read_file, search_files | low |
| backend-engineer | implement, refactor, debug | read_file, write_file, terminal | medium |
| security-audit | vuln scan, auth review | read_file, search_files, terminal | high |

Selection criteria (weighted):
1. Capability match: 40%
2. Tool availability: 25%
3. Cost efficiency: 20%
4. Current load: 15%

Output: selected agent name, justification, and delegation prompt.

## Tips

- Prevents over-assigning expensive agents to simple tasks
- Weight tuning is domain-specific — security tasks should weight capability > cost
- Works as a router pattern in multi-agent systems
