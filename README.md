
# MCP Trading Agents Project

This project demonstrates an agentic trading workflow powered by the **Model Context Protocol (MCP)**.
The system consists of multiple servers that simulate a market environment, manage user accounts, and deliver real-time updates through push notifications.

The project includes **Lab 4** and **Lab 5**, where Lab 4 introduces the core MCP communication process, and Lab 5 extends the system with a more interactive UI and agent-driven decision logic.

## Features

- MCP-enabled agent communication
- Accounts server to handle balances and transactions
- Market simulation server for buying, selling, and price updates
- Push notification server for real-time updates
- Memory storage to persist system state between runs
- Lab 4 notebook for basic MCP testing
- Lab 5 notebook for UI and agent workflows

## Project Structure

```
MCP PROJECTT 2/
│
├─ 4_lab4.ipynb          → Intro lab for testing MCP interactions
├─ 5_lab5.ipynb          → Enhanced lab with UI and agent logic
│
├─ app.py                → Main runtime script coordinating all components
│
├─ accounts.py           → Account data model and balance logic
├─ accounts_client.py    → Client-side interface to the accounts server
├─ accounts_server.py    → Server responsible for account/session operations
│
├─ market.py             → Market price and trading logic
├─ market_server.py      → Server responsible for executing buy/sell requests
│
├─ push_server.py        → Real-time message broadcasting / notification server
│
├─ database.py           → System data persistence (balances, logs, state)
│
├─ mcp_params.py         → MCP configuration for tool exposure
│
├─ reset.py              → Resets state to default
│
└─ memory/
   └─ memory.txt         → Persists stored state across runs
```

## How It Works

The system follows a multi-server architecture:

```
Client/Agent  ↔  Accounts Server   (balance + transactions)
                  ↘
                   ↘→ Market Server (buy/sell + price updates)
                    ↘
                     → Push Server (real-time notifications)
```

Agents communicate using MCP, which allows LLMs to interact with the servers as tool calls.

## Running the Project

Start the servers in separate terminals:

```
python accounts_server.py
python market_server.py
python push_server.py
python app.py
```

Then open:

- `4_lab4.ipynb` to experiment with basic requests
- `5_lab5.ipynb` for the enhanced agent/UI workflow

## Reset System State

If the system becomes inconsistent or you want to restart clean:

```
python reset.py
```

## Requirements

Install dependencies:

```
pip install -r requirements.txt
```

## License

This project is for educational and demonstration purposes.
