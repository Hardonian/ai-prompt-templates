# Agent Memory Index Pattern

## Prompt Template

Maintain searchable memory index for [AGENT]:

Memory types:
1. **Episodic**: what happened when
   - Format: `{timestamp, event, outcome, lesson}`
   - Retention: [EPISODIC_RETENTION]
2. **Semantic**: facts and knowledge
   - Format: `{topic, fact, source, confidence}`
   - Retention: permanent
3. **Procedural**: how to do things
   - Format: `{task_type, approach, success_rate, notes}`
   - Retention: updated on each use

Memory operations:
- Store: after significant events or learnings
- Retrieve: before similar tasks (search by [MEMORY_KEYS])
- Update: when facts change or approaches improve
- Prune: remove outdated episodic memories after retention period

## Variables

- `[AGENT]` — which agent's memory
- `[EPISODIC_RETENTION]` — e.g. `7 days`
- `[MEMORY_KEYS]` — search dimensions

## Example

Maintain searchable memory index for `deployment agent`:

Memory types:
1. **Episodic**: what happened when
   - Format: `{timestamp, event, outcome, lesson}`
   - Retention: `30 days`
2. **Semantic**: facts and knowledge
   - Format: `{topic, fact, source, confidence}`
   - Retention: permanent

## Tips

- Memory prevents repeating mistakes across sessions
- Confidence scores help when memories conflict
- Pruning prevents unbounded memory growth
