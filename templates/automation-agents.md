# Automation & Agent Prompt Templates

## Agent Role Definition
```
You are [ROLE NAME], a specialized AI assistant for [DOMAIN].

Your capabilities:
- [CAPABILITY 1]
- [CAPABILITY 2]
- [CAPABILITY 3]

Your constraints:
- Never [BOUNDARY 1]
- Always [RULE 1]
- When uncertain, [BEHAVIOR]

Your workflow:
1. [STEP 1]
2. [STEP 2]
3. [STEP 3]

Output format: [STRUCTURED/DATA/CONVERSATIONAL]
Tone: [PROFESSIONAL/CASUAL/TECHNICAL]
```

---

## Chain-of-Thought Template
```
Solve this step-by-step:

[PROBLEM]

Before answering:
1. Identify what information is given
2. Identify what's being asked
3. List any assumptions
4. Work through the solution step-by-step
5. Verify your answer makes sense
6. State your confidence level

Show your reasoning at each step.
```

---

## Few-Shot Example Template
```
I need you to [TASK]. Here are examples:

Input: [EXAMPLE 1 INPUT]
Output: [EXAMPLE 1 OUTPUT]

Input: [EXAMPLE 2 INPUT]
Output: [EXAMPLE 2 OUTPUT]

Input: [EXAMPLE 3 INPUT]
Output: [EXAMPLE 3 OUTPUT]

Now process this:
Input: [ACTUAL INPUT]
Output:
```

---

## System Prompt Template
```
SYSTEM PROMPT FOR [APPLICATION NAME]:

Role: You are [ROLE DESCRIPTION].
Purpose: [WHAT YOU DO].
Users: [WHO YOU HELP].

Rules:
1. [RULE 1]
2. [RULE 2]
3. [RULE 3]

Capabilities:
- [CAPABILITY 1]
- [CAPABILITY 2]

Limitations:
- [LIMITATION 1]
- [LIMITATION 2]

When you don't know: [BEHAVIOR]
When you're unsure: [BEHAVIOR]
Output format: [FORMAT]
```

---

## Tool-Use Pattern
```
You have access to these tools:

1. [TOOL NAME]: [DESCRIPTION]
   - Input: [FORMAT]
   - Output: [FORMAT]
   - Use when: [CONDITION]

2. [TOOL NAME]: [DESCRIPTION]
   - Input: [FORMAT]
   - Output: [FORMAT]
   - Use when: [CONDITION]

When you need information:
1. Determine which tool to use
2. Call the tool with correct parameters
3. Process the result
4. Continue or call another tool
5. Provide final answer

Always explain which tool you're using and why.
```

---

## Error Handling Prompt
```
When processing [TASK], handle these error cases:

Error 1: [CONDITION]
→ Response: [WHAT TO SAY]
→ Action: [WHAT TO DO]

Error 2: [CONDITION]
→ Response: [WHAT TO SAY]
→ Action: [WHAT TO DO]

Error 3: [CONDITION]
→ Response: [WHAT TO SAY]
→ Action: [WHAT TO DO]

If an unexpected error occurs:
→ Log the error details
→ Provide a user-friendly message
→ Suggest next steps
→ Offer to retry or escalate
```

---

## Output Format Spec
```
Format your response as [FORMAT TYPE]:

[JSON/TABLE/MARKDOWN/STRUCTURED TEXT]

Required fields:
- [FIELD 1]: [TYPE] — [DESCRIPTION]
- [FIELD 2]: [TYPE] — [DESCRIPTION]
- [FIELD 3]: [TYPE] — [DESCRIPTION]

Example output:
```[EXAMPLE]```

Validation rules:
- [FIELD 1] must be [CONSTRAINT]
- [FIELD 2] must be [CONSTRAINT]
```
