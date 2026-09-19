# Semantic Output Validation

## Prompt Template

Validate [OUTPUT] meaning and correctness:

Semantic checks:
1. Factual accuracy: claims match [SOURCE_OF_TRUTH]?
2. Logical consistency: no contradictions within output?
3. Completeness: all [REQUIRED_ASPECTS] addressed?
4. Relevance: output addresses [ORIGINAL_REQUEST]?
5. Feasibility: proposed actions are actually [FEASIBLE_CHECK]?

Cross-reference checks:
- Output vs [REFERENCE_DOCUMENTS]: any conflicts?
- Output vs [CONSTRAINTS]: any violations?
- Output vs [HISTORICAL_DATA]: any anomalies?

Semantic validation is slower but catches errors structural validation misses.

## Variables

- `[OUTPUT]` — what to validate
- `[SOURCE_OF_TRUTH]` — ground truth
- `[REQUIRED_ASPECTS]` — completeness criteria
- `[ORIGINAL_REQUEST]` — what was asked
- `[FEASIBLE_CHECK]` — can it actually be done
- `[REFERENCE_DOCUMENTS]` — cross-check sources
- `[CONSTRAINTS]` — limits
- `[HISTORICAL_DATA]` — baseline

## Example

Validate `migration plan` meaning and correctness:

Semantic checks:
1. Factual accuracy: schema changes match actual DB schema?
2. Logical consistency: no contradictory migration steps?
3. Completeness: all tables, indexes, constraints addressed?
4. Relevance: plan addresses the stated migration goal?
5. Feasibility: migration can run within maintenance window?

## Tips

- Semantic validation catches "technically correct but wrong" outputs
- Cross-referencing with source of truth is essential for factual claims
- Feasibility checks prevent plans that can't actually be executed
