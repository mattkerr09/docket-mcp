# Installing the Docket MCP server

Docket is a desktop app with its MCP server inside the app's engine. There is nothing to clone or build.

1. Check that Docket is installed.
   - Mac: `/Applications/Docket.app/Contents/Resources/docket/docket` exists.
   - Windows: `%LOCALAPPDATA%\Docket\docket\docket.exe` exists.
   - Linux: the user has unpacked `docket-<version>-linux-x86_64.tar.gz` from https://github.com/mattkerr09/docket-site/releases/latest. Ask where.
   If it is not installed, send the user to https://docketseo.app/download/ and stop until they have it.
2. Add an MCP server named `docket` with that path as the command and one argument, `mcp`. The transport is stdio. No environment variables or API keys are needed.
3. To check it works, call `list_checks`. It answers without touching the network.

An audit without a licence key returns the free version: the score, the count of problems in each area and the most important problem in full.
