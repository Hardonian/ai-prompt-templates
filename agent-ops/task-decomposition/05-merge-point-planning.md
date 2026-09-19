# Merge Point and Integration Planning

## Prompt Template

Plan the integration/merge points for this parallel workstream:

**Workstreams:**
[WORKSTREAM_LIST]

For each merge point:
1. What artifacts converge
2. Integration test required
3. Conflict resolution strategy
4. Rollback plan if integration fails
5. Owner of the merge

## Variables

- `[WORKSTREAM_LIST]` — parallel tracks of work

## Example

Plan the integration/merge points for this parallel workstream:

**Workstreams:**
- WS1: Backend API (agent-backend)
- WS2: Frontend UI (agent-frontend)
- WS3: Database migrations (agent-db)

## Tips

- Merge points are where parallel work most often breaks
- Defining conflict resolution strategy upfront prevents merge paralysis
- Rollback plans make merges non-scary
