# Smithery submission draft - TechnologyChecker.ai MCP

## Listing

- **Name**: TechnologyChecker.ai
- **Slug**: technologychecker
- **Website**: https://technologychecker.ai/
- **Repository**: https://github.com/Sambel/technologychecker-mcp
- **MCP docs**: https://technologychecker.ai/mcp
- **MCP endpoint**: https://technologychecker.ai/api/mcp/technologychecker
- **REST API docs**: https://technologychecker.ai/api/docs

## Description

TechnologyChecker.ai is an MCP server and REST API for querying website technology stacks.
AI agents can search 887k+ websites by the technologies they use, retrieve a domain's full
stack, browse the technology catalog, and detect adoption / removal signals over time.

A BuiltWith / Wappalyzer alternative built API-first for AI agents, GTM teams, and AI SDR
workflows.

## Category

Developer tools, sales intelligence, GTM, web intelligence, AI agents

## Tags

`mcp`, `api`, `website-technology-checker`, `tech-stack`, `builtwith-alternative`,
`wappalyzer-alternative`, `sales-intelligence`, `gtm`, `ai-agents`

## Authentication

Bearer token. Users can create an API key from their TechnologyChecker.ai account
at https://technologychecker.ai/api-keys.

## Tools

| Tool | Purpose |
| --- | --- |
| `search_sites` | Filter sites by tech, country, traffic floor, TLD |
| `get_site` | Full tech stack + first / last seen dates per technology for one domain |
| `list_techs` | Browse the 7,500+ technology catalog |
| `get_adoption_signals` | Sites that ADDED a given tech in the last N days |
| `get_removal_signals` | Sites that REMOVED a given tech in the last N days |
| `add_sites_to_list` | Pin matching sites into a named list, idempotent |

## Example prompts

- Find SaaS websites using Stripe and Webflow in the US.
- Show companies that recently adopted Anthropic SDK or Pinecone.
- Get the technology stack for vercel.com and summarize the GTM-relevant tools.

## Pricing

- Free tier: 10 API + MCP lookups / month, no credit card.
- Pro: 99 EUR / month, unlimited queries, full pagination, CSV / JSON exports.
- Sign up: https://technologychecker.ai/register

## Setup snippets

### Claude Desktop / Claude Code

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

### Cursor

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
