# Artifact-Grounded Context

## Prompt Template

Ground agent responses in [ARTIFACTS]:

For each relevant artifact:
1. Load artifact: [ARTIFACT_PATH]
2. Extract relevant sections: [EXTRACTION_CRITERIA]
3. Pin to context with source attribution

Grounding rules:
- Never claim facts not in provided artifacts
- Cite artifact + line number for every factual claim
- If information is missing from artifacts: say "not found in provided sources"
- Prefer recent artifacts over older ones when conflicts exist

Artifact priority:
1. [PRIORITY_1_ARTIFACTS] (highest trust)
2. [PRIORITY_2_ARTIFACTS]
3. [PRIORITY_3_ARTIFACTS] (lowest trust, cross-check only)

## Variables

- `[ARTIFACTS]` — source documents
- `[ARTIFACT_PATH]` — file location
- `[EXTRACTION_CRITERIA]` — what to pull out
- `[PRIORITY_N_ARTIFACTS]` — trust hierarchy

## Example

Ground agent responses in `codebase and documentation`:

For each relevant artifact:
1. Load artifact: `src/**/*.ts`
2. Extract relevant sections: `functions related to the current task`
3. Pin to context with source attribution

Grounding rules:
- Never claim facts not in provided artifacts
- Cite `file:line` for every factual claim
- If information is missing: say "not found in provided sources"

## Tips

- Artifact grounding prevents hallucination in code agents
- Source attribution makes output verifiable
- Trust hierarchy handles conflicting sources
