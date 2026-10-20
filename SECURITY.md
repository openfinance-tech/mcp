# Security

The OpenFinance MCP server can place orders and move funds from a user's OpenFinance wallets. We take reports about it seriously.

## Reporting a vulnerability

Please report security issues privately with **Report a vulnerability** on this repository's [Security tab](../../security/advisories/new). Don't open a public issue, pull request or discussion for a security problem.

Useful details to include:

- what you found and where (tool name, action, or endpoint);
- steps to reproduce, using your own account and small amounts;
- what an attacker could do with it.

Please don't access other people's accounts or funds, run load tests against production, or publish details before we've had a chance to fix the issue.

## In scope

- `https://api.openfinance.tech/agent/mcp` and its OAuth sign-in and consent flow
- Tool behaviour that could move funds or place orders without the user's confirmation
- Tool descriptions or responses that could steer an agent into an unsafe action
- Anything that exposes another user's data, keys or wallets

## What this repository contains

Documentation only: no code, no keys, no secrets and no install scripts. The server itself is hosted by OpenFinance.

## Safe use

- Prefer OAuth sign-in to API keys where your client supports it.
- Keep API keys in environment variables or your client's secret prompt. Never commit them or paste them into chats.
- Replace a key immediately if it may have been exposed.
- Keep your AI client's per-tool approval prompts switched on for OpenFinance.
