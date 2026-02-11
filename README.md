# Headkey MCP Plugin for Claude Code

Memory layer for AI agents — store, organize, retrieve, and manage memories and beliefs via the [Headkey](https://headkey.ai) API.

## Installation

```bash
claude plugin install headkey@headkey
```

## Features

- **Memory management** — ingest, retrieve, search, and forget memories
- **Belief tracking** — assert beliefs with confidence scores, detect conflicts
- **Knowledge graph** — create entities, define relationships, query connections
- **Sensory events** — stream events into short-term memory for async processing
- **Agent management** — create and configure AI agents with custom memory strategies
- **CLAUDE.md generation** — run `/headkey:claude-md` to auto-generate memory instructions tailored to your project

## Configuration

Run `/headkey:setup` inside Claude Code for guided configuration, or configure manually:

### Account Key (Recommended)

Set your account API key **globally** in `~/.claude/settings.json`:

```json
{
  "env": {
    "HEADKEY_API_KEY": "cibfe_your_account_key_here"
  }
}
```

Set the agent ID **per-project** in `.claude/settings.json` in your project root:

```json
{
  "env": {
    "HEADKEY_AGENT_ID": "my-project-agent"
  }
}
```

The agent ID can be the agent UUID or the friendly slug from your agent configuration.

### Agent Key

If using an agent-specific key, only `HEADKEY_API_KEY` is needed (no agent ID required). Set it per-project or globally as above.

### Git Safety

Add `.claude/settings.json` to your `.gitignore` to avoid committing secrets.

## Development

Test the plugin locally:

```bash
claude --plugin-dir .
```

## License

MIT
