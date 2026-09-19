# Structural Output Validation

## Prompt Template

Validate [OUTPUT] structure before acceptance:

Required structure:
```
[OUTPUT_SCHEMA]
```

Validation checks:
1. Type check: is output correct type ([TYPE])?
2. Required fields: are all [REQUIRED_FIELDS] present?
3. Field types: do fields match expected types?
4. Constraints: do values meet [CONSTRAINTS]?
5. Format: does output match [FORMAT_PATTERN]?

Validation report format:
```json
{
  "valid": true/false,
  "errors": [{"field": "...", "expected": "...", "actual": "..."}],
  "warnings": [{"field": "...", "message": "..."}]
}
```

## Variables

- `[OUTPUT]` — what to validate
- `[OUTPUT_SCHEMA]` — expected structure
- `[TYPE]` — expected type
- `[REQUIRED_FIELDS]` — must-have fields
- `[CONSTRAINTS]` — value limits
- `[FORMAT_PATTERN]` — regex or format spec

## Example

Validate `API response` structure before acceptance:

Required structure:
```json
{
  "status": "success|error",
  "data": {},
  "metadata": {"timestamp": "ISO8601", "request_id": "UUID"}
}
```

## Tips

- Structural validation catches malformed output before it causes downstream failures
- Separate errors (block) from warnings (flag)
- Validate early — the sooner you catch bad output, the cheaper the fix
