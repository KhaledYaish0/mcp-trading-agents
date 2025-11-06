# MCP Trading Agents

This project implements an **Agentic AI trading system** using the **Model Context Protocol (MCP)**.
The system manages a trading account, retrieves market prices, and sends notifications. Agents such as
Trader and Researcher interact with MCP servers rather than directly calling functions.

## Project Structure

```
.accounts.py               # Core account & portfolio logic
.market.py                 # Stock price retrieval (Polygon API or fallback)
.accounts_server.py        # MCP server exposing trading & portfolio tools
.market_server.py          # MCP server exposing price lookup
.push_server.py            # MCP server sending push notifications
.mcp_params.py             # Configures MCP server sets for each agent
4_lab4.ipynb               # Notebook orchestrating agents
memory/                    # Auto-generated memory DB files (ignored)
```

## Setup

1. Copy `.env.example` to `.env` and fill in real API keys.
2. Install dependencies using `uv` or standard setuptools.
3. Start servers (in 3 terminals):
```
uv run accounts_server.py
uv run market_server.py
uv run push_server.py
```
4. Open `4_lab4.ipynb` and run agent logic.

## Notes
- `.env` and `memory/` are ignored via `.gitignore`.
- If Polygon API is available, real-time or daily market data is used.
- Otherwise, the system falls back to generated random prices.
