<p align="center">
  <a href="https://ybug.io/features/mcp-server"><img src="https://ybug.io/images/logo.svg" alt="Ybug" width="72" height="72"></a>
</p>

# Ybug MCP server

Bring your Ybug bug reports into your AI assistant.

[Ybug](https://ybug.io) collects visual feedback and bug reports from your website: a screenshot, the page URL, browser, device and screen size, and optionally console logs and network requests. The Ybug MCP server lets Claude, ChatGPT, Codex, Claude Code, Cursor, VS Code and other MCP clients read those reports and help you triage them. No more copying reports into chat.

```text
https://mcp.ybug.io/mcp
```

This is a remote server hosted by Ybug. There’s nothing to install or run. This repository holds the documentation and the [MCP Registry](https://registry.modelcontextprotocol.io) entry (`io.ybug/mcp`). The server itself is part of Ybug and is not open source.

## What you can ask

- “What feedback came in on the Acme project this week? Group it by page.”
- “Show me open high-priority bugs on Acme that nobody is assigned to.”
- “Read this report and find the likely cause in this repo.” *(in a coding agent, with a report link)*
- “Review the reports since Friday. Suggest priorities and duplicates, then apply the ones I approve with an internal note.”

More in the [example prompts](https://ybug.io/docs/mcp/prompts).

## Connect

1. Add `https://mcp.ybug.io/mcp` as a remote MCP server in your client.
2. Sign in with your Ybug account when asked. There’s no API key.
3. Pick a team and approve access.

Step-by-step guides:

| Client | Guide |
| --- | --- |
| Claude (web and desktop) | [Add a custom connector](https://ybug.io/docs/mcp/claude) |
| ChatGPT | [Create a developer-mode app](https://ybug.io/docs/mcp/chatgpt) |
| Codex | [`codex mcp add`](https://ybug.io/docs/mcp/codex) |
| Claude Code | [`claude mcp add`](https://ybug.io/docs/mcp/claude-code) |
| Cursor | [`mcp.json`](https://ybug.io/docs/mcp/cursor) |
| VS Code | [`mcp.json`](https://ybug.io/docs/mcp/vs-code) |
| Anything else | [Requirements for other clients](https://ybug.io/docs/mcp/other-clients) |

For example, in Claude Code:

```bash
claude mcp add --transport http ybug https://mcp.ybug.io/mcp
```

The server uses streamable HTTP and OAuth 2.1 with PKCE and dynamic client registration.

## Tools

| Tool | What it does | Plan |
| --- | --- | --- |
| `list_projects` | List your projects | BASIC |
| `get_project` | Get a project’s statuses, priorities and types | BASIC |
| `list_tags` | List the team’s tags | BASIC |
| `list_project_members` | List who feedback can be assigned to | BASIC |
| `list_feedback` | Find feedback by status, priority, type, tags, assignee, date or keyword | BASIC |
| `get_feedback` | Read one report in full, with screenshot and video links | BASIC |
| `get_feedback_console_logs` | Read a report’s console logs | BASIC |
| `get_feedback_network_requests` | Read a report’s network requests | BASIC |
| `list_comments` | Read a report’s comments | BASIC |
| `update_feedback` | Change status, priority, type, assignee and tags | STARTUP |
| `add_comment` | Add an internal comment | STARTUP |
| `create_tag` | Create a tag | STARTUP |

The assistant can’t delete anything, change settings or send public comments. Arguments and responses are in the [tool reference](https://ybug.io/docs/mcp/tools).

## Plans

Read access is included in BASIC. Triage tools need STARTUP or higher. There’s no extra charge for MCP, and it isn’t available on FREE. See [pricing](https://ybug.io/pricing).

## Permissions and privacy

- The assistant acts as you, in one team. It sees only the projects you can access and can change only what you could change in the dashboard.
- Reporter and commenter email addresses, phone numbers, the user data your site passes to the widget, and reporter location are never sent.
- Screenshot and video links expire after about an hour.
- Report text is written by other people, so it can contain instructions. The tools tell the assistant to treat it as data. Review what a coding agent plans to do before you approve it. [More on this](https://ybug.io/docs/mcp/permissions#instructions-inside-reports).
- Moving a report to Resolved or Closed can send the reporter your auto-reply, if you’ve turned it on.
- Revoke access any time under **Connected apps** in your Ybug account.

Details: [Permissions, plans and data](https://ybug.io/docs/mcp/permissions) · [Privacy policy](https://ybug.io/privacy-policy)

## Support

- [Documentation](https://ybug.io/docs/mcp)
- [Troubleshooting](https://ybug.io/docs/mcp/troubleshooting)
- [Contact](https://ybug.io/contact)

Found a problem with the server or the docs? Open an issue here, or send it through **Help → Submit feedback** in the Ybug dashboard.

## License

The documentation and `server.json` in this repository are available under the [MIT License](LICENSE). The Ybug service is subject to the [Ybug terms](https://ybug.io/terms).
