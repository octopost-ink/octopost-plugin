# Installing Octopost in Cline

Octopost is a hosted MCP server. There is nothing to build, clone or run locally: Cline connects to the remote URL.

- Server URL: `https://octopost.ink/mcp`
- Transport: Streamable HTTP
- Auth: OAuth 2.1 (sign in from the browser), or an API key sent as `Authorization: Bearer op_...`

## Steps

1. The user needs an Octopost account with at least one connected network (X, Bluesky, Mastodon or LinkedIn). Plans start at $29/month with a 7-day trial for $1: https://octopost.ink
2. Add this server to Cline's MCP settings (`cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "octopost": {
      "type": "streamableHttp",
      "url": "https://octopost.ink/mcp"
    }
  }
}
```

3. When Cline asks to authenticate, open the sign-in link and approve access. No key needs to be copied.

### With an API key instead

If the user prefers a key (or OAuth isn't available), they can create one at https://octopost.ink/dashboard/api-keys and use:

```json
{
  "mcpServers": {
    "octopost": {
      "type": "streamableHttp",
      "url": "https://octopost.ink/mcp",
      "headers": {
        "Authorization": "Bearer op_YOUR_KEY"
      }
    }
  }
}
```

Never commit the key to a repository.

## Check that it works

Call the `list_accounts` tool. It returns the social accounts the user has connected. Only post to networks that appear there.

## Networks

| Network | Status |
|---|---|
| X (Twitter), Bluesky, Mastodon | Live |
| LinkedIn | Live (personal profiles) |
| Threads | Opens to customers after Meta approves the Octopost app |
| Instagram, Facebook, TikTok, YouTube, Pinterest, Reddit | In platform review, not available yet |
