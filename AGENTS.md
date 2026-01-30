# Skills Market Guidelines

Skills for building paid Lucid Agents with x402.

## Skill Format

Every skill needs `SKILL.md` with YAML frontmatter and markdown instructions:

```yaml
---
name: my-skill
description: What this does. Use when [trigger conditions].
---

Instructions Claude follows when invoked...
```

- `name` → becomes `/slash-command`
- `description` → helps Claude decide when to auto-load

## Frontmatter Reference

| Field | Description |
|:------|:------------|
| `name` | Lowercase, hyphens only (max 64 chars). Default: directory name |
| `description` | What it does and when to use it |
| `disable-model-invocation` | `true` = only user can invoke |
| `user-invocable` | `false` = hidden from / menu |
| `allowed-tools` | Tools Claude can use without asking |
| `context` | `fork` to run in subagent |
| `agent` | Subagent type when `context: fork` |

## Structure

```
plugins/<skill-name>/
├── .claude-plugin/plugin.json
└── skills/
    ├── SKILL.md          # Required - main instructions
    ├── template.md       # Optional - templates
    ├── examples/         # Optional - example outputs
    └── scripts/          # Optional - executable scripts
```

Keep SKILL.md under 500 lines. Move detailed reference to separate files.

## Dynamic Context

Use `!`command`` to inject live data:

```yaml
---
name: pr-summary
context: fork
---
PR diff: !`gh pr diff`
Changed files: !`gh pr diff --name-only`

Summarize this pull request...
```

Commands run before Claude sees the prompt.

## Arguments

Use `$ARGUMENTS` or `$0`, `$1`, etc:

```yaml
---
name: fix-issue
---
Fix GitHub issue $ARGUMENTS following our standards.
```

`/fix-issue 123` → "Fix GitHub issue 123..."

---

## Market-Specific Goals

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
```

## Must Have

- YAML frontmatter with `name` and `description`
- Focus on Lucid Agents (x402, ERC-8004)
- Zod v4 (not v3)
- Modern imports: `@lucid-agents/core`, `@lucid-agents/http`

## Must NOT Have

- CLI basics everyone knows
- Verbose explanations of common concepts
- Hardcoded/mock data
- Outdated SDK patterns (`agent.listen()`, monolithic imports)

## PR Review Criteria

- [ ] Has SKILL.md with frontmatter
- [ ] Has plugin.json manifest
- [ ] Uses Zod v4, modern SDK imports
- [ ] No bloat
- [ ] Adds value for paid agent creation

## Troubleshooting

| Problem | Fix |
|:--------|:----|
| Skill not triggering | Make description match natural phrases; check `/context` |
| Triggers too often | Make description more specific; add `disable-model-invocation: true` |
| Claude doesn't see skill | Too many skills exceed 15K char budget; increase `SLASH_COMMAND_TOOL_CHAR_BUDGET` |

## Reference

- [Agent Skills Standard](https://agentskills.io)
- [Claude Code Docs](https://code.claude.com/docs/llms.txt)
