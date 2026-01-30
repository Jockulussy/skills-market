# Skills Market Guidelines

## Goals

1. **Build paid agents** — Every skill should help create monetizable Lucid Agents
2. **Be concise** — Only include what agents don't already know
3. **No repetition** — Don't explain CLI basics, common patterns, or standard tooling
4. **Composable** — Skills should work standalone or together
5. **Real data only** — No hardcoded mocks; agents must fetch live data

## Skill Requirements

### Must Have
- YAML frontmatter with `name` and `description`
- `.claude-plugin/plugin.json` manifest
- Focus on Lucid Agents ecosystem (x402, ERC-8004)
- Zod v4 for schemas (not v3)
- Modern imports: `@lucid-agents/core`, `@lucid-agents/http`, etc.

### Must NOT Have
- CLI usage basics (`curl`, `git`, `npm` commands everyone knows)
- Obvious programming patterns
- Verbose explanations of common concepts
- Hardcoded/mock data examples
- Outdated SDK patterns (monolithic imports, `agent.listen()`)

## Quality Bar

```
❌ Bad:  "Run `npm install` to install dependencies"
✅ Good: "Requires: Zod v4, @lucid-agents/payments"

❌ Bad:  50 lines explaining how fetch() works
✅ Good: API endpoint table with tested URLs

❌ Bad:  Generic TypeScript patterns
✅ Good: Lucid-specific: addEntrypoint, paymentsFromEnv, price config
```

## PR Review Criteria

- [ ] Has required files (plugin.json, SKILL.md)
- [ ] YAML frontmatter present
- [ ] Uses Zod v4, modern SDK imports
- [ ] No bloat (CLI basics, obvious patterns)
- [ ] Adds value for paid agent creation

## Structure

```
plugins/<skill-name>/
├── .claude-plugin/plugin.json
└── skills/SKILL.md
```
