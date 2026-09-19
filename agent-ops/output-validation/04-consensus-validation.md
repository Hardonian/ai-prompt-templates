# Multi-Agent Consensus Validation

## Prompt Template

Validate [OUTPUT] by asking [VALIDATOR_COUNT] independent validators:

Each validator receives:
- The output to validate
- The original task/requirement
- Their specific validation focus: [VALIDATOR_FOCUS_N]

Validators vote: APPROVE / REJECT / REVISE

Consensus rules:
- Unanimous APPROVE: accept output
- Majority APPROVE: accept with noted concerns
- Majority REJECT: return for revision with aggregated feedback
- Split: escalate to [TIEBREAKER]

Feedback aggregation:
- Combine all REJECT reasons
- Prioritize by frequency (mentioned by multiple validators)
- Remove contradictory feedback
- Produce actionable revision list

## Variables

- `[OUTPUT]` — what to validate
- `[VALIDATOR_COUNT]` — e.g. `3`
- `[VALIDATOR_FOCUS_N]` — each validator's specialty
- `[TIEBREAKER]` — who decides on ties

## Example

Validate `architecture design document` by asking `3` independent validators:

Each validator receives their specific focus:
- Validator 1: `scalability and performance`
- Validator 2: `security and compliance`
- Validator 3: `maintainability and developer experience`

Consensus rules:
- Unanimous APPROVE: accept output
- Majority APPROVE: accept with noted concerns
- Majority REJECT: return for revision

## Tips

- Consensus catches blind spots that single validators miss
- Specialized focus prevents all validators looking at the same thing
- Tiebreakers prevent deadlock — designate one upfront
