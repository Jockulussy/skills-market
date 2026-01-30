# Skills Market Guidelines

Skills for building paid Lucid Agents with x402.

## Skill Format

Every skill needs a `SKILL.md` with:

1. **YAML frontmatter** (between `---` markers) — name and description
2. **Markdown content** — instructions Claude follows when invoked

```yaml
---
name: my-skill
description: One-line description. Use when [trigger conditions].
---

Instructions go here...
```

The `name` becomes the `/slash-command`. The `description` helps Claude decide when to load it automatically.

## Structure

```
plugins/<skill-name>/
├── .claude-plugin/plugin.json    # Plugin manifest
└── skills/SKILL.md               # Skill instructions
```

## Goals

1. **Build paid agents** — Every skill helps create monetizable Lucid Agents
2. **Be concise** — Only include what agents don't already know
3. **No repetition** — Don't explain CLI basics or common patterns
4. **Composable** — Skills work standalone or together
5. **Real data only** — No hardcoded mocks

## Quality Bar

```
❌ Bad:  "Run `npm install` to install dependencies"
✅ Good: "Requires: Zod v4, @lucid-agents/payments"

❌ Bad:  50 lines explaining how fetch() works
✅ Good: API endpoint table with tested URLs

❌ Bad:  Generic TypeScript patterns
✅ Good: Lucid-specific: addEntrypoint, paymentsFromEnv, price config
```

## Must Have
- YAML frontmatter with `name` and `description`
- Focus on Lucid Agents ecosystem (x402, ERC-8004)
- Zod v4 for schemas (not v3)
- Modern imports: `@lucid-agents/core`, `@lucid-agents/http`, etc.

## Must NOT Have
- CLI usage basics everyone knows
- Verbose explanations of common concepts
- Hardcoded/mock data examples
- Outdated SDK patterns

## PR Review

PRs are auto-reviewed against:
- [ ] Has SKILL.md with frontmatter
- [ ] Has plugin.json manifest
- [ ] Uses Zod v4, modern SDK imports
- [ ] No bloat
- [ ] Adds value for paid agent creation

## Reference

[Agent Skills Standard](https://agentskills.io) | [Claude Code Docs](https://code.claude.com/docs/llms.txt)
