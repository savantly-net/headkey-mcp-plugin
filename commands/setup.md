---
description: Configure Headkey API connection (set API key for this project or globally)
allowed-tools: [Bash, Read, Write, Edit, AskUserQuestion]
---

# Headkey Setup

Help the user configure their Headkey API connection.

## Steps

1. Check if `HEADKEY_API_KEY` is already set:
   - Run `echo $HEADKEY_API_KEY` to check
   - If set, show the key prefix (first 10 characters only) and confirm the configuration

2. Ask the user what scope they want to configure:
   - **Project-level** — each project uses a different Headkey agent (different API key per project). This is the recommended approach when working across multiple projects.
   - **Global** — same Headkey agent across all projects (single API key set once).

3. Ask for their Headkey API key (prefix: `cibfe_`).

4. Based on their chosen scope:

   **For project-level configuration:**
   - Check if `.claude/settings.json` exists in the current project root
   - Create or update it to include the API key:
     ```json
     {
       "env": {
         "HEADKEY_API_KEY": "cibfe_your_api_key_here"
       }
     }
     ```
   - Remind the user to add `.claude/settings.json` to `.gitignore` since it contains a secret
   - Check if `.gitignore` exists and whether it already includes `.claude/settings.json`; if not, offer to add it

   **For global configuration:**
   - Update `~/.claude/settings.json` to include the API key in the `env` block
   - Preserve any existing settings in the file

5. Verify the configuration works by restarting Claude Code or checking that the Headkey MCP tools are available.

6. Report success and explain that Headkey tools are now available in this session.

## Important

- Never log or display the full API key — only show the prefix (first 10 characters)
- Warn the user not to commit API keys to version control
- Each API key is associated with a specific Headkey agent, so project-level keys let different projects use different agents
- If the user already has a global key and wants to override it for a specific project, project-level settings take precedence
