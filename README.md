# Stocks-ticker-for-Raspberry-Pi-SenseHAT

# README: Sense HAT Stock Ticker

This Python script displays the current price of IWDA.AS (iShares Core MSCI World UCITS ETF) on a Raspberry Pi Sense HAT. It scrolls the EUR price and shows a simple bar chart based on price movement (green for uptrend, red for downtrend). Updates every 4 minutes.

## Software Requirements
- Python 3 (pre-installed on Raspberry Pi OS).
- Internet connection for Yahoo Finance API.

## Installation
1. **Enable I2C** (one-time):
   ```
   sudo raspi-config
   ```
   - Select "Interface Options" > "I2C" > Enable.
   - Reboot: `sudo reboot`.

2. **Install packages**:
   ```
   sudo apt update
   sudo apt install python3-sense-hat python3-pip
   pip3 install yfinance
   ```

3. **Save script**:
   Copy `aktie.py` content into a file: `nano aktie.py` and save.

## Running
```
python3 aktie.py
```
- Runs indefinitely; stop with `Ctrl+C`.
- First run fetches data immediately, then every 4 minutes (240 seconds).

## Configuration
- **Change ticker**: Edit line `TICKER = "IWDA.AS"` (e.g., "AAPL" or "DAX"). Use valid Yahoo Finance symbols.
- **Update interval**: `UPDATE_INTERVAL = 240` (seconds; min 60 recommended due to API limits).
- **Currency**: Already set to "EUR"; price fetched directly from yfinance. Replace EUR with $ for US-dollar.

| Parameter | Default | Description |
|-----------|---------|-------------|
| TICKER | "IWDA.AS" | Yahoo symbol to change [1] |
| UPDATE_INTERVAL | 240s | Update frequency [1] |
