<p align="center">
  <a href="https://openfinance.tech/agents">
    <img src="./assets/banner.png" alt="OpenFinance: the trading MCP server for AI agents. Crypto, perps, stocks, prediction markets, forex and memecoins." width="100%" />
  </a>
</p>

<h1 align="center">OpenFinance MCP Server</h1>

<p align="center">
  <b>The easiest way to let your AI agent trade.</b><br />
  Research, trade and move money across every major market through one remote MCP connection. No install, no keys to juggle.
</p>

<p align="center">
  <a href="#quick-start"><img alt="MCP: Streamable HTTP" src="https://img.shields.io/badge/MCP-Streamable_HTTP-111111?style=flat-square" /></a>
  <a href="#authentication"><img alt="Auth: OAuth or API key" src="https://img.shields.io/badge/Auth-OAuth_%7C_API_key-111111?style=flat-square" /></a>
  <a href="#tool-reference"><img alt="18 tools, 100+ actions" src="https://img.shields.io/badge/Tools-18_tools_%C2%B7_100%2B_actions-111111?style=flat-square" /></a>
  <a href="https://docs.openfinance.tech"><img alt="Docs" src="https://img.shields.io/badge/Docs-docs.openfinance.tech-2563eb?style=flat-square" /></a>
  <a href="https://x.com/openfinancelabs"><img alt="Follow on X" src="https://img.shields.io/badge/X-@openfinancelabs-000000?style=flat-square&logo=x" /></a>
  <a href="https://discord.gg/6EA3z4HjSe"><img alt="Discord" src="https://img.shields.io/badge/Discord-Join-5865F2?style=flat-square&logo=discord&logoColor=white" /></a>
</p>

<p align="center">
  <a href="https://cursor.com/en/install-mcp?name=openfinance-tech&config=eyJ1cmwiOiJodHRwczovL2FwaS5vcGVuZmluYW5jZS50ZWNoL2FnZW50L21jcCJ9"><img alt="Add to Cursor" src="https://cursor.com/deeplink/mcp-install-dark.svg" height="32" /></a>
  &nbsp;
  <a href="https://insiders.vscode.dev/redirect/mcp/install?name=openfinance-tech&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.openfinance.tech%2Fagent%2Fmcp%22%7D"><img alt="Install in VS Code" src="https://img.shields.io/badge/VS_Code-Install_Server-0098FF?style=for-the-badge&logo=visualstudiocode&logoColor=white" height="32" /></a>
  &nbsp;
  <a href="https://insiders.vscode.dev/redirect/mcp/install?name=openfinance-tech&quality=insiders&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.openfinance.tech%2Fagent%2Fmcp%22%7D"><img alt="Install in VS Code Insiders" src="https://img.shields.io/badge/VS_Code_Insiders-Install_Server-24bfa5?style=for-the-badge&logo=visualstudiocode&logoColor=white" height="32" /></a>
</p>

---

The OpenFinance MCP server supercharges AI agents with trading skills. Connect Claude, ChatGPT, Cursor, Codex or any MCP client and your agent can:

- **Trade crypto spot and perpetuals** on Hyperliquid, with limit, market and TWAP orders, leverage and margin control.
- **Trade stocks, indices, commodities, forex and pre-IPO names** as Hyperliquid HIP-3 perps (for example `xyz:NVDA`).
- **Trade prediction markets** on Polymarket: sports, politics, crypto and world events, plus trader leaderboards.
- **Swap and bridge anything onchain** across 40+ EVM chains and Solana, with Relay and Jupiter routing.
- **Find and trade memecoins** with token search across 200+ chains, live prices and liquidity.
- **Launch tokens** on Robinhood Chain and Solana, including tokens paired against tokenized stocks.
- **Fund the account** with fiat, through card, bank transfer or UPI.

There is nothing to install or host. The server runs at one HTTPS endpoint, and your agent connects to it like any other remote MCP server.

```text
https://api.openfinance.tech/agent/mcp
```

> [!IMPORTANT]
> This server can place real orders and move real funds. Every write action is designed to ask you first, and you should keep your client's tool-approval prompts switched on. Read [Safety and security](#safety-and-security) before you trade.

## Contents

- [Quick start](#quick-start)
- [What your agent can do](#what-your-agent-can-do)
- [Supported chains](#supported-chains)
- [Authentication](#authentication)
- [Install in your AI client](#install-in-your-ai-client)
- [Use it from your own code](#use-it-from-your-own-code)
- [Tool reference](#tool-reference)
- [Example prompts](#example-prompts)
- [Safety and security](#safety-and-security)
- [Pair it with OpenFinance Skills](#pair-it-with-openfinance-skills)
- [Verify the connection](#verify-the-connection)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Links](#links)

## Quick start

Easy trading for your agent in under a minute.

**1. Create your account.** Sign in at [openfinance.tech](https://openfinance.tech). Your trading wallets (one EVM address for every EVM chain, plus a Solana address) are created for you.

**2. Add the server to your AI client.** In Claude Code, for example:

```bash
claude mcp add --transport http openfinance-tech https://api.openfinance.tech/agent/mcp
```

**3. Sign in and approve.** The first time your agent uses the server, your client opens an OpenFinance sign-in page. Approve the connection on the consent screen and you're done.

Then ask your agent something like:

> *"What's BTC's funding rate on Hyperliquid right now, and how has it moved over the last day?"*

Using a different client? See [Install in your AI client](#install-in-your-ai-client).

## What your agent can do

| Market | Venue | What the agent can do | Tool |
|---|---|---|---|
| **Crypto perpetuals** | Hyperliquid | Prices, order books, candles, funding; market, limit and TWAP orders; leverage and isolated margin | `hyperliquid` |
| **Crypto spot** | Hyperliquid, onchain DEXs | Spot orders on Hyperliquid; swaps on any EVM chain or Solana | `hyperliquid`, `relay_*`, `onchain_jupiter_*` |
| **Stocks, indices, commodities, FX, pre-IPO** | Hyperliquid HIP-3 | Discover markets by category, then trade them like any perp | `hyperliquid` |
| **Prediction markets** | Polymarket | Events, odds, order books, positions, PnL, leaderboards; place and cancel orders; redeem winnings | `polymarket` |
| **Hyperliquid outcomes** | Hyperliquid HIP-4 | Read outcome markets; split and merge outcome positions | `hyperliquid` |
| **Memecoins and long-tail tokens** | 200+ chains | Search by name or address, live price, volume, liquidity, market cap; then swap | `onchain_search_tokens`, `onchain_*` |
| **Bridging** | Relay | Quote and execute cross-chain transfers and swaps, including EVM ↔ Solana | `relay_get_quote`, `relay_execute`, `relay_get_status` |
| **Wallet** | Your OpenFinance wallets | Addresses, holdings per chain with USD values, token metadata, transfers | `get_wallet_addresses`, `onchain_*` |
| **Token launches** | Robinhood Chain, Solana | Launch on a bonding curve, trade pre-graduation, graduate, claim creator fees | `openfinance-launchpad*`, `openfinance-pons-launch` |
| **Fiat on-ramp** | Card, bank, UPI | Get a checkout link to buy crypto straight into your wallet | `get_onramp_url` |

## Supported chains

| Chain | Read | Trade, swap, send | Notes |
|---|:-:|:-:|---|
| Hyperliquid L1 | ✅ | ✅ | Perps, spot, HIP-3 and HIP-4 markets; funded with USDC from Arbitrum |
| Ethereum | ✅ | ✅ | |
| Base | ✅ | ✅ | |
| Arbitrum | ✅ | ✅ | Hyperliquid deposits and withdrawals settle here |
| Polygon | ✅ | ✅ | Polymarket settles here |
| Optimism, BNB Chain, Avalanche, Linea, Blast, Scroll, zkSync, Zora | ✅ | ✅ | Transfers and Relay swaps |
| Robinhood Chain (4663) | ✅ | ✅ | OpenFinance token launches and tokenized-stock pairs |
| Solana | ✅ | ✅ | Jupiter swaps, SPL transfers, Solana launchpad |
| 40+ EVM chains via Relay | ✅ | ✅ | Bridge and swap |
| 200+ chains | ✅ | | Token search and prices |

## Authentication

Every call to the server is authenticated. You can sign in two ways; both act on your own OpenFinance account.

| | OAuth sign-in (recommended) | API key |
|---|---|---|
| **How** | Add the URL only. Your client opens an OpenFinance sign-in and consent page. | Send your key in an `x-api-key` header. |
| **Best for** | Claude, ChatGPT, Cursor, VS Code, Claude Code, Gemini CLI | Scripts, bots, servers, and clients without OAuth support |
| **Secret stored in your client** | A token your client manages | Your API key |
| **Revoking** | Revoke the authorization from your OpenFinance account | Replace the key in OpenFinance; the old one stops working immediately |

**OAuth sign-in.** The server follows the MCP authorization spec, so supporting clients discover it automatically. When you connect, you sign in to OpenFinance and see which account is being connected; you have to confirm twice before anything is authorized.

**API key.** Sign in at [openfinance.tech](https://openfinance.tech), open **External AI** in the sidebar, and copy the API key shown under **Connect OpenFinance to your AI**. Keys start with `open_`.

> [!WARNING]
> **Treat your API key like a password.** It carries the same permissions as your account, including placing trades and sending funds from your wallets. Keep it in an environment variable or your client's secret prompt, never in a file you commit, and never paste it into a shared chat. If it leaks, replace it straight away.

The examples below read the key from an environment variable:

```bash
export OPENFINANCE_API_KEY="open_..."   # add to your shell profile, not to a repo
```

## Install in your AI client

Use the server name `openfinance-tech` and the URL `https://api.openfinance.tech/agent/mcp` everywhere. Each section shows the OAuth setup first, then the API-key alternative.

<details open>
<summary><b>Claude Code</b></summary>

**OAuth (recommended)**

```bash
claude mcp add --transport http openfinance-tech https://api.openfinance.tech/agent/mcp
```

Start Claude Code, run `/mcp`, choose **openfinance-tech** and select **Authenticate**. Add `--scope user` to make it available in every project.

**API key**

```bash
claude mcp add --transport http openfinance-tech https://api.openfinance.tech/agent/mcp \
  --header "x-api-key: $OPENFINANCE_API_KEY"
```

**Shared project config (`.mcp.json`)**: Claude Code expands environment variables, so the key never lands in the file:

```json
{
  "mcpServers": {
    "openfinance-tech": {
      "type": "http",
      "url": "https://api.openfinance.tech/agent/mcp",
      "headers": { "x-api-key": "${OPENFINANCE_API_KEY}" }
    }
  }
}
```

</details>

<details>
<summary><b>Claude.ai and Claude Desktop</b></summary>

1. Open **Settings → Connectors** and click **Add custom connector**.
2. Name: `OpenFinance`. URL: `https://api.openfinance.tech/agent/mcp`.
3. Click **Add**, then **Connect**, and approve the connection on OpenFinance.
4. In a chat, open the tools menu and switch **OpenFinance** on.

Connectors you add on Claude.ai also appear in Claude Desktop. Custom connectors are available on Claude's paid plans; on Team and Enterprise an owner may need to add them first.

**API key alternative (Claude Desktop only).** Bridge the server through [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) in `claude_desktop_config.json` (**Settings → Developer → Edit Config**), then fully quit and reopen Claude:

```json
{
  "mcpServers": {
    "openfinance-tech": {
      "command": "npx",
      "args": [
        "-y", "mcp-remote",
        "https://api.openfinance.tech/agent/mcp",
        "--header", "x-api-key:${OPENFINANCE_API_KEY}"
      ],
      "env": { "OPENFINANCE_API_KEY": "open_..." }
    }
  }
}
```

</details>

<details>
<summary><b>ChatGPT</b></summary>

1. Open **Settings → Apps & Connectors**. If you don't see a **Create** button, turn on **Developer mode** under **Advanced settings**.
2. Click **Create**. Name: `OpenFinance`. MCP server URL: `https://api.openfinance.tech/agent/mcp`. Authentication: **OAuth**.
3. Save, sign in to OpenFinance and approve the connection.
4. In a new chat, pick **OpenFinance** from the tools or connectors menu.

Custom connectors need a ChatGPT plan that supports them (Plus, Pro, Business, Enterprise or Edu); workspace admins may need to allow them.

</details>

<details>
<summary><b>Cursor</b></summary>

Click **[Add to Cursor](https://cursor.com/en/install-mcp?name=openfinance-tech&config=eyJ1cmwiOiJodHRwczovL2FwaS5vcGVuZmluYW5jZS50ZWNoL2FnZW50L21jcCJ9)**, or add this to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "openfinance-tech": {
      "url": "https://api.openfinance.tech/agent/mcp"
    }
  }
}
```

Cursor shows **Needs login** next to the server. Click it to sign in to OpenFinance.

**API key**

```json
{
  "mcpServers": {
    "openfinance-tech": {
      "url": "https://api.openfinance.tech/agent/mcp",
      "headers": { "x-api-key": "${env:OPENFINANCE_API_KEY}" }
    }
  }
}
```

</details>

<details>
<summary><b>VS Code (GitHub Copilot agent mode)</b></summary>

Click **[Install in VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=openfinance-tech&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.openfinance.tech%2Fagent%2Fmcp%22%7D)**, or run **MCP: Add Server** from the Command Palette and paste the URL. VS Code signs you in with OAuth.

**API key**, with VS Code prompting for the key once and storing it securely (`.vscode/mcp.json` or your user `mcp.json`):

```json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "openfinance-api-key",
      "description": "OpenFinance API key",
      "password": true
    }
  ],
  "servers": {
    "openfinance-tech": {
      "type": "http",
      "url": "https://api.openfinance.tech/agent/mcp",
      "headers": { "x-api-key": "${input:openfinance-api-key}" }
    }
  }
}
```

VS Code uses `servers`, not `mcpServers`. Open Copilot Chat, switch to **Agent** mode, and the OpenFinance tools appear in the tools picker.

</details>

<details>
<summary><b>Codex (CLI and IDE extension)</b></summary>

```bash
codex mcp add openfinance-tech --url https://api.openfinance.tech/agent/mcp
```

If Codex asks you to sign in, run `codex mcp login openfinance-tech`.

**API key** in `~/.codex/config.toml`, read from your environment:

```toml
[mcp_servers.openfinance-tech]
url = "https://api.openfinance.tech/agent/mcp"
env_http_headers = { "x-api-key" = "OPENFINANCE_API_KEY" }
```

The CLI and the IDE extension share this config. Run `/mcp` in Codex to check the server is connected.

</details>

<details>
<summary><b>Gemini CLI</b></summary>

Add to `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "openfinance-tech": {
      "httpUrl": "https://api.openfinance.tech/agent/mcp"
    }
  }
}
```

Then run `/mcp auth openfinance-tech` to sign in. For an API key instead, add `"headers": { "x-api-key": "$OPENFINANCE_API_KEY" }`.

</details>

<details>
<summary><b>Windsurf</b></summary>

Open Cascade, click the hammer icon, then **Configure**, and add:

```json
{
  "mcpServers": {
    "openfinance-tech": {
      "serverUrl": "https://api.openfinance.tech/agent/mcp",
      "headers": { "x-api-key": "${env:OPENFINANCE_API_KEY}" }
    }
  }
}
```

Windsurf uses `serverUrl` rather than `url`. Refresh the server list after saving.

</details>

<details>
<summary><b>Cline</b></summary>

In the Cline panel, open **MCP Servers → Configure MCP Servers** and add:

```json
{
  "mcpServers": {
    "openfinance-tech": {
      "type": "streamableHttp",
      "url": "https://api.openfinance.tech/agent/mcp",
      "headers": { "x-api-key": "open_..." }
    }
  }
}
```

Cline uses `streamableHttp` as the transport type. This file is stored on your machine; don't commit it.

</details>

<details>
<summary><b>Manus</b></summary>

**Settings → Connectors → + Add Connectors → Custom MCP → + Add Custom MCP → Direct Configuration**:

- Name: `OpenFinance`
- Transport: `Streamable HTTP`
- Server URL: `https://api.openfinance.tech/agent/mcp`
- Header: `x-api-key: open_...`

</details>

<details>
<summary><b>Hermes Agent</b></summary>

```bash
hermes mcp add openfinance-tech --url https://api.openfinance.tech/agent/mcp
```

Or in `~/.hermes/config.yaml`:

```yaml
mcp_servers:
  openfinance-tech:
    url: "https://api.openfinance.tech/agent/mcp"
    headers:
      x-api-key: "open_..."
```

Run `/reload-mcp`, or restart the agent.

</details>

<details>
<summary><b>OpenClaw</b></summary>

In `~/.openclaw/openclaw.json` (note the nested `mcp.servers` key):

```json
{
  "mcp": {
    "servers": {
      "openfinance-tech": {
        "url": "https://api.openfinance.tech/agent/mcp",
        "headers": { "x-api-key": "open_..." }
      }
    }
  }
}
```

</details>

<details>
<summary><b>Any other MCP client</b></summary>

| Setting | Value |
|---|---|
| Transport | Streamable HTTP |
| URL | `https://api.openfinance.tech/agent/mcp` |
| Auth | OAuth 2.1 with dynamic client registration (discovered from the server's `WWW-Authenticate` header), **or** header `x-api-key: open_...` |

If your client only supports local (stdio) servers, bridge it with `npx -y mcp-remote https://api.openfinance.tech/agent/mcp`.

</details>

## Use it from your own code

Building your own agent? Connect with the official MCP SDKs.

<details open>
<summary><b>TypeScript</b></summary>

```bash
npm install @modelcontextprotocol/sdk
```

```ts
import { Client } from "@modelcontextprotocol/sdk/client/index.js";
import { StreamableHTTPClientTransport } from "@modelcontextprotocol/sdk/client/streamableHttp.js";

const transport = new StreamableHTTPClientTransport(
  new URL("https://api.openfinance.tech/agent/mcp"),
  { requestInit: { headers: { "x-api-key": process.env.OPENFINANCE_API_KEY! } } },
);

const client = new Client({ name: "my-trading-agent", version: "1.0.0" });
await client.connect(transport);

const { tools } = await client.listTools();
console.log(tools.map((t) => t.name));

// Read-only: mid prices for every Hyperliquid market
const mids = await client.callTool({
  name: "hyperliquid",
  arguments: { action: "get_all_mids" },
});
console.log(mids.content);
```

</details>

<details>
<summary><b>Python</b></summary>

```bash
pip install mcp
```

```python
import asyncio, os
from mcp import ClientSession
from mcp.client.streamable_http import streamablehttp_client

URL = "https://api.openfinance.tech/agent/mcp"

async def main():
    headers = {"x-api-key": os.environ["OPENFINANCE_API_KEY"]}
    async with streamablehttp_client(URL, headers=headers) as (read, write, _):
        async with ClientSession(read, write) as session:
            await session.initialize()
            tools = await session.list_tools()
            print([t.name for t in tools.tools])

            # Read-only: mid prices for every Hyperliquid market
            mids = await session.call_tool("hyperliquid", {"action": "get_all_mids"})
            print(mids.content)

asyncio.run(main())
```

</details>

> [!TIP]
> Each tool's description tells the model exactly how to use it: which action to pick, what to check before an order, and when to ask the user. Pass the descriptions to your model unchanged for the best results.

## Tool reference

18 tools. The larger venues (`hyperliquid`, `polymarket` and the launchpads) group many operations behind one tool with an `action` parameter. Actions marked ✍️ change state: they place orders, move funds or sign transactions.

### Trading venues

<details>
<summary><b><code>hyperliquid</code></b>: perps, spot, HIP-3 markets (stocks, FX, commodities, indices, pre-IPO), HIP-4 outcomes · 34 actions</summary>

| Group | Actions |
|---|---|
| Market data | `get_all_mids`, `get_market_metas`, `get_perp_categories`, `get_l2_book`, `get_token_details`, `get_candle_snapshot`, `get_all_dexs_asset_ctxs`, `set_all_dexs_asset_ctxs_subscription`, `get_ws_status`, `get_outcome_meta` |
| Account | `get_deposit_address`, `get_account_summary`, `get_batch_portfolio_states`, `get_rate_limit`, `get_user_fills`, `get_user_funding_history`, `get_user_abstraction` |
| Orders | ✍️ `place_order`, ✍️ `cancel_order`, ✍️ `modify_order`, `get_open_orders`, `get_historical_orders`, `get_order_status` |
| TWAP | ✍️ `place_twap_order`, ✍️ `terminate_twap_order`, `get_twap_fills` |
| Risk | ✍️ `update_leverage`, ✍️ `update_isolated_margin` |
| Funds | ✍️ `withdraw_to_arbitrum`, ✍️ `set_user_abstraction` |
| Outcomes (HIP-4) | ✍️ `split_outcome`, ✍️ `merge_outcome`, ✍️ `merge_question`, ✍️ `negate_outcome` |

Fund your Hyperliquid account by sending USDC on Arbitrum to the address from `get_deposit_address`. Withdrawals go back to the same address on Arbitrum.

</details>

<details>
<summary><b><code>polymarket</code></b>: prediction markets, odds, positions, leaderboards · 32 actions</summary>

| Group | Actions |
|---|---|
| Discovery | `get_events`, `get_event`, `get_event_live_volume`, `get_markets`, `get_market`, `search`, `get_market_stats` |
| Prices | `get_orderbooks`, `get_prices`, `get_spread`, `get_last_trade_price`, `get_market_trades` |
| Traders | `get_leaderboard`, `get_builder_trades` |
| Your account | `get_user_positions`, `get_user_closed_positions`, `get_user_activity`, `get_user_trades`, `get_user_portfolio`, `get_user_pnl`, `get_deposit_wallet` |
| Orders | ✍️ `place_order`, ✍️ `place_market_order`, ✍️ `place_orders`, ✍️ `cancel`, `get_order`, `get_user_orders`, `get_order_scoring` |
| Funds | ✍️ `wrap_collateral`, ✍️ `withdraw_and_bridge`, ✍️ `redeem`, ✍️ `redeem_all` |

Polymarket orders settle from your Polymarket deposit wallet, not your main wallet. Use `get_deposit_wallet` to find it before funding.

</details>

### Swaps, bridges and transfers

| Tool | What it does | |
|---|---|:-:|
| `relay_get_quote` | Quote a swap, bridge or bridge-and-swap across 40+ EVM chains and Solana | |
| `relay_execute` | Execute a Relay quote: signs every step and waits for completion | ✍️ |
| `relay_get_status` | Check a Relay transfer by its request ID | |
| `onchain_jupiter_order` | Quote a Solana swap through Jupiter | |
| `onchain_jupiter_execute` | Execute a Jupiter swap | ✍️ |
| `onchain_send_token` | Send any token to any address on the same chain (EVM or Solana) | ✍️ |

### Wallet and market data

| Tool | What it does |
|---|---|
| `get_wallet_addresses` | Your OpenFinance EVM address (the same on every EVM chain) and Solana address |
| `onchain_get_address_holdings` | Token and NFT holdings for an address on one chain, with optional USD values |
| `onchain_get_token_metadata` | Name, symbol, decimals and logo for one or many tokens |
| `onchain_get_token_usd_price` | Live USD price for one or many tokens |
| `onchain_search_tokens` | Find a token by name, symbol or address across 200+ chains, with price, volume and liquidity |
| `get_onramp_url` | A checkout link to buy crypto with card, bank transfer or UPI, paid into your wallet |

### Token launches

<details>
<summary><b><code>openfinance-launchpad-wrapper</code></b>: launch on Robinhood Chain with a fee module (keep, burn, split, raffle or pay holders) · 11 actions</summary>

✍️ `launch`, `simulate_launch`, `list_launches`, `get_launch`, `get_funding`, `list_creator_launches`, `get_raffle`, `get_raffle_claims`, `list_raffle_stocks`, `get_readiness`, `get_keeper_status`

</details>

<details>
<summary><b><code>openfinance-launchpad-v4</code></b>: launch on Robinhood Chain as a Uniswap V4 position · 14 actions</summary>

✍️ `launch`, ✍️ `buy`, ✍️ `sell`, ✍️ `graduate`, ✍️ `claim_fees`, `list_launches`, `get_readiness`, `list_quote_assets`, `get_pair_terms`, `get_pool`, `get_market`, `get_candles`, `get_quote`, `get_fees`

</details>

<details>
<summary><b><code>openfinance-launchpad</code></b>: launch on Solana with a bonding curve that graduates to an AMM · 11 actions</summary>

✍️ `launch_token`, ✍️ `buy`, ✍️ `sell`, ✍️ `migrate`, ✍️ `claim_creator_fees`, `list_tokens`, `get_pool_state`, `quote_buy`, `quote_sell`, `get_pool_fees`, `get_creator_fees`

</details>

<details>
<summary><b><code>openfinance-pons-launch</code></b>: launch terms, quote assets (including tokenized stocks) and fees for Pons launches · 8 actions</summary>

`list_quote_assets`, `get_launch_terms`, `list_tokens`, `get_claimable_fees`, ✍️ `enable_holder_fee_sharing`, ✍️ `sweep_fees`, ✍️ `claim_fees`, ✍️ `launch_token` (legacy; new launches use `openfinance-launchpad-wrapper`)

</details>

## Example prompts

**Research**

- *"Which Hyperliquid perps have the highest funding right now? Show the top 10 with open interest."*
- *"List every stock perp on Hyperliquid and today's move for NVDA, TSLA and AAPL."*
- *"What are the odds on Polymarket for the next Fed rate decision? Show me the order book."*
- *"Who are the top 10 Polymarket traders in sports this month?"*
- *"Find PEPE on Base and tell me its price, 24h volume and liquidity."*

**Portfolio**

- *"What do I hold across all my wallets, in USD?"*
- *"Show my open Hyperliquid positions with entry price, PnL and liquidation price."*
- *"What are my open Polymarket positions and my PnL this week?"*

**Trading** (your agent will show you a summary and wait for your yes)

- *"Long 0.01 BTC on Hyperliquid at 5x with a limit at 2% below the current price."*
- *"Buy $25 of YES on the leading Polymarket outcome for the Champions League final."*
- *"Swap 50 USDC on Polygon for ETH on Base."*
- *"Swap 1 SOL for BONK."*
- *"TWAP 500 USDC into ETH perps over 2 hours."*

**Funding and launches**

- *"Give me a link to buy $100 of USDC with my card."*
- *"Launch a token called Rocket (RKT) on Robinhood Chain that burns its trading fees. Simulate it first."*

## Safety and security

**How write actions work.** OpenFinance creates your trading wallets when you sign up. When your agent calls a write action (✍️ above), the server signs and submits it from your account. To keep you in control:

- **Every write tool tells the agent to confirm with you first.** The agent should quote or preview, show you the tokens, amounts, chains, fees and recipient, and wait for your explicit yes in the current conversation.
- **Transfers to outside addresses get an extra warning.** If the recipient isn't one of your own wallets, the agent must show a clear external-transfer warning before it sends anything.
- **Keep your client's approval prompts on.** Most clients can ask before each tool call. Leave that on for OpenFinance, and don't add its tools to an auto-approve list. It's your second check if a model ever skips a confirmation.

**Protecting your account**

- Prefer **OAuth sign-in** over API keys where your client supports it.
- If you use a key, keep it in an environment variable or a secret prompt. Never commit it, and never paste it into a chat, issue or screenshot.
- Replace your key at once if you think it has been exposed; the old key stops working immediately.
- Revoke clients you no longer use from your OpenFinance account.
- Be careful with prompt injection. Don't ask an agent with trading access to act on instructions from web pages, emails or documents you don't trust, and never let it take an address or amount from that kind of content without checking it yourself.
- You can export your wallets' private keys from **Settings → Export Keys** in OpenFinance at any time.

**This repository** is documentation only. It contains no code, no keys, no secrets and no install scripts.

To report a vulnerability, use **Report a vulnerability** on this repository's [Security tab](../../security/advisories/new). Please don't open a public issue for security problems. See [SECURITY.md](./SECURITY.md).

## Pair it with OpenFinance Skills

The MCP server gives your agent the tools. [OpenFinance Skills](https://github.com/openfinance-tech/skills) teach it how to use them well: how to size a Hyperliquid perp, read a Polymarket order book, or route a cross-chain swap. They work in Claude Code, Cursor, Codex and most coding agents.

```bash
npx skills add openfinance-tech/skills -y
```

## Verify the connection

Check the server is reachable. Without credentials it answers `401` and points your client to sign-in, which is expected:

```bash
curl -si https://api.openfinance.tech/agent/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}' | head -3
```

With your API key it lists all 18 tools:

```bash
curl -s https://api.openfinance.tech/agent/mcp \
  -H "x-api-key: $OPENFINANCE_API_KEY" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

You can also browse the tools interactively with the [MCP Inspector](https://github.com/modelcontextprotocol/inspector):

```bash
npx @modelcontextprotocol/inspector
```

Choose **Streamable HTTP**, enter the URL, and sign in or add the `x-api-key` header.

## Troubleshooting

| Problem | Fix |
|---|---|
| `401 Unauthorized` | You're not signed in, or the key is wrong. Re-run your client's sign-in, or copy the key again from **External AI** (it starts with `open_`). |
| Sign-in page says there's no API key on the account | Open [openfinance.tech](https://openfinance.tech) once while signed in so your key is created, then retry. |
| Tools don't appear after editing config | Most clients only read MCP config at startup. Fully quit and reopen, or use the client's reload-servers command. |
| `429 Too Many Requests` | You've hit a rate limit. Slow your agent down, then retry. |
| A Polymarket order is rejected for funds | Polymarket trades from your deposit wallet. Ask your agent for `get_deposit_wallet` and fund that address. |
| A Solana swap fails with `412` | Your Solana wallet needs to be enabled for agent trading first. Follow the instructions in the error. |
| The agent says you hold nothing | Holdings are per chain. Ask it to check every chain, including Robinhood Chain (4663) for OpenFinance launches. |

## FAQ

<details>
<summary><b>Do I need to install or run anything?</b></summary>

No. OpenFinance is a hosted remote MCP server. You add a URL to your client; there's no package, Docker image or local process.

</details>

<details>
<summary><b>Which AI clients work?</b></summary>

Any client that supports remote MCP servers over Streamable HTTP, including Claude (web, desktop and Claude Code), ChatGPT, Cursor, VS Code, Codex, Gemini CLI, Windsurf, Cline, Manus, Hermes and OpenClaw. Clients that only support local servers can use `mcp-remote`.

</details>

<details>
<summary><b>Can my agent trade without asking me?</b></summary>

Every write tool instructs the agent to show a summary and wait for your explicit confirmation, and your client's approval prompts add a second check. Keep both on. Whether an agent follows instructions ultimately depends on the model and client, so stay in the loop for anything that moves money.

</details>

<details>
<summary><b>Who controls the wallets?</b></summary>

Your OpenFinance account. The same wallets are used in the OpenFinance app and over MCP, and you can export their private keys from **Settings → Export Keys**.

</details>

<details>
<summary><b>How do I fund my account?</b></summary>

Send crypto to your wallet address (ask your agent for `get_wallet_addresses`), or ask for a fiat on-ramp link with `get_onramp_url`. Hyperliquid and Polymarket each have their own deposit address; your agent can fetch both.

</details>

<details>
<summary><b>What's the difference between this and OpenFinance Skills?</b></summary>

The MCP server is the live tool layer: prices, orders, transfers. Skills are playbooks that teach an agent good judgement with those tools. Install both for the best results.

</details>

## Links

- **App:** [openfinance.tech](https://openfinance.tech)
- **Connect your agent:** [openfinance.tech/agents](https://openfinance.tech/agents)
- **Docs:** [docs.openfinance.tech](https://docs.openfinance.tech) · [llms.txt](https://docs.openfinance.tech/llms.txt)
- **Skills:** [openfinance-tech/skills](https://github.com/openfinance-tech/skills)
- **X:** [@openfinancelabs](https://x.com/openfinancelabs)
- **Discord:** [discord.gg/6EA3z4HjSe](https://discord.gg/6EA3z4HjSe)

## Disclaimer

Trading crypto, perpetual futures, prediction markets and other leveraged or volatile products carries a high risk of loss, and you can lose more than you expect. Nothing in this repository or in the server's responses is financial, investment or legal advice. AI agents make mistakes: review every action before you confirm it. Availability of some markets depends on where you live; you're responsible for following the laws that apply to you.

## License

The contents of this repository are released under the [MIT License](./LICENSE).
