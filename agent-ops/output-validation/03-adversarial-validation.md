# Adversarial Output Validation

## Prompt Template

Validate [OUTPUT] by trying to break it:

Adversarial tests:
1. Edge cases: feed [EDGE_CASE_INPUTS] — does output handle them?
2. Boundary values: test [BOUNDARY_VALUES] — any overflow/underflow?
3. Malformed input: inject [MALFORMED_INPUTS] — any crashes/injections?
4. Stress test: [STRESS_CONDITIONS] — does it degrade gracefully?
5. Contradiction test: does output survive [CONTRADICTIONS]?

Attack vectors:
- [ATTACK_VECTOR_1]: try to make output [UNDESIRED_BEHAVIOR_1]
- [ATTACK_VECTOR_2]: try to make output [UNDESIRED_BEHAVIOR_2]

Pass criteria: output remains correct, safe, and useful under all adversarial conditions.

## Variables

- `[OUTPUT]` — what to attack
- `[EDGE_CASE_INPUTS]` — unusual inputs
- `[BOUNDARY_VALUES]` — min/max values
- `[MALFORMED_INPUTS]` — bad data
- `[STRESS_CONDITIONS]` — high load
- `[CONTRADICTIONS]` — conflicting requirements
- Attack vectors and undesired behaviors

## Example

Validate `SQL query builder output` by trying to break it:

Adversarial tests:
1. Edge cases: feed `empty strings, NULL, Unicode` — does output handle them?
2. Boundary values: test `max integer, empty arrays` — any overflow?
3. Malformed input: inject `'; DROP TABLE users;--` — any SQL injection?
4. Stress test: `1000 concurrent queries` — does it degrade gracefully?

## Tips

- Adversarial validation finds bugs that happy-path testing misses
- Security-critical outputs MUST undergo adversarial testing
- Document discovered attack vectors for future prevention
