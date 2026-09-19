# Human-in-the-Loop Review Gate

## Prompt Template

This change requires human review before proceeding.

Prepare review package:
1. Summary of changes (≤[SUMMARY_LENGTH] words)
2. Risk assessment: [RISK_LEVEL] — justification
3. Files changed with line-level annotations
4. Test results and coverage delta
5. Recommended reviewer: [REVIEWER_CRITERIA]
6. Suggested review focus areas: [FOCUS_AREAS]

Block criteria (auto-escalate to human):
- [AUTO_BLOCK_CONDITIONS]

Auto-approve criteria (skip human review):
- [AUTO_APPROVE_CONDITIONS]

## Variables

- `[SUMMARY_LENGTH]` — e.g. `200`
- `[RISK_LEVEL]` — `low/medium/high/critical`
- `[REVIEWER_CRITERIA]` — who should review
- `[FOCUS_AREAS]` — what to look at
- `[AUTO_BLOCK_CONDITIONS]` — always need human
- `[AUTO_APPROVE_CONDITIONS]` — safe to auto-approve

## Example

This change requires human review before proceeding.

Block criteria (auto-escalate to human):
- Changes to auth/payment/infra code
- >500 lines changed
- Security scan findings

Auto-approve criteria (skip human review):
- Documentation-only changes
- Dependency version bumps with green CI
- Formatting/lint fixes

## Tips

- Not everything needs human review — define clear auto-approve paths
- Good summaries reduce review time by 80%
- Focus areas prevent rubber-stamp reviews
