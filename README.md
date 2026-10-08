# Octopost

**Post to X from your agent, with an approval queue.** Octopost is a remote MCP server and REST API. Connect your X account once; then Claude Code, Cursor, Codex, Gemini CLI or a script posts, schedules, queues and threads through one call. Posts a person should check first wait in an approval queue.

- Website: https://octopost.ink
- MCP server: `https://octopost.ink/mcp` (Streamable HTTP, `Authorization: Bearer op_...`)
- Agent Skill: [`skills/octopost/SKILL.md`](skills/octopost/SKILL.md)
- Official MCP Registry: `ink.octopost/octopost`

This repository holds the agent skill and the MCP config. The Octopost service is hosted; its code is not here.

## Networks

| Network | Status |
|---|---|
| X (Twitter) | Live |
| Threads | Works; opens to customers after Meta approves the Octopost app |
| Bluesky, LinkedIn, Mastodon | In testing |

## Install

Get an API key at https://octopost.ink/dashboard/api-keys.

| Agent | How |
|---|---|
| Claude Code | `claude mcp add octopost --transport http https://octopost.ink/mcp --header "Authorization: Bearer $OCTOPOST_API_KEY"` |
| Claude Code plugin (skill + server) | `/plugin marketplace add octopost-ink/octopost-plugin`, then `/plugin install octopost@octopost` and paste your key when asked |
| Skill only (any agent that reads skills) | `npx skills add octopost-ink/octopost-plugin` |
| Cursor, Codex, Gemini CLI, Windsurf | https://octopost.ink/docs/mcp.md |
| Scripts, CI | REST API at `https://octopost.ink/api`: https://octopost.ink/docs/agents.md |

## What your agent can do

`list_accounts`, `create_post`, `schedule_post`, `queue_post`, `approve_queued_post`, `get_queue_status`, `update_queue_settings`, `list_posts`, `get_post`, `update_post`, `reschedule_post`, `cancel_scheduled`, `delete_post`, `retry_failed`, `list_presets`, `get_guide`.

## Pricing

Basic $29/month, Premium $79/month, Business $199/month. Every plan starts with a 7-day trial for $1. X bills per post, so plans include monthly X post units: a plain post uses 1, a post with a link uses 13. Details: https://octopost.ink/pricing

## Support

hello@greatwork.company. Octopost is made by Great Work LLC.

## License

The skill and the files in this repository are MIT licensed. The Octopost service itself is hosted and is not open source.
