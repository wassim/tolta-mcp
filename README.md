# Tolta MCP server

Find jobs that fit you, apply to your matches and follow your applications from ChatGPT, Claude, OpenClaw and other AI assistants.

[Tolta](https://tolta.ai) is an AI job application agent. It finds fresh roles on company career boards, tailors your CV to each one and applies on the employer's own form. When a form asks something your profile can't answer, such as work authorization or salary, it holds the application and asks you instead of guessing.

```
You: Any good matches today?
Assistant: 6 new matches. The best is Senior Data Analyst at Northwind (fit 91)...
You: Apply to that one.
Assistant: Done. Tolta is preparing the application and will send it when it's ready.
```

## Server

- Address: `https://tolta.ai/mcp` (Streamable HTTP)
- Auth: OAuth 2.1 with dynamic client registration and PKCE. You sign in to Tolta and approve the assistant once. No API key.
- Who can connect: a Tolta member with a plan or a free trial ([pricing](https://tolta.ai/pricing)). During the trial your assistant can read but not apply.

## Tools

| Tool | What it does |
|---|---|
| `todays_matches` | Today's matches, best first, with a fit score out of 100 and the reasons |
| `search_jobs` | Search open jobs by keywords, remote arrangement or seniority |
| `get_job` | One job's role, salary, requirements and benefits, and your fit score |
| `list_applications` | Your applications and which ones are waiting on you |
| `get_application` | One application's status and the questions waiting for you |
| `apply_to_match` | Apply to one of today's matches, only when you ask |

Questions an application needs you to answer are answered in Tolta, never in the chat.

## Setup

### Claude

Settings → Connectors → Add custom connector. Name it Tolta, paste `https://tolta.ai/mcp`, then sign in to Tolta and approve Claude.

### ChatGPT

Turn on developer mode in Settings, add a connector named Tolta with `https://tolta.ai/mcp`, then sign in to Tolta and approve ChatGPT.

### Cursor

Settings → MCP → Add a remote server with `https://tolta.ai/mcp`, then sign in to Tolta and approve Cursor. The Cursor plugin in `.cursor-plugin/` uses the same server.

### OpenClaw

```bash
openclaw mcp set tolta '{"url":"https://tolta.ai/mcp","transport":"streamable-http","auth":"oauth"}'
openclaw mcp login tolta
```

Or install the skill: `clawhub install wassim/tolta`. The skill is in [`skills/tolta/SKILL.md`](skills/tolta/SKILL.md).

### Other clients

Add `https://tolta.ai/mcp` as a remote MCP server in any client that supports OAuth.

## Disconnect

In Tolta, open Settings → Security and press Disconnect next to the assistant.

## Links

- [Using Tolta from AI assistants](https://tolta.ai/ai-assistants)
- [How Tolta works](https://tolta.ai/how-it-works)
- [Pricing](https://tolta.ai/pricing)
- Support: support@tolta.ai

## License

MIT for this repository. The Tolta name and logo belong to Tolta.
