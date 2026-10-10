# Fincept MCP

<img src="assets/logo.png" alt="Fincept" width="120">

Hosted [Model Context Protocol](https://modelcontextprotocol.io) server for [Fincept Terminal](https://fincept.in). It gives Claude Code, Codex, Cursor, VS Code and any other MCP client access to markets data, research and analytics, through 440 platform tools and 15 quant engines.

- **Endpoint:** `https://enterprise.fincept.in/mcp` (Streamable HTTP)
- **Auth:** OAuth 2.1 browser sign-in with your Fincept account. You don't need an API key.
- **Plan:** any Fincept Exclusive plan: Exclusive, Exclusive+ or Exclusive Pro ([pricing](https://fincept.in/pricing))
- **Docs:** [docs.fincept.in](https://docs.fincept.in)
- **Registry:** `in.fincept/mcp` on the [official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=in.fincept)

## Connect

**Claude Code**
```bash
claude mcp add --transport http --scope user fincept https://enterprise.fincept.in/mcp
```
Then run `/mcp`, pick `fincept` and choose **Authenticate**.

**Codex**
```bash
codex mcp add fincept --url https://enterprise.fincept.in/mcp
```

**Cursor** (`~/.cursor/mcp.json`)
```json
{ "mcpServers": { "fincept": { "url": "https://enterprise.fincept.in/mcp" } } }
```

**VS Code** (`.vscode/mcp.json`)
```json
{ "servers": { "fincept": { "type": "http", "url": "https://enterprise.fincept.in/mcp" } } }
```

Any other client that supports remote HTTP servers with OAuth works too. The first call opens fincept.in in your browser so you can authorize the client.

## What's included

| Area | Covers |
|---|---|
| Markets | Quotes, OHLCV candles, option chains, futures curves, fundamentals, funds, symbol search |
| Data and filings | Global economic series, SEC filings, deals, economic calendar |
| Analytics and backtests | Portfolio analytics, screeners, option models, strategy backtests and sweeps |
| Portfolios and paper trading | Portfolios, ledgers, limits and the Fincept Paper account |
| News and alternative data | News, sentiment, monitors, maritime, trade and geopolitical data |
| Crypto | Venues, markets, derivatives, accounts and DeFi (read-only) |

**Engines:** Stats, Forecast, TS Forecast, Volatility, Panel, Quant, Technicals (201 indicators, 61 candlestick patterns), Change Points, Regimes, Copula, Allocation, Portfolio Optimizer, Portfolio Lab, Multi-Period, and Pricing (curves, bonds, swaps, credit and options).

## How it works

- **Discovery:** the server lists a small core set of tools. `fincept_search_tools`, `fincept_describe_tool` and `fincept_call_tool` reach every other tool in the catalog.
- **Results:** every tool returns the same structured result. Large results are stored and can be read page by page.
- **Credits:** tools use the same credits and quotas as the terminal.
- **No real money:** trading tools only reach the Fincept Paper account.

## Example prompts

```text
Using Fincept, get the latest quote for AAPL and the last 5 daily candles.
Using Fincept, fit an ARIMA(1,1,1) to the last 500 daily closes of ^NSEI and forecast 10 days.
Using Fincept, build a hierarchical risk parity portfolio from SPY, TLT, GLD and QQQ over 3 years.
```

## Links

- Documentation: https://docs.fincept.in
- Website: https://fincept.in
- Support: [open an issue](https://github.com/Fincept-Corporation/fincept-mcp-docs/issues)

This repository also holds the source of the documentation site. The site's pages are the `.mdx` files listed in `docs.json`.
