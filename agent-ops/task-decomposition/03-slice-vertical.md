# Vertical Slice Decomposition

## Prompt Template

Decompose [FEATURE] into vertical slices that each deliver user value.

Each slice must be:
- Independently deployable
- Testable end-to-end
- Small enough for [SLICE_SIZE]

Format per slice:
```
Slice N: [name]
  User story: As a [user], I can [action] so that [benefit]
  Frontend: [components]
  Backend: [endpoints]
  Database: [changes]
  Tests: [test scenarios]
  Estimated effort: [hours]
```

Order slices by [PRIORITY_CRITERIA].

## Variables

- `[FEATURE]` — feature to decompose
- `[SLICE_SIZE]` — max effort per slice (e.g. `4 hours`)
- `[PRIORITY_CRITERIA]` — `risk`, `value`, `dependencies`

## Example

Decompose `user profile management` into vertical slices that each deliver user value.

Each slice must be:
- Independently deployable
- Testable end-to-end
- Small enough for `half a day`

Order slices by `highest user value first`.

## Tips

- Vertical slices > horizontal layers for agent work — each slice is a completable unit
- Forces thinking about end-to-end flow, not just "do the DB part"
- Enables incremental delivery and early feedback
