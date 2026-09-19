# Task Dependency Graph Generation

## Prompt Template

Given these tasks, generate a dependency graph:

[TASK_LIST]

Output:
1. Adjacency list of dependencies
2. Topological sort (execution order)
3. Parallelizable groups (tasks with no mutual dependencies)
4. Critical path (longest dependency chain)
5. Blocked tasks and their blockers

Format as a DAG with clear execution phases.

## Variables

- `[TASK_LIST]` — numbered list of tasks with brief descriptions

## Example

Given these tasks, generate a dependency graph:

1. Design database schema
2. Create API endpoints
3. Write authentication middleware
4. Implement frontend login form
5. Write unit tests
6. Set up CI pipeline
7. Deploy to staging

## Tips

- Topological sort reveals true execution order
- Parallelizable groups are where multi-agent shines
- Critical path = minimum wall-clock time even with infinite agents
