# Quality Review Handoff

## Prompt Template

Submit [ARTIFACT] for quality review:

Review package:
1. **Artifact**: [ARTIFACT_DESCRIPTION]
2. **Self-review completed**: [SELF_REVIEW_CHECKLIST]
3. **Test results**: [TEST_RESULTS]
4. **Known issues**: [KNOWN_ISSUES]
5. **Design decisions**: [DESIGN_DECISIONS]
6. **Review focus requested**: [FOCUS_AREAS]

Review criteria:
- [ ] Correctness: does it do what was asked?
- ] Completeness: are all requirements met?
- [ ] Quality: does it meet [QUALITY_STANDARDS]?
- [ ] Maintainability: can others understand and modify it?
- [ ] Performance: meets [PERF_REQUIREMENTS]?
- [ ] Security: passes [SECURITY_CHECKLIST]?

## Variables

- `[ARTIFACT]` — what's being reviewed
- Self-review checklist
- Test results
- Review criteria and focus areas

## Example

Submit `REST API implementation` for quality review:

Review package:
1. **Artifact**: `User management API (CRUD + search)`
2. **Self-review completed**: `All unit tests pass, lint clean`
3. **Test results**: `47 tests, 94% coverage`
4. **Known issues**: `Search endpoint slow for >10K records`
5. **Review focus requested**: `Error handling patterns, SQL injection prevention`

## Tips

- Self-review before submission saves reviewer time
- Known issues show self-awareness and honesty
- Focused review requests get better feedback than "review everything"
