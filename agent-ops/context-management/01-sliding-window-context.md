# Sliding Window Context Management

## Prompt Template

Manage context for [LONG_CONVERSATION] using sliding window:

Window configuration:
- System prompt: always included (size: [SYSTEM_SIZE] tokens)
- Recent messages: last [RECENT_COUNT] messages always included
- Summary window: [SUMMARY_SIZE] token budget for older context
- Total budget: [TOTAL_BUDGET] tokens

When context exceeds budget:
1. Summarize messages older than [RECENT_COUNT] into running summary
2. Preserve key decisions, facts, and action items in summary
3. Drop raw messages that have been summarized
4. Keep all tool call results that are still relevant

Summary format:
```
## Context Summary
- Key decisions: [DECISIONS]
- Facts established: [FACTS]
- Open items: [OPEN_ITEMS]
- Files modified: [FILES]
```

## Variables

- `[LONG_CONVERSATION]` — extended interaction
- `[SYSTEM_SIZE]` — e.g. `2000 tokens`
- `[RECENT_COUNT]` — e.g. `10 messages`
- `[SUMMARY_SIZE]` — e.g. `1000 tokens`
- `[TOTAL_BUDGET]` — e.g. `8000 tokens`

## Example

Manage context for `multi-hour debugging session` using sliding window:

Window configuration:
- System prompt: always included (size: `2000` tokens)
- Recent messages: last `10` messages always included
- Summary window: `1000` token budget for older context
- Total budget: `8000` tokens

## Tips

- Summarization is lossy — preserve facts, drop narrative
- Tool results are often more valuable than conversation history
- Running summaries prevent the "what were we doing?" problem
