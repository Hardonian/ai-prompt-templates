# Troubleshooting — AI Prompt Templates

## Common Issues

### Template Produces Generic Output

**Cause:** Variables not replaced or too vague.

**Fix:**
- Replace ALL `[BRACKETED]` variables with specific details
- Add concrete numbers, names, and constraints
- Include examples of desired output format

### AI Ignores Template Structure

**Cause:** Model doesn't follow complex instructions well.

**Fix:**
- Try a more capable model (GPT-4, Claude Opus)
- Simplify the template — break into smaller steps
- Add explicit formatting instructions

### Output Too Short/Long

**Cause:** No length constraints specified.

**Fix:**
- Add "Write 500 words" or "Keep under 200 words"
- Specify "3-5 bullet points" or "10 sentences"
- Use "Be concise" or "Be thorough"

### Wrong Tone or Style

**Cause:** No tone specification in template.

**Fix:**
- Add "Write in professional/formal/casual tone"
- Specify "Use simple language" or "Use technical jargon"
- Include "Target audience: [specific group]"

### Variables Not Working

**Cause:** Brackets not recognized or format incorrect.

**Fix:**
- Use `[SQUARE_BRACKETS]` not (parentheses) or {curly braces}
- Replace the entire bracket including the text inside
- Check for typos in variable names

### Template Works in ChatGPT but Not Claude (or Vice Versa)

**Cause:** Different models handle instructions differently.

**Fix:**
- Simplify complex instructions
- Add more explicit step-by-step guidance
- Test with the specific model you'll use

### Can't Find the Right Template

**Cause:** Looking in wrong category or template doesn't exist yet.

**Fix:**
- Browse all categories — templates may be in unexpected places
- Combine multiple templates for complex tasks
- Modify existing templates to fit your needs

## Platform-Specific Issues

### ChatGPT

- Use GPT-4 or GPT-4o for best results with complex templates
- Avoid very long prompts — break into conversation turns
- Use "Continue" if output is truncated

### Claude

- Claude handles long prompts well — don't worry about length
- Use XML tags for complex structures: `<instructions>...</instructions>`
- Specify "Think step-by-step" for reasoning tasks

### Gemini

- Gemini works best with clear, structured instructions
- Use numbered lists for multi-step tasks
- Avoid ambiguous pronouns

### Local LLMs (Llama, Mistral, Qwen)

- Simpler templates work better with smaller models
- Add more explicit instructions
- Use few-shot examples for consistent output

## Still Stuck?

- Check the [FAQ](faq.md)
- Open a [GitHub Issue](https://github.com/Hardonian/ai-prompt-templates/issues)
- Visit [aiautomatedsystems.ca](https://aiautomatedsystems.ca) for support
