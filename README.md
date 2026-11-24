# Distribewt MCP companion

Distribewt is a hosted remote MCP server for iOS app marketing. It turns an App Store link and real screenshots into TikTok and Instagram slideshows, then supports review, approval, scheduling, and weekly reports.

Product docs: https://distribewt.com/mcp/  
Product site: https://distribewt.com/  
Machine-readable product reference: https://distribewt.com/llms-full.txt

This repository is a public companion for MCP directories and awesome lists. The product implementation is not in this repo.

## Endpoint

- Transport: MCP Streamable HTTP
- URL: `https://mcp-k6cifennla-ul.a.run.app/mcp`
- Health check: `GET https://mcp-k6cifennla-ul.a.run.app/health`
- Auth: `Authorization: Bearer dwk_...` on every MCP request
- Key creation: Distribewt dashboard; MCP access requires a paid plan

Unauthenticated MCP requests return `401` with a `missing_api_key` error and a pointer to create a key.

## Claude Code

```bash
claude mcp add --transport http distribewt https://mcp-k6cifennla-ul.a.run.app/mcp \
  --header "Authorization: Bearer dwk_your_key"
```

## Cursor / generic MCP client

```json
{
  "mcpServers": {
    "distribewt": {
      "type": "streamable-http",
      "url": "https://mcp-k6cifennla-ul.a.run.app/mcp",
      "headers": {
        "Authorization": "Bearer dwk_your_key"
      }
    }
  }
}
```

## What the MCP server does

- Creates or updates an app profile from an App Store link and real screenshots
- Creates upload sessions and attaches owner screenshots
- Generates TikTok and Instagram slideshow drafts
- Lists jobs, posts, approvals, schedules, templates, and usage
- Approves or rejects posts before scheduling
- Schedules approved posts and pulls weekly performance reports

## What Distribewt is not

- Not an Android or web-app tool
- Not an AI avatar or AI-generated fake UI tool
- Not a general social scheduler
- Does not promise views, downloads, or virality

## Registry and listings

- Official MCP Registry: `io.github.AbdiAreys/distribewt`
- Registry page: https://registry.modelcontextprotocol.io/v0.1/servers/io.github.AbdiAreys/distribewt
- MCP guide: https://distribewt.com/mcp/

## Support

Email: hello@distribewt.com
