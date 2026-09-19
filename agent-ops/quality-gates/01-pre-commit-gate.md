# Pre-Commit Quality Gate

## Prompt Template

Run this quality gate before any commit:

Gate checklist:
- [ ] [LINT_CHECK] passes with 0 errors
- [ ] [TYPE_CHECK] passes with 0 errors
- [ ] All [TEST_SUITE] tests pass
- [ ] No [SECURITY_PATTERNS] in changed files
- [ ] Code coverage ≥ [COVERAGE_THRESHOLD]% for changed files
- [ ] [CUSTOM_CHECKS]

If any gate fails:
1. Report which gates failed with specific errors
2. Auto-fix what's safe (formatting, imports)
3. Flag what needs human review
4. Do NOT commit if critical gates fail

## Variables

- `[LINT_CHECK]` — e.g. `eslint`, `ruff`
- `[TYPE_CHECK]` — e.g. `tsc --noEmit`, `mypy`
- `[TEST_SUITE]` — test command
- `[SECURITY_PATTERNS]` — e.g. `hardcoded secrets, eval()`
- `[COVERAGE_THRESHOLD]` — minimum %
- `[CUSTOM_CHECKS]` — project-specific gates

## Example

Run this quality gate before any commit:

Gate checklist:
- [ ] `ruff check` passes with 0 errors
- [ ] `mypy src/` passes with 0 errors
- [ ] All `pytest` tests pass
- [ ] No `hardcoded secrets, eval(), exec()` in changed files
- [ ] Code coverage ≥ 80% for changed files
- [ ] `CHANGELOG.md` updated if user-facing change

## Tips

- Auto-fix safe issues (formatting) before flagging for review
- Never auto-fix logic or security issues — always escalate
- Gate severity: critical (block), warning (flag), info (note)
