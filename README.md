# WageAPI MCP Server

[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-blue)](https://modelcontextprotocol.io)

US and EU salary benchmarking data for 1,400+ occupations across 500+ metro areas and 27 EU countries. Query salary percentiles, compare locations with cost-of-living adjustment, search jobs with fuzzy matching, analyze historical wage trends, assess offer competitiveness, and validate EU pay transparency compliance. Data sourced from BLS OES, O\*NET, Eurostat SES, and BEA RPP.

## Installation

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "aethar-wageapi": {
      "url": "https://salary.wageapi.com/api/mcp",
      "headers": {
        "X-API-Key": "your_api_key_here"
      }
    }
  }
}
```

### Claude Code

Add to `.claude/settings.json` in your project root:

```json
{
  "mcpServers": {
    "aethar-wageapi": {
      "url": "https://salary.wageapi.com/api/mcp",
      "headers": {
        "X-API-Key": "your_api_key_here"
      }
    }
  }
}
```

### Cursor

Open Settings > MCP Servers > Add Server:

```json
{
  "aethar-wageapi": {
    "url": "https://salary.wageapi.com/api/mcp",
    "headers": {
      "X-API-Key": "your_api_key_here"
    }
  }
}
```

### VS Code (Copilot MCP)

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "aethar-wageapi": {
      "url": "https://salary.wageapi.com/api/mcp",
      "headers": {
        "X-API-Key": "your_api_key_here"
      }
    }
  }
}
```

## Available Tools

### Salary Tools

| Tool | Description |
|------|-------------|
| `get_salary_v1_salary_get` | Get salary data for a job title in any location (US metro or EU country). Returns percentiles, mean/median, gender pay gap, minimum wage, and cost-of-living index. |
| `compare_salary_v1_salary_compare_get` | Compare salaries for the same job across up to 10 locations. Supports mixed US/EU locations. |

### Jobs Tools

| Tool | Description |
|------|-------------|
| `search_jobs_v1_jobs_search_get` | Fuzzy search across 1,400+ US occupations. Returns SOC codes, descriptions, skills, education level, and job outlook. |

### Trends Tools

| Tool | Description |
|------|-------------|
| `get_trends_v1_trends_get` | Get historical salary trends and CAGR for a job title. Up to 10 years of BLS data. |

### Compliance Tools (EU Pay Transparency)

| Tool | Description |
|------|-------------|
| `validate_salary_range_v1_compliance_validate_salary_range_post` | Validate whether a job posting's salary range complies with EU Pay Transparency requirements. |
| `get_requirements_v1_compliance_requirements__country__get` | Get pay transparency requirements for a specific EU country (transposition status, rules, penalties). |
| `get_salary_bands_v1_compliance_salary_bands__country__get` | Get recommended compliant salary bands for a job title in an EU country. |
| `generate_pay_gap_report_v1_compliance_pay_gap_report_post` | Generate a gender pay gap analysis from company workforce data. |

### Intelligence Tools (Semantic)

| Tool | Description |
|------|-------------|
| `get_salary_competitiveness_v1_salary_competitiveness_get` | Assess whether a salary offer is competitive for a role and location. Returns percentile rank and market assessment. |
| `get_best_cities_v1_best_cities_for_get` | Rank cities or countries by salary for an occupation. Supports US, EU, or all regions. |
| `get_salary_adjusted_v1_salary_adjusted_get` | Calculate salary adjusted for cost of living between two locations (US and/or EU). |

## Example Prompts

These prompts work directly with Claude, Cursor, or any MCP-compatible AI client:

- "What do software developers earn in Austin, TX?"
- "Compare software developer salaries between Austin TX, Berlin, and Paris"
- "Is a $150K offer for a senior data scientist in Seattle above market?"
- "What are the best-paying US cities for software developers?"
- "How have software developer salaries changed over the last 5 years?"
- "What salary in Berlin equals my $120K in San Francisco as a developer?"
- "Is a EUR 45K-65K range valid for a software developer posting in Germany?"
- "Find occupations related to nursing"

## Authentication

All tools require an API key. Get one at [RapidAPI](https://rapidapi.com/AETHAR/api/wageapi) or [wageapi.com](https://wageapi.com).

Pass the key via the `X-API-Key` header in your MCP server configuration (see installation instructions above).

## Links

- [RapidAPI Listing](https://rapidapi.com/AETHAR/api/wageapi)
- [Demo Dashboard](https://salary.wageapi.com/demo)
- [Workforce Data Suite](https://wageapi.com)

## Part of Workforce Data Suite

WageAPI works alongside [CostAPI](https://github.com/aethar-dev/costapi-mcp) (cost-of-living and price index data for 190+ countries). Both are available as MCP servers. Configure both for comprehensive salary + cost-of-living analysis.

## License

The MCP server endpoint is provided as part of WageAPI. Source code is proprietary.
