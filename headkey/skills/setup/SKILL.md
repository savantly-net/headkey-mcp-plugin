---
name: setup
description: This skill should be used when the user asks to "set up headkey", "configure headkey", "connect to headkey", mentions "HEADKEY_API_KEY", or discusses headkey configuration, authentication setup, or per-project agent configuration.
version: 1.0.0
---

# Headkey Setup Skill

This skill helps users configure their connection to the Headkey Memory API.

## When This Skill Applies

- User wants to set up or configure the Headkey plugin
- User needs help with API key configuration
- User is troubleshooting connection issues
- User wants to configure a different Headkey agent per project

## Key Concept

Each Headkey API key is associated with a specific agent. To use different agents in different projects, set the API key at the project level rather than globally.

## Configuration

### Project-Level (Recommended for multi-project setups)

Add to `.claude/settings.json` in the project root:

```json
{
  "env": {
    "HEADKEY_API_KEY": "cibfe_your_key_here"
  }
}
```

Make sure `.claude/settings.json` is in `.gitignore` to avoid committing secrets.

Project-level settings override global settings, so you can have a default global key and override it per project.

### Global

Add to `~/.claude/settings.json`:

```json
{
  "env": {
    "HEADKEY_API_KEY": "cibfe_your_key_here"
  }
}
```

## Setup Command

Users can run `/headkey:setup` for a guided walkthrough that handles scope selection, key configuration, and `.gitignore` setup.

## Verification

After configuration, restart Claude Code and verify the Headkey MCP tools are available. If the connection fails, check:

1. The API key is valid and not expired
2. Network connectivity to https://www.headkey.ai
3. Project-level settings aren't being overridden unexpectedly
