# Infograph for Cursor

Connects Cursor to [Infograph](https://infograph.ai), so the agent can work with your business
data: find a table, query it with SQL, and build dashboards, reports and analyses you can keep and
share.

Infograph keeps your uploaded files and the data from your connected apps and databases (such as
Shopify, Stripe, Google Analytics, Postgres and Google Sheets) as tables in one private data lake.
Queries run there, over every row, and only the answer comes back to Cursor.

## What is in this plugin

- **An MCP server**, `https://app.infograph.ai/mcp` (`mcp.json`). Nothing runs on your machine.
- **A skill** (`skills/infograph/SKILL.md`) that tells the agent when to use Infograph and in what
  order to call its tools.

## Signing in

There is no API key. The first time the agent calls Infograph, Cursor opens a browser window: sign
in to Infograph and choose the account the agent should work in, your personal account or one of
your teams. You can disconnect it at any time on the AI Connect page in Infograph.

You need an Infograph account with at least one file uploaded or one source connected.

## What the agent can do

It acts as you, in the one account you chose.

| Reads | Changes something in Infograph |
|---|---|
| `listFiles`, `previewFile`, `sqlQuery` | `createArtifact`, `updateCode` |
| `listArtifacts`, `readCodeTree`, `readCode` | `shareArtifact`, `publishArtifact` |
| | `renameItems`, `deleteItems` |
| | `createUploadUrl`, `confirmUpload` |

Queries are read-only, and nothing in the apps your data came from is ever changed.

## Network and data

The plugin talks only to `app.infograph.ai` (the MCP server) and `clerk.infograph.ai` (sign-in). It
stores no credentials in this repository and sets no environment variables. Calls use the credits
of your Infograph plan.

## Try it

- What data do I have in Infograph?
- Which products brought in the most revenue last month?
- Build a dashboard of signups by week from our Postgres users table.

## Help

- Guide: https://infograph.ai/docs/ai-connect
- Privacy: https://infograph.ai/privacy
- Support: support@infograph.ai
