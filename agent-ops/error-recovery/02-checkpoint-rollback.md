# Checkpoint and Rollback Recovery

## Prompt Template

Before executing [RISKY_OPERATION]:

**Checkpoint:**
1. Save state: [STATE_SNAPSHOT_COMMAND]
2. Record checkpoint ID: [CHECKPOINT_ID]
3. Verify checkpoint integrity: [VERIFY_COMMAND]

**Execute operation:**
[RISKY_OPERATION]

**On failure:**
1. Detect failure: [FAILURE_DETECTION]
2. Stop all further operations
3. Restore from checkpoint: [ROLLBACK_COMMAND]
4. Verify restoration: [VERIFY_COMMAND]
5. Report: what failed, what was rolled back, what state we're in

## Variables

- `[RISKY_OPERATION]` — what to attempt
- `[STATE_SNAPSHOT_COMMAND]` — how to save state
- `[CHECKPOINT_ID]` — identifier
- `[VERIFY_COMMAND]` — integrity check
- `[FAILURE_DETECTION]` — how to know it failed
- `[ROLLBACK_COMMAND]` — how to restore

## Example

Before executing `database migration: add users.avatar_url column`:

**Checkpoint:**
1. Save state: `pg_dump mydb > /tmp/checkpoint_$(date +%s).sql`
2. Record checkpoint ID: `checkpoint_20240115_1430`
3. Verify restoration: `psql mydb < /tmp/checkpoint_20240115_1430.sql && echo OK`

**On failure:**
1. Detect failure: `migration script exits non-zero`
2. Restore: `psql mydb < /tmp/checkpoint_20240115_1430.sql`

## Tips

- Checkpoint before anything destructive — migrations, deploys, bulk edits
- Verify checkpoint is restorable BEFORE proceeding (test the backup)
- DB checkpoints are cheap insurance; code checkpoints = git stash/branch
