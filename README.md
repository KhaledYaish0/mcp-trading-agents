# MCP Trading Agents (Lab 4 + Lab 5)

This project demonstrates an **Agentic AI trading system** using the **Model Context Protocol (MCP)**.  
Instead of calling functions directly, the agents communicate with **MCP servers** that provide tools for:
- Account management (balance, buy, sell, holdings)
- Market price retrieval (Polygon API if available, fallback otherwise)
- Push notifications (optional)

---

## 📌 Lab Structure

### **Lab 4 – Core System**
Lab 4 builds the main system:
- Defines the trading account model.
- Connects to a market price source.
- Exposes functionality through **MCP servers**.
- Implements two agents:
  - **Researcher Agent** → gathers market insights.
  - **Trader Agent** → decides whether to buy or sell.


---

### **Lab 5 – Automated Loop + Reset**
Lab 5 doesn’t add new trading logic.  
Instead, it focuses on:
- Running the trader repeatedly (looping cycles).
- Resetting all trader accounts to clean starting states.


---

## 📂 Main Files

```
accounts.py           # Account model + buy/sell logic
market.py             # Market price lookup (API or fallback)
database.py           # Storage for logs, balances, and prices

accounts_server.py    # MCP Server for trading actions
market_server.py      # MCP Server for price retrieval
push_server.py        # MCP Server for push notifications

mcp_params.py         # Specifies which servers each agent connects to
reset.py              # Resets trader accounts (Lab 5)
4_lab4.ipynb          # Lab 4 notebook (manual trading demonstration)
5_lab5.ipynb          # Lab 5 notebook (automated trading loop)
```

Optional UI (not required for labs):

```
app.py                # Gradio dashboard to visualize traders
traders.py            # Multi-trader logic
trading_floor.py      # Automatic background trading loop (scheduler)
templates.py / util.py / tracers.py # UI and logging helpers
```

---

## ▶️ Running the System

### Start MCP Servers (3 terminals):
```bash
uv run accounts_server.py
uv run market_server.py
uv run push_server.py
```

### Lab 4:
Open:
```
4_lab4.ipynb
```
Run cells in order.

### Lab 5:
```python
from reset import reset_traders
reset_traders()
```
Then run:
```
5_lab5.ipynb
```

---

## (Optional) UI Dashboard
```bash
uv run app.py
```

The UI is optional and available for visualization, not required for lab submission.
