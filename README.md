# 📈 Ticker Kit

*A plug-and-play stock data pipeline + dashboard template.*
Clone the repo, bring your own [Polygon.io](https://polygon.io/) API key, and spin up a full analytics pipeline with **React + Plotly.js** dashboards.

---

## ⚡ What is Ticker Kit?

Ticker Kit is a **developer-friendly template** for working with market data. It’s designed as a learning + portfolio project, not a trading system. The goal is to give you a ready-to-go scaffold for:

- **Data Pipeline** → Bronze (raw JSON) → Silver (clean Parquet) → Gold (features in Delta/SQL).
- **Backend** → FastAPI endpoints to serve clean data.
- **Frontend** → React + Plotly.js dashboards with charts, heatmaps, and comparisons.
- **Demo Mode** → Ships with [yfinance](https://pypi.org/project/yfinance/) data so you can run dashboards instantly without a Polygon account.

---

## 🔑 Bring Your Own API Key

To use **live Polygon data**, you must provide your own API key.

1. Get a free or paid key from [Polygon.io](https://polygon.io).
2. Copy `.env.example` → `.env` and add your key:

```bash
POLYGON_API_KEY=your_key_here
```

3. Choose your tickers in the pipeline config.
4. Run the pipeline to ingest & transform your own data.

> ⚠️ **Important:** Polygon data is licensed to the account holder. You **cannot redistribute** Polygon data or include it in repos/demos. Each user must use their **own API key** to ingest data.

---

## 🎮 Demo Mode (Safe & Shareable)

Because Polygon data can’t be redistributed, Ticker Kit ships with **demo datasets** built using [yfinance](https://pypi.org/project/yfinance/).

- Demo tickers: `AAPL`, `MSFT`
- Data range: 2 years of daily OHLCV
- Available out of the box under `data/demo/`

This allows the **frontend dashboard** to run instantly after cloning.

---

## 🛠 Project Structure

```
ticker_kit/
│
├── data/                     # Storage
│   ├── demo/                 # yfinance demo data (ships with repo)
│   ├── bronze/               # raw Polygon dumps (user-owned)
│   ├── silver/               # cleaned data
│   └── gold/                 # aggregated features
│
├── pipeline/                 # ETL logic
│   ├── client_polygon.py     # Polygon ingestion (requires API key)
│   ├── client_yfinance.py    # Demo ingestion
│   ├── ingest.py             # Bronze ingestion
│   ├── transform.py          # Bronze → Silver
│   └── aggregate.py          # Silver → Gold
│
├── backend/                  # FastAPI service
│   ├── main.py
│   ├── routers/
│   │   ├── tickers.py        # Live endpoints
│   │   └── demo.py           # Demo endpoints
│
├── frontend/                 # React + Plotly.js dashboard
│   ├── src/
│   │   ├── pages/
│   │   ├── components/
│   │   └── api/
│   └── package.json
│
└── notebooks/                # EDA & experiments
```

---

## 🚀 Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/your-username/ticker_kit.git
cd ticker_kit
```

### 2. Run Demo Mode
```bash
cd frontend
npm install
npm run dev
```
Visit `http://localhost:5173` → you’ll see demo dashboards powered by yfinance.

### 3. Run Live Mode
1. Add your Polygon API key to `.env`.
2. Ingest data:
   ```bash
   python -m pipeline.ingest
   python -m pipeline.transform
   python -m pipeline.aggregate
   ```
3. Start backend:
   ```bash
   uvicorn backend.main:app --reload
   ```
4. Switch frontend to live API mode and restart.

---

## 📊 Features

- Clone-and-run template → instant dashboards
- Medallion architecture → Bronze → Silver → Gold
- FastAPI backend + React/Plotly frontend
- Demo mode with yfinance (safe to share)
- Live mode with Polygon (BYO key, cannot redistribute data)

---

## 🧭 Roadmap

- [ ] Expand demo data to multiple sectors (finance, energy, healthcare)
- [ ] Add correlation heatmaps & rolling volatility
- [ ] Portfolio watchlist view
- [ ] Deployment via Docker Compose

---

## ⚖️ License & Data Disclaimer

- Code is MIT licensed.
- Demo datasets (yfinance) are included for testing and learning.
- **Polygon data is licensed to the individual account holder. You must use your own API key. Redistribution of Polygon data is not allowed.**

