# Output Schema Validation Gate

## Prompt Template

Validate agent output against this schema before accepting:

```json
{
  "type": "object",
  "required": [REQUIRED_FIELDS],
  "properties": {
    [SCHEMA_PROPERTIES]
  },
  "additionalProperties": false
}
```

Validation steps:
1. Parse output as JSON/YAML
2. Validate against schema
3. Check field-level constraints (lengths, enums, formats)
4. Verify semantic correctness (e.g. file paths exist, URLs reachable)
5. Return validation report: pass/fail per field

## Variables

- `[REQUIRED_FIELDS]` — must-have fields
- `[SCHEMA_PROPERTIES]` — field definitions with types and constraints

## Example

Validate agent output against this schema before accepting:

```json
{
  "type": "object",
  "required": ["summary", "files_changed", "tests_added"],
  "properties": {
    "summary": {"type": "string", "maxLength": 500},
    "files_changed": {"type": "array", "items": {"type": "string"}},
    "tests_added": {"type": "integer", "minimum": 0},
    "breaking_changes": {"type": "boolean", "default": false}
  }
}
```

## Tips

- Schema validation catches malformed agent output before it propagates
- Semantic validation (do paths exist?) catches hallucinated outputs
- Use JSON Schema for structured outputs, regex for free-form
