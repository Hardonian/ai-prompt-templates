# Hierarchical Task Breakdown

## Prompt Template

Decompose this objective into a work breakdown structure:

**Objective:** [OBJECTIVE]
**Constraints:** [CONSTRAINTS]
**Team capacity:** [TEAM_SIZE] agents, [TIMEBOX]

Output format:
```
OBJECTIVE
├── EPIC 1: [name]
│   ├── TASK 1.1: [name] — [agent] — [estimate]
│   │   ├── SUBTASK 1.1.1
│   │   └── SUBTASK 1.1.2
│   └── TASK 1.2: [name] — [agent] — [estimate]
├── EPIC 2: [name]
│   └── ...
└── DEPENDENCIES: [cross-epic deps]
```

Rules:
- No task should take more than [MAX_TASK_DURATION]
- Every task must have a clear owner and done criteria
- Identify critical path

## Variables

- `[OBJECTIVE]` — top-level goal
- `[CONSTRAINTS]` — time, resource, tech constraints
- `[TEAM_SIZE]` — available agents
- `[TIMEBOX]` — total time budget
- `[MAX_TASK_DURATION]` — task size cap

## Example

Decompose this objective into a work breakdown structure:

**Objective:** `Build a user authentication system with OAuth2 and RBAC`
**Constraints:** `Must use existing Postgres DB, no new infrastructure`
**Team capacity:** `3` agents, `2 days`

Rules:
- No task should take more than `2 hours`
- Every task must have a clear owner and done criteria
- Identify critical path

## Tips

- Break tasks until each is completable in one agent session
- Critical path identification prevents false parallelism
- Done criteria per task prevents "90% done" syndrome
