# arXiv & OpenAlex Academic Paper Search + Clean Web Extract MCP Server

[![MCP Compatible](https://img.shields.io/badge/MCP-2024--11--05%20%7C%202025--06--18-blue)](https://modelcontextprotocol.io)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](#)
[![Free Tier](https://img.shields.io/badge/Free%20Tier-2%20Calls%2FDay-success)](https://agent-kiosk.vercel.app/mcp)
[![Unlimited Pass](https://img.shields.io/badge/Unlimited%20Pass-%241%20%2F%20%245-purple)](https://agent-kiosk.vercel.app/buy)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

> Search peer-reviewed scientific papers, citations, abstracts & PDFs across arXiv and OpenAlex, plus extract clean prompt-injection-scanned Markdown from any URL.

Looking for a fast, zero-dependency **arXiv MCP** or **OpenAlex academic research MCP server** for Claude Desktop, Cursor, or Codex? `arxiv-academic-search-mcp` searches millions of preprints and peer-reviewed papers with citation counts, DOIs, and direct PDF links — paired with a clean Markdown web extractor that scans pages for hidden prompt-injection attacks.

---

## Why Use `arxiv-academic-search-mcp`?

- **Unified arXiv + OpenAlex Literature Search (`academic_search`)** — Query computer science, AI/ML, physics, quant finance, biomedicine, and economics papers sorted by citations or recency, complete with abstracts, authors, year, and open-access PDF links.
- **Clean LLM Markdown Web Extractor (`web_extract`)** — Converts documentation, HTML papers, blog posts, and research pages into clean Markdown while flagging hidden prompt-injection payloads.
- **Zero Python / Zero API Key Setup** — Runs immediately on Node >=18 (`npx` or remote Streamable-HTTP) with 2 free calls/day out of the box.
- **2 Free Calls / Day Out of the Box** — Works immediately with **zero configuration** and **no API key required**.
- **Instant Unlimited Upgrade** — Need high-volume production calls? Grab an instant API key at **[https://agent-kiosk.vercel.app/buy](https://agent-kiosk.vercel.app/buy)** (**$1 Starter 7-Day Pass** or **$5 Pro 30-Day Pass**) or pay per request natively via **x402 (USDC on Base)**.

---

## Option 1: Zero-Install Remote MCP URL (Fastest)

Connect directly via **Streamable-HTTP MCP** without installing anything locally:

- **Free Tier (2 Free Calls/Day, Zero Config):**
  ```text
  https://agent-kiosk.vercel.app/mcp
  ```
- **Paid Unlimited URL (With Prepaid Pass Key):**
  ```text
  https://agent-kiosk.vercel.app/mcp?api_key=ak_live_YOUR_KEY_HERE
  ```

> **Get an Instant API Key in 10 Seconds:** **[https://agent-kiosk.vercel.app/buy](https://agent-kiosk.vercel.app/buy)**
> - **$1.00 USDC** — **7-Day Starter Pass** (Instant `ak_live_...` key)
> - **$5.00 USDC** — **30-Day Pro Pass** (Full unmasked datasets across all endpoints)

---

## Option 2: Local `npx` / Stdio Setup (Claude Desktop, Cursor, Codex)

This package is **pure Node.js >= 18** with **zero external npm dependencies**, exposing **only** the 2 focused tools for this workflow so your LLM context window stays lean.

### Claude Desktop (`claude_desktop_config.json`)

```json
{
  "mcpServers": {
    "arxiv-academic-search-mcp": {
      "command": "npx",
      "args": ["-y", "github:ralf9090/arxiv-academic-search-mcp"],
      "env": {
        "AGENT_KIOSK_API_KEY": ""
      }
    }
  }
}
```
*(Leave `AGENT_KIOSK_API_KEY` empty for **2 free calls/day**, or paste your `ak_live_...` key from [agent-kiosk.vercel.app/buy](https://agent-kiosk.vercel.app/buy) for unlimited access.)*

### Cursor (`.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "arxiv-academic-search-mcp": {
      "command": "npx",
      "args": ["-y", "github:ralf9090/arxiv-academic-search-mcp"],
      "env": {
        "AGENT_KIOSK_API_KEY": "ak_live_OPTIONAL_PASS_KEY"
      }
    }
  }
}
```

### OpenAI Codex CLI (`~/.codex/config.toml`)

```toml
[mcp_servers.arxiv_academic_search_mcp]
command = "npx"
args = ["-y", "github:ralf9090/arxiv-academic-search-mcp"]
env = { AGENT_KIOSK_API_KEY = "" }
```

### Run Directly via `git clone` + `node index.js`

```bash
git clone https://github.com/ralf9090/arxiv-academic-search-mcp.git
cd arxiv-academic-search-mcp
node index.js
```

---

## Included MCP Tools (2)

### `academic_search`
Deep scientific & academic research tool. Queries OpenAlex and arXiv for peer-reviewed papers and preprints, returning citation counts, reconstructed abstracts, authors, and direct Open-Access PDF links.

| Parameter | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `query` | `string` | **Yes** | Research topic or scientific query (e.g., 'autonomous AI agents', 'zero knowledge proofs') |
| `limit` | `number` | No | Number of papers to return (1-15, default: 5) |
| `x_api_key` | `string` | No | Optional ak_live_... 30-day Prepaid API Pass key to unlock the full unmasked dataset |

### `web_extract`
Extract clean, LLM-ready Markdown from any web URL while automatically scanning the page for hidden Prompt Injection traps targeting AI agents.

| Parameter | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `url` | `string` | **Yes** | Full URL to extract (must start with http:// or https://) |
| `max_length` | `number` | No | Maximum markdown character length to return (500-25000, default: 8000) |
| `x_api_key` | `string` | No | Optional ak_live_... 30-day Prepaid API Pass key to unlock the full unmasked dataset |


---

## Example Prompts

- "Search arXiv and OpenAlex for 2025-2026 papers on test-time compute scaling in reasoning LLMs."
- "Find the highest-cited papers on high-frequency market making and order book imbalance."
- "Extract clean Markdown from https://arxiv.org/abs/2305.18290 and summarize the core objective function."

---

## Pricing & Rate Limits

| Tier | Cost | Quota | Setup |
| :--- | :--- | :--- | :--- |
| **Free Trial** | **$0** | **2 Free Calls / Day** | Zero config — works out of the box |
| **Starter Pass** | **$1 USDC** | **7 Days Unlimited** | Get `ak_live_...` at [agent-kiosk.vercel.app/buy](https://agent-kiosk.vercel.app/buy) |
| **Pro Pass** | **$5 USDC** | **30 Days Unlimited** | Get `ak_live_...` at [agent-kiosk.vercel.app/buy](https://agent-kiosk.vercel.app/buy) |
| **x402 Pay-Per-Call** | **$0.008–$0.10** | Unlimited autonomous | Pass `payment_signature` (Base USDC EIP-3009) |

---

## License

MIT © [ralf9090](https://github.com/ralf9090) — Powered by [Agent Kiosk](https://agent-kiosk.vercel.app) ([Upgrade / Buy API Key](https://agent-kiosk.vercel.app/buy)).
