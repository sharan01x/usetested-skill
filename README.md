# UseTested Skill

[![smithery badge](https://smithery.ai/badge/authk-smithery-ai-craftily886/usetested)](https://smithery.ai/servers/authk-smithery-ai-craftily886/usetested)

An [Agent Skill](https://agentskills.io) that teaches AI agents to check **receipts-verified reviews before paying for x402 services and paid APIs**.

UseTested (https://usetested.com) buys and tests paid API services with real money, then publishes structured reviews anchored to on-chain purchase receipts — aliveness, real price vs advertised, measured latency, error rates, and BUY/CAUTION/AVOID verdicts. 57% of listed x402 services are dead or never settle; a 10-second review check prevents wasted spend.

## Install

```bash
npx skills add sharan01x/usetested-skill
```

Then ask your agent: *"Check the UseTested review before I call that x402 service."*

## What's inside

- `SKILL.md` — the skill: when to trigger, and the three-step workflow (search → free review read → optional $0.05 category bundle)
- MCP alternative: `POST https://usetested.com/mcp` (streamable-http) — tools `search_services` (free), `get_review` (free), `get_bundle` ($0.05 via x402/USDC)

## Endpoints (from llms.txt)

| Endpoint | Cost | What |
|---|---|---|
| `GET /v1/search?q=` | free | service directory with verdicts, scores, prices |
| `GET /v1/review?service=` | free | full review JSON with on-chain receipts[] |
| `GET /v1/bundle?category=` | $0.05 | every review in a category |
| `POST /mcp` | free tools + $0.05 bundle | MCP server (streamable-http) |

Contact: usetested@redd.in