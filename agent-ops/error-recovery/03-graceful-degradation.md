# Graceful Degradation Pattern

## Prompt Template

[PRIMARY_ACTION] failed. Execute degradation cascade:

Level 1 (Full capability): [PRIMARY_ACTION]
  ↓ if failed
Level 2 (Reduced capability): [DEGRADED_ACTION_1]
  ↓ if failed
Level 3 (Minimal capability): [DEGRADED_ACTION_2]
  ↓ if failed
Level 4 (Safe mode): [SAFE_MODE_ACTION]

At each level:
- Log what capability was lost
- Notify user of degraded state
- Continue with available functionality
- Track degradation for post-mortem

## Variables

- `[PRIMARY_ACTION]` — ideal path
- `[DEGRADED_ACTION_1]` — slightly worse
- `[DEGRADED_ACTION_2]` — significantly worse
- `[SAFE_MODE_ACTION]` — bare minimum safe operation

## Example

`Full code analysis with type checking` failed. Execute degradation cascade:

Level 1 (Full capability): `mypy + ruff + pytest --cov`
  ↓ if failed
Level 2 (Reduced capability): `ruff + pytest` (skip type checking)
  ↓ if failed
Level 3 (Minimal capability): `ruff check` (lint only)
  ↓ if failed
Level 4 (Safe mode): `python -c "import ast; ast.parse(open('src/main.py').read())"` (syntax only)

## Tips

- Degradation > total failure — always deliver something
- Each level should be independently useful
- Track degradation frequency to prioritize fixing flaky levels
