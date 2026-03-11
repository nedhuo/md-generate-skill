# md-generate-skill

A skill for AI assistants that enforces readable, well-structured Markdown output.

## What it does

Constrains AI Markdown generation with concrete rules covering:

- Heading hierarchy (no skipped levels, one H1 per doc)
- Bold/italic usage (emphasis only, not decoration)
- List vs prose decision logic
- Code block language tags (always required)
- Table usage criteria
- Visual spacing and rhythm
- Forbidden filler phrases and redundant closers
- Scene-specific templates: technical notes, project docs, tutorials, meeting notes

## Usage

### OpenCode / Kiro

Add to your project's `.kiro/skills/` directory, or load remotely:

```yaml
# .kiro/skills/md-generate.md (remote reference)
url: https://raw.githubusercontent.com/nedhuo/md-generate-skill/main/skill.md
```

Or reference directly in a prompt:

```
Load skill from: https://raw.githubusercontent.com/nedhuo/md-generate-skill/main/skill.md

Now generate a technical note about React Server Components.
```

### Any AI assistant

Paste the contents of `skill.md` at the top of your prompt before asking the AI to generate Markdown.

## File structure

```
md-generate-skill/
  skill.md          # The skill rules (load this)
  README.md         # This file
  examples/
    good.md         # Well-formatted output examples
    bad.md          # Common anti-patterns to avoid
```

## License

MIT
