# Installing Infograph (for AI agents such as Cline)

Infograph is a remote MCP server. There is nothing to clone, build or run, and no API key.

## 1. Add the server

Add this entry under `mcpServers` in the MCP settings file (`cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "infograph": {
      "type": "streamableHttp",
      "url": "https://app.infograph.ai/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Do not add an `Authorization` header: the server does not take a token you can paste.

## 2. Sign in

The server uses OAuth. The first connection answers `401` with a sign-in address: start the
client's OAuth sign-in for `infograph` (in the Cline CLI, `cline mcp` then "Authorize OAuth"). A
browser window opens: the user signs in to Infograph and chooses the account to work in.

The user needs an Infograph account (https://app.infograph.ai) with at least one file uploaded or
one source connected.

## 3. Check it works

Ask: "What data do I have in Infograph?" The agent should call `listFiles` and name the user's
tables.

## If it fails

- `401` after signing in: disconnect on the AI Connect page in Infograph, then sign in again.
- An answer that starts with a code in square brackets, such as `[RATE_LIMITED]`: the text after
  it says what to change.
- Help: https://infograph.ai/docs/ai-connect or support@infograph.ai
