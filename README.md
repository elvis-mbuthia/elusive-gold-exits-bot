# Automated Forex & Gold Trading Bot (XAUUSD)

A Python-based automated trading bot for forex and gold (XAUUSD) markets, built on the MetaTrader 5 platform with a custom ratcheting profit-lock mechanism.

## 📈 About the Project

This bot connects directly to MetaTrader 5 to execute and manage trades on XAUUSD and other forex pairs. Unlike typical bots that rely on broker-side stop-loss and take-profit orders, this bot manages all trade logic programmatically — giving more control and avoiding broker-side slippage on SL/TP execution.

## ✨ Features

- 🤖 **Automated trade execution** via MetaTrader 5 Python API
- 🔒 **Ratcheting profit-lock mechanism** — locks in profits as price moves in your favour, with no broker-side SL/TP
- 📊 **Multi-trade tracking** — monitors multiple open positions simultaneously
- 🖥️ **Live terminal dashboard** — real-time display of open trades, profit/loss, and lock levels
- 💹 **XAUUSD focused** — optimised for gold trading with forex pair support
- 📉 **Raw bitmask filling modes** — handles MT5 broker filling mode compatibility

## 🛠️ Tech Stack

| Component | Tool |
|-----------|------|
| Language | Python |
| Trading Platform | MetaTrader 5 |
| MT5 Integration | MetaTrader5 Python package |
| Market Data | yfinance (supplementary data) |
| Interface | Live terminal dashboard |

## 📁 Project Structure

```
trading-bot/
├── main.py              # Entry point and main trading loop
├── bot.py               # Core trade logic and ratchet mechanism
├── mt5_connector.py     # MetaTrader 5 connection and order management
├── dashboard.py         # Live terminal display
├── config.py            # Settings (symbol, lot size, ratchet levels)
└── requirements.txt     # Python dependencies
```

## 🚀 Getting Started

### Prerequisites

- Python 3.10+
- MetaTrader 5 desktop app installed and logged into a broker account
- A broker that supports the MetaTrader 5 platform and XAUUSD trading

### Installation

```bash
git clone https://github.com/YOUR_USERNAME/xauusd-trading-bot.git
cd xauusd-trading-bot
pip install -r requirements.txt
```

### Configuration

Edit `config.py` to set your trading parameters:

```python
SYMBOL = "XAUUSD"
LOT_SIZE = 0.01          # Start small while testing
RATCHET_STEP = 10        # Pips to move lock level up
INITIAL_LOCK = 20        # Pips profit before first lock
```

### Usage

```bash
python main.py
```

Make sure MetaTrader 5 is running and logged in before starting the bot.

## ⚠️ Disclaimer

This tool is for **educational purposes**. Trading forex and gold carries significant financial risk. Always test on a **demo account** before using real funds. Past performance does not guarantee future results.

## 📌 Notes

- The ratcheting mechanism tracks profit programmatically — no SL/TP is placed on the broker side
- MT5 filling mode compatibility is handled via raw bitmask values to work across different brokers
- Supports tracking of multiple simultaneous open trades independently
