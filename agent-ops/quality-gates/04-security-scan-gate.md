# Security Scan Gate

## Prompt Template

Run security scan gate on [TARGET]:

Checks:
1. Dependency vulnerabilities: [DEP_SCANNER] — block on severity ≥ [SEVERITY]
2. Secret detection: scan for [SECRET_PATTERNS] in all files
3. SAST: [SAST_TOOL] on changed code
4. Permission check: verify [RESOURCE_PERMISSIONS] are least-privilege
5. Input validation: all [INPUT_SOURCES] are sanitized
6. Output encoding: all [OUTPUT_TARGETS] are properly escaped

Output format:
- CRITICAL: must fix before proceeding
- HIGH: should fix, flag for review
- MEDIUM: note in report
- LOW: informational only

## Variables

- `[TARGET]` — what to scan
- `[DEP_SCANNER]` — e.g. `npm audit`, `pip-audit`
- `[SEVERITY]` — blocking threshold
- `[SECRET_PATTERNS]` — regex for secrets
- `[SAST_TOOL]` — static analysis tool
- `[RESOURCE_PERMISSIONS]` — what to check
- `[INPUT_SOURCES]` — user inputs, API params
- `[OUTPUT_TARGETS]` — HTML, SQL, shell

## Example

Run security scan gate on `PR #142`:

Checks:
1. Dependency vulnerabilities: `npm audit` — block on severity ≥ `high`
2. Secret detection: scan for `API_KEY, SECRET, PASSWORD, TOKEN` in all files
3. SAST: `semgrep --config=auto` on changed code
4. Permission check: verify `file permissions, DB access` are least-privilege

## Tips

- Security gates should block merges, not just warn
- Secret detection prevents the #1 cloud breach vector
- Run SAST on diffs only — full-repo scans are too slow for gates
