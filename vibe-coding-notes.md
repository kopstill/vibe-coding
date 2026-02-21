# Vibe Coding Notes

## Guidelines

This document helps future sessions quickly restore context and working agreements without rereading the entire project.  
Think and research in English and response always in Chinese.  
Use the Sequential Thinking MCP server and surface the advanced reasoning steps in every response.  
When working with libraries, check the docs with Ref.

## System Instructions

Absolute Mode  
• Eliminate: emojis, filler, hype, soft asks, conversational transitions, call-to-action appendixes.  
• Assume: user retains high-perception despite blunt tone.  
• Prioritize: blunt, directive phrasing; aim at cognitive rebuilding, not tone-matching.  
• Disable: engagement/sentiment-boosting behaviors.  
• Suppress: metrics like satisfaction scores, emotional softening, continuation bias.  
• Never mirror: user's diction, mood, or affect.  
• Speak only: to underlying cognitive tier.  
• No: questions, offers, suggestions, transitions, motivational content.  
• Terminate reply: immediately after delivering info — no closures.  
• Goal: restore independent, high-fidelity thinking.  
• Outcome: model obsolescence via user self-sufficiency.

## MCP(Model Context Protocal)

### claude code

```plain
claude mcp add -s user sequential-thinking -- npx -y @modelcontextprotocol/server-sequential-thinking

claude mcp add -s user --transport http Ref https://api.ref.tools/mcp --header "x-ref-api-key: ref-a8680bfe2f7exxxxxxxx"

claude mcp add -s user context7 -- npx -y @upstash/context7-mcp --api-key ctx7sk-8033be31-xxxx-xxxx-xxxx-539eeeba0170

claude mcp add -s user --transport http exa https://mcp.exa.ai/mcp?exaApiKey=bcdeafb9-xxxx-xxxx-xxxx-ea3878fd3070

claude mcp add -s user firecrawl -e FIRECRAWL_API_KEY=fc-b003201c9cf44fb4aa7accf5xxxxxxxx -- npx -y firecrawl-mcp

claude mcp add -s user playwright -- npx -y @playwright/mcp@latest
```

### codex

```plain
codex mcp add sequential-thinking npx -y @modelcontextprotocol/server-sequential-thinking

[mcp_servers.Ref]
url = "https://api.ref.tools/mcp?apiKey=ref-8cc387f20450xxxxxxxx"

[mcp_servers.context7]
url = "https://mcp.context7.com/mcp"
http_headers = { "CONTEXT7_API_KEY" = "ctx7sk-9027ffce-954d-4f4f-a70f-xxxxxxxxxxxx" }

codex mcp add exa --url https://mcp.exa.ai/mcp?exaApiKey=f3fd357a-633d-4fbf-822f-xxxxxxxxxxxx

codex mcp add firecrawl --url https://mcp.firecrawl.dev/fc-f884e037cef2492e805ad3faxxxxxxxx/v2/mcp

codex mcp add playwright npx "@playwright/mcp@latest"
```

## Agent Skills

Tools  
[skills installer](https://github.com/vercel-labs/skills)  
[skills directory](https://skills.sh/)

npx skills list [-g]  
npx skills find [skill-name]  
npx skills check  
npx skills update

Awesome agent skills  
[https://github.com/ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)  
[https://github.com/travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills)  
[https://github.com/VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)

Anthropic's implementation of skills  
[https://github.com/anthropics/skills](https://github.com/anthropics/skills)  
npx skills add [--yes] [--global] anthropics/skills

Vercel's official collection of agent skills  
[https://github.com/vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)  
npx skills add [--yes] [--global] vercel-labs/agent-skills

UI/UX  
[https://github.com/nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)  
uipro init --ai claude # Claude Code  
uipro init --ai codex # Codex

Superpowers  
[https://github.com/obra/superpowers](https://github.com/obra/superpowers)

Everything Claude Code  
[https://github.com/affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)

## Something Interesting and Useful

ccstatusline - Customize your claude code statusline  
[https://github.com/sirmalloc/ccstatusline](https://github.com/sirmalloc/ccstatusline)

peon-ping - Stop babysitting your terminal  
[https://www.peonping.com/](https://www.peonping.com/)
