# Docket MCP server

Docket is an SEO audit app that runs on your own computer. Its engine has an MCP server built in, so Claude, the ChatGPT desktop app or any MCP client can run an audit, read past audits and explain a problem with its fix.

The server is the `docket` command with the argument `mcp`. It talks over stdio, opens no network port, and needs no API key. You install Docket, then point your client at the engine.

## Install Docket

- Mac: download Docket from https://docketseo.app/download/ and drag it to Applications.
- Windows: run the installer from the same page.
- Linux: download `docket-<version>-linux-x86_64.tar.gz` from https://github.com/mattkerr09/docket-site/releases/latest and unpack it anywhere.

## Add it to your client

The engine is at:

- Mac: `/Applications/Docket.app/Contents/Resources/docket/docket`
- Windows: `C:\Users\YOU\AppData\Local\Docket\docket\docket.exe`
- Linux: the `docket` file in the folder you unpacked

Claude Code:

```
claude mcp add docket -- /Applications/Docket.app/Contents/Resources/docket/docket mcp
```

Claude Desktop, in `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "docket": {
      "command": "/Applications/Docket.app/Contents/Resources/docket/docket",
      "args": ["mcp"]
    }
  }
}
```

ChatGPT desktop: Settings, then MCP servers, add a server, choose STDIO, and give it the same command with the argument `mcp`.

Any other MCP client works the same way: the command and the argument are all it needs.

## Tools

| Tool | What it does |
|---|---|
| `audit_site` | Crawls a site and returns the score and every finding, with the pages affected and the fix. Takes `url`, and optionally `max_pages`, `max_seconds` and `offline`. |
| `get_last_report` | Returns the most recent kept audit, or the most recent of one site, without crawling again. |
| `explain_finding` | Explains one problem from a kept audit in full: what is wrong, which pages, why it matters and the fix. |
| `compare_audits` | Compares two kept audits of the same site: the score change, each area's change, and which problems are new or fixed. |
| `list_checks` | Lists every check Docket runs, by area, with its id and title. |

## Free and paid

Without a licence key, `audit_site` returns the free version: the score, the count of problems in each area and the most important problem in full. A licence ($59 once) returns every finding and fix. Details at https://docketseo.app/how-to/audit-your-site-from-an-ai-assistant/
