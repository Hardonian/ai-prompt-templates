# Coding & Development Prompt Templates

## Code Review
```
Review this code for:
1. Bugs and logic errors
2. Security vulnerabilities
3. Performance issues
4. Code style and readability
5. Missing error handling
6. Edge cases not covered

Language: [LANGUAGE]
Context: [WHAT THE CODE DOES]

Code:
```[CODE]```

Provide specific line-by-line feedback with suggested fixes.
```

---

## Bug Diagnosis
```
I'm getting this error:
```
[PASTE ERROR]
```

Context:
- Language/framework: [LANGUAGE/FRAMEWORK]
- What I expected: [EXPECTED BEHAVIOR]
- What actually happened: [ACTUAL BEHAVIOR]
- Steps to reproduce: [STEPS]
- What I've already tried: [ATTEMPTS]

Relevant code:
```[CODE]```

Diagnose the root cause and provide a fix. Explain why the error occurred.
```

---

## Architecture Design
```
Design the architecture for [APPLICATION] with these requirements:

Functional:
- [REQUIREMENT 1]
- [REQUIREMENT 2]
- [REQUIREMENT 3]

Non-functional:
- Expected users: [NUMBER]
- Latency target: [MS]
- Availability: [PERCENTAGE]
- Data volume: [SIZE]

Constraints:
- Budget: [AMOUNT]
- Team size: [NUMBER]
- Timeline: [WEEKS]

Provide:
1. High-level architecture diagram (text description)
2. Technology stack recommendation
3. Database schema (key entities)
4. API design (main endpoints)
5. Deployment strategy
6. Scaling considerations
```

---

## API Documentation Generator
```
Generate API documentation for this endpoint:

Method: [GET/POST/PUT/DELETE]
Path: [ENDPOINT PATH]
Purpose: [WHAT IT DOES]

Request body (if applicable):
```[JSON]```

Response:
```[JSON]```

Include:
1. Description
2. Authentication requirements
3. Request parameters/body schema
4. Response schema with field descriptions
5. Error codes and messages
6. Example curl command
7. Example response
```

---

## Test Case Builder
```
Generate comprehensive test cases for this function:

```[CODE]```

Include:
1. Happy path tests
2. Edge cases (empty input, null, boundary values)
3. Error cases (invalid input, exceptions)
4. Performance considerations

Testing framework: [JEST/PYTEST/JUNIT/ETC]
Output format: Ready-to-run test code.
```

---

## Refactoring Prompt
```
Refactor this code to improve:
- Readability
- Performance
- Maintainability
- Testability

Constraints:
- Don't change the public API
- Keep backward compatibility
- Add type hints/annotations

Code:
```[CODE]```

Explain each change and why it's an improvement.
```

---

## Debugging Workflow
```
I'm debugging [ISSUE DESCRIPTION] in [LANGUAGE/FRAMEWORK].

Symptoms:
- [SYMPTOM 1]
- [SYMPTOM 2]

Environment:
- OS: [OS]
- Version: [VERSION]
- Dependencies: [LIST]

Guide me through a systematic debugging process:
1. What to check first
2. What logs/metrics to examine
3. Common causes for this type of issue
4. Diagnostic commands to run
5. How to verify the fix
```

---

## Code Explanation
```
Explain this code in detail:

```[CODE]```

For each section:
1. What it does (plain English)
2. Why it's done that way
3. Potential gotchas
4. How it fits in the larger system

Audience: [junior developer / senior developer / non-technical stakeholder]
```
