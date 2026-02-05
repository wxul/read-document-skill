# Read Document Skill

Claude Code skill for documentation-driven code generation.

## Installation

```bash
npx skills add wxul/read-document-skill
```

## Usage

```
/read-doc <technology> <requirement>
```

**Example:**

```
/read-doc gsap create a scroll-triggered animation
```

**Workflow:**

1. Suggest documentation URL based on the technology
2. User confirms or provides alternative URL
3. Fetch entry page, extract navigation links
4. Navigate to relevant sub-page based on requirement
5. Summarize docs and generate code

## Manual Installation

```bash
git clone https://github.com/wxul/read-document-skill.git
cp -r read-document-skill/skills/* .claude/skills/
```

## License

ISC
