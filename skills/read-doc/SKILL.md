---
name: read-doc
description: Pre-step for code generation. Fetch official documentation and create a technical reference summary. Trigger when user mentions a specific technology/library/framework and wants to generate or modify code.
allowed-tools: WebFetch
---

# Documentation Reference Generator

This is a **pre-step** for code generation. Fetch documentation and produce a technical reference summary that will be used for subsequent code generation.

## Trigger

When user requests to generate or modify code using a specific technology/library/framework.

## Workflow

### Step 1: Confirm Documentation URL

Based on the technology name, suggest the official documentation URL.

Ask user with options:

> I'll fetch documentation from: `[url]`
>
> - **Yes** - proceed with this URL
> - **Use different URL** - provide an alternative URL
> - **Ignore** - skip this step, proceed without documentation reference

If user selects **Ignore**, skip this skill entirely and proceed to code generation using existing knowledge.

Only ask once per technology in a session.

### Step 2: Fetch Documentation

Use WebFetch to retrieve the entry page. Extract:
- Navigation links (sidebar, table of contents)
- Link titles and URLs

### Step 3: Navigate to Relevant Page

Based on user's code requirement, match keywords with link titles and fetch the specific sub-page(s) that are most relevant.

### Step 4: Generate Technical Reference Summary

Extract and summarize from the documentation:
- Relevant API signatures and parameters
- Usage patterns and examples
- Best practices and recommendations
- Common pitfalls to avoid

### Step 5: Output

Produce a technical reference summary:

```markdown
## Technical Reference: [technology]

### Source
- [documentation URL]

### Relevant APIs
[API signatures, parameters, return types]

### Usage Patterns
[Code examples from docs]

### Best Practices
[Recommendations from docs]

### Notes
[Important caveats or version-specific info]
```

This summary will be used as reference for the subsequent code generation step.
