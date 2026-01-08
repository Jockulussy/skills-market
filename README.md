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

## Development

### Repository Structure

```
skills-market/
├── .claude-plugin/
│   └── marketplace.json       # Marketplace catalog
├── plugins/
│   └── xgate-server/
│       ├── .claude-plugin/
│       │   └── plugin.json    # Plugin manifest
│       ├── skills/
│       │   └── xgate-server.md
│       └── scripts/
│           └── xgate          # CLI tool
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
