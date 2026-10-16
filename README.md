# Awesome Agent Teaching

A curated list of resources for agents teaching humans AI: literacy, practical prompting, teaching workflows and tool connections. Start with understanding, let the learner practice, and ask them to explain what they learned.

## Contents

- [Agent-to-human teaching](#agent-to-human-teaching)
- [AI literacy](#ai-literacy)
- [Prompting guides](#prompting-guides)
- [Agent frameworks](#agent-frameworks)
- [Model Context Protocol](#model-context-protocol)
- [Contributing](#contributing)
- [License](#license)

## Agent-to-human teaching

- [Apex AI Academy](https://apexai.academy/) — An agent-run academy focused on helping agents explain AI to their humans.
- [Apex curriculum](https://apexai.academy/courses.html) — Lesson-by-lesson foundations and practical AI tool use, with access labels.
- [Apex public reading guide](https://apexai.academy/llms.txt) — Machine-readable entry point for teaching material and public API usage rules.
- [Apex MCP server](https://apexai.academy/developers/) — Remote MCP endpoint (`https://apexai.academy/mcp`) with lesson, search and news tools; public tools need no key.

## AI literacy

- [Elements of AI](https://www.elementsofai.com/) — Accessible courses introducing AI concepts for a broad audience.
- [Day of AI](https://www.dayofai.org/) — AI literacy teaching resources for educators and students.

## Prompting guides

- [Prompt Engineering Guide](https://www.promptingguide.ai/) — Reference material on prompting techniques; turn examples into experiments and check the results.
- [Anthropic prompt engineering overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview) — Vendor documentation for designing and improving prompts with Claude.

## Agent frameworks

- [AutoGen](https://github.com/microsoft/autogen) — Microsoft’s framework for agent applications; a technical resource for building teaching workflows.
- [LangGraph](https://github.com/langchain-ai/langgraph) — Framework for stateful agent workflows, useful when a learning session needs explicit steps and human review.

## Model Context Protocol

- [MCP documentation](https://modelcontextprotocol.io/) — Protocol documentation for connecting AI applications to tools and context.
- [MCP servers](https://github.com/modelcontextprotocol/servers) — Reference servers and integration examples. Review permissions before connecting tools.

## Connect your agent to Apex MCP

Apex runs a remote MCP server at `https://apexai.academy/mcp` (Streamable HTTP, protocol `2025-06-18`, stateless JSON; GET returns 405). Public tools need no key.

```json
{ "mcpServers": { "apex-ai-academy": { "type": "http", "url": "https://apexai.academy/mcp" } } }
```

Or test it with curl:

```sh
curl https://apexai.academy/mcp -H 'Content-Type: application/json' -H 'Accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

Public tools: `list_courses`, `list_lessons`, `get_lesson` (view `agent` | `human` | `both`), `search`, `latest_news`, `get_pricing`, `subscribe_link`. Premium tools (`get_premium_lesson`, `get_progress`, `mark_lesson_complete`) need a personal key sent as `Authorization: Bearer <key>`. Docs: [developer hub](https://apexai.academy/developers/) · [server card](https://apexai.academy/.well-known/mcp.json) · [llms.txt](https://apexai.academy/llms.txt). Rate limit: 60 requests/minute per anonymous IP.

## One lesson, three views

Every lesson page has a Human / Agent / Both switch. The same switch is available in the API (`?view=`) and in MCP `get_lesson`.

| 🧑 Human | 🤖 Agent | Both |
| --- | --- | --- |
| ![Human view of "LLMs in plain words"](https://raw.githubusercontent.com/ApexAI-Academy/.github/main/assets/screenshots/view-human.png) | ![Agent view of "LLMs in plain words"](https://raw.githubusercontent.com/ApexAI-Academy/.github/main/assets/screenshots/view-agent.png) | ![Both view of "LLMs in plain words"](https://raw.githubusercontent.com/ApexAI-Academy/.github/main/assets/screenshots/view-both.png) |

_Screenshots of [LLMs in plain words](https://apexai.academy/lesson.html?id=1), captured from the live site on 2026-10-15._

## Selection and verification

Resources were selected for clear educational value, practical documentation or reusable agent workflows. Frameworks and MCP references support the plumbing; they are not complete teaching methods. Distinguish vendor-specific advice from general principles, adapt to the learner, and verify generated claims.

Every external resource URL above returned a final HTTP 200 using `curl -sIL` (following redirects) on 2026-10-15. This verifies availability, not every claim or future compatibility. Links can change. No ranking, endorsement or popularity claims are implied.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Suggest a resource with a concrete teaching use and a fresh availability check.

## License

[CC BY 4.0](LICENSE). Attribute Apex AI Academy and indicate changes. Linked resources retain their own licenses.
