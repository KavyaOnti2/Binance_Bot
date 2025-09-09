🚀 Binance Futures Testnet Trading Bot

A simplified crypto trading bot built in Python for the Binance Futures Testnet (USDT-M).
Supports Market and Limit orders (required) plus advanced order types like Stop-Limit and a simple TWAP strategy (bonus).

📌 Features

✅ Place Market orders (BUY/SELL)

✅ Place Limit orders with Time-in-Force (GTC, IOC, etc.)

✅ Bonus: Stop-Limit orders (trigger + limit price)

✅ Bonus: TWAP strategy (split order into timed slices)

✅ Command-line interface (CLI) with input validation

✅ Logging of all API requests, responses, and errors (bot.log)

✅ Built for Binance Futures Testnet (safe environment, no real money)

⚙️ Requirements

Python 3.9+

Binance Futures Testnet account (get API key/secret from: Binance Testnet
)

🛠 Setup

Clone repo:

git clone https://github.com/your-username/binance-futures-bot.git
cd binance-futures-bot


Create virtual environment:

python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate


Install dependencies:

pip install -r requirements.txt


Configure API keys (.env file in project root):

BINANCE_API_KEY=your_testnet_key
BINANCE_API_SECRET=your_testnet_secret

▶️ Usage

Check price:

python -m src.cli price BTCUSDT


Place MARKET order:

python -m src.cli market BTCUSDT BUY 0.001


Place LIMIT order:

python -m src.cli limit BTCUSDT SELL 0.001 70000


Stop-Limit (bonus):

python -m src.cli stop-limit BTCUSDT BUY 0.001 65000 65100


TWAP (bonus):

python -m src.cli twap BTCUSDT SELL 0.01 5 2

📂 Project Structure
├── src/
│   ├── binance_client.py   # REST client
│   ├── cli.py              # CLI interface
│   ├── config.py           # Config loader
│   ├── logger_setup.py     # Logging
│   ├── utils.py            # Validation helpers
│   ├── orders/
│   │   ├── market_orders.py
│   │   ├── limit_orders.py
│   │   └── stop_limit.py
│   └── strategies/
│       └── twap.py
├── bot.log                 # Log file (runtime)
├── requirements.txt
├── .env.example
├── README.md
└── report.md

📊 Logs

Every API call (request/response/error) is written to bot.log, for example:

2025-09-08 23:40:10 | INFO | BinanceFuturesREST | REQUEST POST /fapi/v1/order params={'symbol': 'BTCUSDT', ...}
2025-09-08 23:40:11 | INFO | BinanceFuturesREST | RESPONSE status=200 body={...}

🔮 Future Enhancements

WebSocket integration for live trades/positions

Risk management (leverage, stop-loss, take-profit)

Simple UI (e.g., web dashboard or TUI)
