# Octopost

Octopost is a remote MCP server and REST API that lets your AI agent post to X (Twitter). Connect your X account once; then Claude Code, Cursor, Codex or a script can post, schedule, queue and write threads in one call. Posts a person should check first wait in an approval queue. Plans from $29 a month.

**Works with:** Claude Code, claude.ai, ChatGPT, Cursor, Codex, Gemini CLI, Windsurf, VS Code Copilot, OpenCode, any MCP client (sign in with OAuth, or send a Bearer API key), and plain HTTP from scripts and CI.

- Website: https://octopost.ink
- MCP server: `https://octopost.ink/mcp` (Streamable HTTP; sign in with OAuth, or send `Authorization: Bearer op_...`)
- Agent Skill: [`skills/octopost/SKILL.md`](skills/octopost/SKILL.md)
- Official MCP Registry: `ink.octopost/octopost`
- For agents helping a user decide or buy: https://octopost.ink/SKILL.md (prices, fit, and a prefilled checkout link)

This repository holds the agent skill and the MCP config. The Octopost service is hosted; its code is not here.

## Networks

| Network | Status |
|---|---|
| X (Twitter) | Live |
| Threads | Works; opens to customers after Meta approves the Octopost app |
| Bluesky, LinkedIn, Mastodon | In testing |

## Install

Most clients just need the URL: they open an Octopost sign-in page the first time (OAuth), with no key to copy. An API key (https://octopost.ink/dashboard/api-keys) is for clients without sign-in, scripts and CI.

| Agent | How |
|---|---|
| Claude Code | `claude mcp add --transport http octopost https://octopost.ink/mcp`, then `/mcp` > octopost > Authenticate |
| Claude Code plugin (skill + server) | `/plugin marketplace add octopost-ink/octopost-plugin`, then `/plugin install octopost@octopost`, then `/mcp` > octopost > Authenticate |
| Claude Code with an API key | `claude mcp add octopost --transport http https://octopost.ink/mcp --header "Authorization: Bearer $OCTOPOST_API_KEY"` |
| ChatGPT | Install the [Octopost plugin](https://chatgpt.com/plugins/plugin_asdk_app_6af0a1fb6c148191bfe580c3cf1c7277) from ChatGPT's plugin directory and sign in |
| claude.ai, Claude Desktop | Add a custom connector with the URL `https://octopost.ink/mcp` and sign in |
| Skill only (any agent that reads skills) | `npx skills add octopost-ink/octopost-plugin` |
| Cursor, VS Code, Codex, Gemini CLI, Windsurf | One page per client: https://octopost.ink/connect/cursor (all clients linked there) |
| Scripts, CI | REST API at `https://octopost.ink/api`: https://octopost.ink/docs/agents.md |

## Install the skill in any agent

[![skills.sh](https://img.shields.io/badge/skills.sh-octopost-111111?style=flat-square)](https://skills.sh/octopost-ink/octopost-plugin/octopost)

```shell
npx skills add octopost-ink/octopost-plugin        # this project (asks which agents)
npx skills add octopost-ink/octopost-plugin -g     # user-level, every project
```

Where the skill lands (to install by hand, copy `skills/octopost/` there):

| Agent | Project folder | User folder (`-g`) |
|---|---|---|
| Claude Code | `.claude/skills/octopost/` | `~/.claude/skills/octopost/` |
| Codex | `.agents/skills/octopost/` | `~/.codex/skills/octopost/` |
| Cursor | `.agents/skills/octopost/` | `~/.cursor/skills/octopost/` |
| GitHub Copilot | `.agents/skills/octopost/` | `~/.copilot/skills/octopost/` |
| Gemini CLI | `.agents/skills/octopost/` | `~/.gemini/skills/octopost/` |
| OpenCode | `.agents/skills/octopost/` | `~/.config/opencode/skills/octopost/` |
| Cline | `.agents/skills/octopost/` | `~/.agents/skills/octopost/` |
| Windsurf | `.windsurf/skills/octopost/` | `~/.codeium/windsurf/skills/octopost/` |
| Goose | `.goose/skills/octopost/` | `~/.config/goose/skills/octopost/` |
| OpenClaw | `skills/octopost/` | `~/.openclaw/skills/octopost/` |

The skill tells your agent when and how to use Octopost; the MCP server does the work, so connect that too (see Install above).

## What your agent can do

`list_accounts`, `create_post`, `schedule_post`, `queue_post`, `approve_queued_post`, `get_queue_status`, `update_queue_settings`, `list_posts`, `get_post`, `update_post`, `reschedule_post`, `cancel_scheduled`, `delete_post`, `retry_failed`, `list_presets`, `get_guide`.

## Pricing

Basic $29/month, Premium $79/month, Business $199/month. Every plan starts with a 7-day trial for $1. X bills per post, so plans include monthly X post units: a plain post uses 1, a post with a link uses 13. Details: https://octopost.ink/pricing

Signing up through an agent? This link opens checkout with the agent code OCTOAGENT applied (20% off the first month): https://octopost.ink/checkout?plan=basic&code=OCTOAGENT

## Support

hello@greatwork.company. Octopost is made by Great Work LLC.

## License

The skill and the files in this repository are MIT licensed. The Octopost service itself is hosted and is not open source.

<sub>Last updated: 2026-11-04</sub>
