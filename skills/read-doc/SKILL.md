---
name: read-doc
description: Fetch documentation from URL and use it to generate accurate code. Use when user wants to generate code based on official documentation.
---

# Documentation-Driven Code Generation

Fetch documentation, summarize key information, and generate code based on official docs.

## Input

`<technology> <requirement>`

## Workflow

### Step 1: Confirm Documentation URL

Based on the technology name, suggest the official documentation URL.

Ask user to confirm:

> I'll use documentation from: `[url]`
>
> Is this correct, or provide a different URL?

Only ask once per technology in a session.

### Step 2: Fetch Documentation

Use WebFetch to retrieve the entry page. Extract:
- Navigation links (sidebar, table of contents)
- Link titles and URLs

### Step 3: Navigate to Relevant Page

Match user's requirement keywords with link titles, then fetch the specific sub-page.

### Step 4: Summarize and Generate

From the documentation, extract:
- API signatures and parameters
- Usage examples
- Best practices

Generate code following official patterns.

### Step 5: Output

```markdown
## Documentation
- Source: [url]

## Summary
[Key API info from docs]

## Code
[Generated code]

## Notes
[Important details from docs]
```
