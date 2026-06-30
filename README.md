# TechnologyChecker.ai MCP Server

Query website technology stacks from Claude, Cursor, Zed, and other MCP-compatible clients.

This is documentation and configuration for the **official remote MCP endpoint** at
`https://technologychecker.ai/api/mcp/technologychecker`. There is no local server
to install. Add the endpoint to your AI client of choice and the agent gets six
tools for querying the live tech-stack database.

## What you can do with it

TechnologyChecker.ai is a BuiltWith / Wappalyzer alternative built API-first for AI agents,
GTM teams, and AI SDR workflows. From your agent, you can:

- Query the technology stack of 887k+ websites (CMS, hosting, JS framework, payment
  processor, analytics, AI tools)
- Filter sites by the technologies they use, country, traffic, TLD
- Browse the 7,500+ technology catalog
- Detect adoption and removal signals across 18 months of history
- Add matching sites to curated lists you can later export

## Endpoint

```
https://technologychecker.ai/api/mcp/technologychecker
```

Authentication: Bearer token from your TechnologyChecker.ai API key.
Create one at https://technologychecker.ai/api-keys after signing up.

## Setup: Claude Desktop / Claude Code

Edit your `claude_desktop_config.json` (macOS:
`~/Library/Application Support/Claude/claude_desktop_config.json`,
Windows: `%APPDATA%\Claude\claude_desktop_config.json`) and add:

```json
{
  "mcpServers": {
    "technologychecker": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://technologychecker.ai/api/mcp/technologychecker",
        "--header",
        "Authorization: Bearer YOUR_API_KEY"
      ]
    }
  }
}
```

Restart Claude Desktop. The six tools appear under the "technologychecker" server.

## Setup: Cursor

In Cursor settings, add an HTTP-type MCP server pointing at the endpoint:

```json
{
  "mcpServers": {
    "technologychecker": {
      "type": "http",
      "url": "https://technologychecker.ai/api/mcp/technologychecker",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Restart Cursor. Same six tools available to the agent.

## Tools

| Tool | Purpose |
| --- | --- |
| `search_sites` | Filter sites by tech slug(s), country, traffic floor, TLD. Returns paginated results. |
| `get_site` | Full tech stack for one domain, plus first-seen / last-seen dates per technology. |
| `list_techs` | Browse the 7,500+ technology catalog. Filter by category or partial name. |
| `get_adoption_signals` | Sites that ADDED a given tech in the last N days. |
| `get_removal_signals` | Sites that REMOVED a given tech in the last N days. |
| `add_sites_to_list` | Pin sites matching a filter into a named list, idempotent. Returns a shareable view URL. |

Full tool schemas at https://technologychecker.ai/mcp

## Example prompts

Try these from your MCP-enabled client:

- Find SaaS websites using Stripe and Webflow in the US.
- Show companies that recently adopted Anthropic SDK or Pinecone.
- Get the technology stack for vercel.com and summarize the GTM-relevant tools.

## REST API

Same data is available via REST at https://technologychecker.ai/api/docs.
Same Bearer token authentication. Same rate limits.

## Pricing

- **Free tier**: 10 API + MCP lookups / month. No credit card required.
- **Pro**: 99 EUR / month. Unlimited queries, full pagination, CSV / JSON exports,
  webhook signals.
- Sign up at https://technologychecker.ai/register.

## Links

- Website: https://technologychecker.ai
- Landing page: https://technologychecker.ai/lp/website-technology-checker
- REST API docs: https://technologychecker.ai/api/docs
- MCP docs: https://technologychecker.ai/mcp
- Pricing: https://technologychecker.ai/pricing

## GitHub topics

`mcp`, `mcp-server`, `website-technology-checker`, `tech-stack`,
`builtwith-alternative`, `wappalyzer-alternative`, `sales-intelligence`,
`gtm`, `ai-agents`

## License

MIT. See [LICENSE](LICENSE).
