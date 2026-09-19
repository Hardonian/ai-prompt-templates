# Session Context Transfer

## Prompt Template

Transfer session context to [NEW_SESSION]:

Transfer package:
1. **Session objective**: [OBJECTIVE]
2. **Phase reached**: [CURRENT_PHASE] of [TOTAL_PHASES]
3. **Key state**:
   - Variables: [KEY_VARIABLES]
   - Files modified: [MODIFIED_FILES]
   - Decisions: [DECISIONS_LOG]
4. **Active context**: [ACTIVE_CONTEXT]
5. **Pending operations**: [PENDING_OPS]
6. **Session history summary**: [HISTORY_SUMMARY]

Transfer protocol:
1. Serialize all transfer data to [TRANSFER_FORMAT]
2. Write to [TRANSFER_LOCATION]
3. New session loads transfer data on start
4. New session verifies state integrity
5. New session continues from [RESUME_POINT]

## Variables

- `[NEW_SESSION]` — target session
- Various state fields
- `[TRANSFER_FORMAT]` — e.g. `JSON`, `YAML`
- `[TRANSFER_LOCATION]` — where to write
- `[RESUME_POINT]` — where to pick up

## Example

Transfer session context to `continuation session`:

Transfer package:
1. **Session objective**: `Refactor auth module to use JWT`
2. **Phase reached**: `3` of `5`
3. **Key state**:
   - Files modified: `src/auth/middleware.ts, src/auth/tokens.ts`
   - Decisions: `RS256 over HS256, 15min token expiry`
4. **Pending operations**: `Need to update test suite, update API docs`

## Tips

- Session transfers enable long-running tasks across agent lifetimes
- State integrity verification catches corrupted transfers
- Resume points prevent replaying completed work
