# Contributing

This repository documents the hosted OpenFinance MCP server at `https://api.openfinance.tech/agent/mcp`: setup for each AI client, the tool reference, examples and safety notes. The server itself is hosted, so most contributions are fixes to the docs.

## Good first contributions

- **Setup that didn't work.** Your client, its version, the config you used and what happened. Open an issue, or a pull request against the client's section in the README.
- **A client we don't cover yet.** Add a section under "Install in your AI client" with the exact config and where it goes.
- **An example that no longer matches a tool's response.** Include the call and the response you got.
- **Unclear wording.** Small edits are welcome.

## Rules for changes

1. Use the real endpoint, `https://api.openfinance.tech/agent/mcp`. Don't add a second endpoint or a local server.
2. Every request needs OAuth sign-in or an `x-api-key`. There is no keyless tier.
3. Orders go through only after the user confirms. Funds only move between the user's own wallets. Don't describe server-side trade limits or trade-only keys; they don't exist.
4. Check fees and limits against [docs.openfinance.tech](https://docs.openfinance.tech).
5. Never put a real API key, wallet key or account detail in an issue, example or screenshot.

## Security issues

Don't open a public issue for a security problem. Follow [SECURITY.md](./SECURITY.md).

## Agent skills

Playbooks that teach coding agents how to use these tools live in [openfinance-tech/skills](https://github.com/openfinance-tech/skills).
