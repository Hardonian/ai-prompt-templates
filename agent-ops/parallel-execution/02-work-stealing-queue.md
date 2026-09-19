# Work-Stealing Task Queue

## Prompt Template

Set up work-stealing queue for [TASK_BATCH]:

Queue setup:
1. Decompose [TASK_BATCH] into [N] tasks
2. Add all tasks to shared queue
3. Spawn [WORKER_COUNT] worker agents

Worker loop:
```
while queue not empty:
    task = queue.steal_or_own()
    if task:
        result = execute(task)
        results_queue.push(result)
    else:
        wait_or_help_other_worker()
```

Coordination:
- Queue is thread-safe (no duplicate execution)
- Workers report progress every [PROGRESS_INTERVAL]
- Slow workers get smaller tasks (adaptive sizing)
- Completion: all tasks processed OR [TIMEOUT]

## Variables

- `[TASK_BATCH]` — collection of work
- `[N]` — task count
- `[WORKER_COUNT]` — parallel workers
- `[PROGRESS_INTERVAL]` — status update frequency
- `[TIMEOUT]` — max duration

## Example

Set up work-stealing queue for `process 100 customer support tickets`:

Queue setup:
1. Decompose into `100` tasks (one per ticket)
2. Spawn `5` worker agents

Worker loop:
- Each worker pulls next unprocessed ticket
- Categorizes, drafts response, flags for review
- Pushes result to shared results queue

## Tips

- Work stealing balances load naturally — fast workers don't idle
- Adaptive sizing: if a worker is slow, give it simpler tasks
- Progress reporting prevents "is it stuck?" anxiety
