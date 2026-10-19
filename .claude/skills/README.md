# OpenSEO Agent Skills

Vendored from [every-app/open-seo](https://github.com/every-app/open-seo) (`plugins/openseo/skills`, MIT license).

## Important: these need the OpenSEO MCP server to actually work

Each `SKILL.md` here is just instructions — they call MCP tools like `research_keywords`, `get_keyword_metrics`, `get_serp_results`, etc. Without the OpenSEO MCP server connected, Claude will read the skill but have no tool to call, so nothing will actually fetch data.

To make these functional, connect the MCP server (one of):

- **Hosted** (simplest): add `https://app.openseo.so/mcp` as an MCP connector. Requires an OpenSEO account/subscription (~$10/month per the plugin description).
- **Self-hosted**: run OpenSEO yourself (Docker/Cloudflare) with your own DataForSEO API key, then point the connector at your instance.

Skills included: `keyword-research`, `competitor-analysis`, `competitive-landscape`, `keyword-clustering`, `seo-audit`, `ai-visibility-audit`, `ai-prompt-research`, `link-prospecting`, `local-seo`, `seo-coach`, `seo-report`, `seo-project-setup`.
