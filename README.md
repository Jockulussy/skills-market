# Daydreams AI Skills Marketplace

A Claude Code plugin marketplace for working with Daydreams AI infrastructure.

## Installation

Add this marketplace to Claude Code:

```bash
/plugin marketplace add daydreamsai/skills-market
```

Then install the plugins you want:

```bash
/plugin install xgate-server@daydreams-skills
/plugin install lucid-agents-sdk@daydreams-skills
/plugin install lucid-client-api@daydreams-skills
```

## Available Plugins

### xgate-server

Query the xgate-server API for X402 services, ERC-8004 agents, and on-chain token transfers.

**Features:**
- Search services by query, network, and asset
- Search agents by protocol (MCP, A2A), reputation score, and validation status
- Query on-chain token transfers
- CLI tool for quick API access

**Usage:**
```bash
# After installing, use the skill
/xgate-server

# Or use the CLI directly
xgate health
xgate services -q "token" -n ethereum
xgate agents -p MCP --min-score 0.8
xgate transfers -c 8453 --totals
```

**Environment:**
```bash
export XGATE_URL=https://xgate.run  # or http://localhost:9000
```

### lucid-agents-sdk

Comprehensive skill for working with the Lucid Agents SDK - a TypeScript framework for building and monetizing AI agents.

**Features:**
- Building agents with extensions (http, payments, identity, a2a, etc.)
- Using adapters (Hono, Express, TanStack)
- Payment networks (EVM and Solana)
- Code structure principles
- Common development tasks and patterns

**Usage:**
Automatically activates when:
- Building or modifying Lucid Agents projects
- Working with agent entrypoints, payments, identity, or A2A communication
- Developing in the lucid-agents monorepo
- Questions about the Lucid Agents architecture

**Resources:**
- [Lucid Agents Repository](https://github.com/daydreamsai/lucid-agents)
- [AGENTS.md Guide](https://github.com/daydreamsai/lucid-agents/blob/master/AGENTS.md)
- [ERC-8004 Specification](https://eips.ethereum.org/EIPS/eip-8004)
- [x402 Protocol](https://github.com/paywithx402)

### lucid-client-api

Skill for interacting with the Lucid Client API - a multi-agent runtime system.

**Features:**
- Agent management endpoints (create, update, delete, list)
- Entrypoint invocation with payment handling
- Payment handling (x402 protocol)
- Secrets management
- Analytics and rankings
- OpenAPI documentation access

**Usage:**
Automatically activates when:
- Interacting with the Lucid Client API
- Managing agents programmatically
- Invoking agent entrypoints
- Working with the multi-agent runtime

**Resources:**
- [Lucid Client Repository](https://github.com/daydreamsai/lucid-client)
- [API Documentation](https://github.com/daydreamsai/lucid-client/blob/master/AGENTS.md)

## Development

### Repository Structure

```
skills-market/
├── .claude-plugin/
│   └── marketplace.json          # Marketplace catalog
├── plugins/
│   ├── xgate-server/
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json       # Plugin manifest
│   │   ├── skills/
│   │   │   └── xgate-server.md
│   │   └── scripts/
│   │       └── xgate             # CLI tool
│   ├── lucid-agents-sdk/
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json
│   │   └── skills/
│   │       └── SKILL.md
│   └── lucid-client-api/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       └── skills/
│           └── SKILL.md
└── README.md
```

### Adding New Plugins

1. Create a new directory under `plugins/`
2. Add `.claude-plugin/plugin.json` with the plugin manifest
3. Add skills, commands, or other plugin components
4. Update `.claude-plugin/marketplace.json` to include the new plugin

### Testing Locally

```bash
# Add marketplace from local path
/plugin marketplace add ./path/to/skills-market

# Install a plugin
/plugin install xgate-server@daydreams-skills

# Validate marketplace
/plugin validate .
```

## License

MIT
