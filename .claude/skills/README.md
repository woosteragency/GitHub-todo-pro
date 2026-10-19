# OpenSEO Agent Skills

Vendored from [every-app/open-seo](https://github.com/every-app/open-seo) (`plugins/openseo/skills`, MIT license).

## Important: these need the OpenSEO MCP server to actually work

Each `SKILL.md` here is just instructions — they call MCP tools like `research_keywords`, `get_keyword_metrics`, `get_serp_results`, etc. Without the OpenSEO MCP server connected, Claude will read the skill but have no tool to call, so nothing will actually fetch data.

**This project self-hosts OpenSEO** — see [`openseo-selfhost/DEPLOY.md`](../../openseo-selfhost/DEPLOY.md) for setup on a Hostinger VPS. Once deployed, add your instance's `https://YOUR_DOMAIN_OR_TUNNEL/mcp` as an MCP connector in claude.ai (Settings → Connectors) to make these skills functional.

Self-hosting needs a DataForSEO API key (pay-as-you-go, $50 minimum top-up) — see `docs/DATAFORSEO_API_KEY.md` in [every-app/open-seo](https://github.com/every-app/open-seo).

Skills included: `keyword-research`, `competitor-analysis`, `competitive-landscape`, `keyword-clustering`, `seo-audit`, `ai-visibility-audit`, `ai-prompt-research`, `link-prospecting`, `local-seo`, `seo-coach`, `seo-report`, `seo-project-setup`.
