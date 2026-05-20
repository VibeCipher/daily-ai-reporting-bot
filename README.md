# Daily AI Reporting Bot

Automated daily reporting tool that reads sales data from Excel/CSV, generates charts, and writes an AI-powered executive summary — all inside Google Colab, no server needed.

---

## What it does

- Reads your sales CSV or Excel file directly from Google Drive
- Computes key metrics: daily revenue, region breakdown, product mix, week-on-week trend
- Creates 3 charts: daily revenue bar chart, region breakdown, product mix pie
- Generates a 3-paragraph AI executive summary using Groq (free)
- Saves a clean HTML report back to your Google Drive
- Downloads the report to your computer automatically

**Sample output:**

<img width="667" height="407" alt="image" src="https://github.com/user-attachments/assets/80081b13-a11a-4fe2-8f2c-c6f0147c9af4" />


---

## Quickstart

### Step 1 — Get a free Groq API key
1. Go to [console.groq.com](https://console.groq.com)
2. Sign up (free) → Dashboard → API Keys → Create API Key
3. Copy the key

### Step 2 — Add the key to Colab Secrets
1. Open the notebook in Google Colab
2. Click the **key icon** in the left sidebar (Secrets)
3. Click **+ Add new secret**
4. Name: `GROQ_API_KEY` | Value: paste your key
5. Toggle **Notebook access** → ON

### Step 3 — Upload your data to Google Drive
Put your `sales_data.csv` or `sales_data.xlsx` anywhere in your Google Drive.

### Step 4 — Run the notebook
1. Open `daily_report_bot.py` in [Google Colab](https://colab.research.google.com)
2. Update `FILE_PATH` in Cell 3 to point to your file
3. Run all cells top to bottom
4. The HTML report downloads automatically

---

## File structure

```
daily-ai-reporting-bot/
│
├── daily_report_bot.py       # Main notebook (open this in Colab)
├── requirements.txt          # Python dependencies
├── .gitignore                # Keeps API keys and outputs out of Git
│
└── sample_data/
    └── sales_data.csv        # Sample data to test with
```

---

## Your CSV/Excel format

The bot expects these columns (you can rename them in Cell 3):

| Column | Type | Example |
|---|---|---|
| Date | date | 2024-06-16 |
| Revenue | number | 85000 |
| Units Sold | number | 320 |
| Region | text | South |
| Product | text | Product A |

`Region` and `Product` are optional — charts for those are skipped if not present.

---

## AI provider options

The notebook supports 4 options — switch between them in Cell 7:

| Option | Provider | Cost | Notes |
|---|---|---|---|
| A | Groq | Free | Recommended — fast, generous limits |
| B | Gemini | Free tier | Daily limit ~1500 requests |
| C | OpenRouter | Free models available | Multiple model choices |
| D | Rule-based | No API needed | Always works, no AI required |

---

## Adapting to your data

In **Cell 3**, change these variables to match your file:

```python
FILE_PATH   = '/content/drive/MyDrive/your_file.csv'
DATE_COL    = 'Date'          # your date column name
REVENUE_COL = 'Revenue'       # your revenue column name
UNITS_COL   = 'Units Sold'    # your units column name
REGION_COL  = 'Region'        # your region column name
PRODUCT_COL = 'Product'       # your product column name
```

---

## Running it daily

Since this runs on Colab, the easiest way to automate it is:

1. Save the notebook to Google Drive
2. Each morning, open it and click **Runtime → Run all**
3. The report saves itself to Drive and downloads automatically

For full automation without manual steps, you can migrate to a local Python script and use cron (Linux/Mac) or Task Scheduler (Windows) — see `requirements.txt` for dependencies.

---

## Tech stack

- **Python** — pandas, matplotlib
- **Google Colab** — free cloud runtime, no setup
- **Google Drive** — data source + report storage
- **Groq API** — free LLM inference (Llama 3.3 70B)

---

## Skills demonstrated

- Data ingestion and cleaning with pandas
- Statistical aggregation (daily, weekly, regional)
- Data visualization with matplotlib
- AI/LLM API integration
- Automated HTML report generation
- Google Colab + Drive workflow

---

## License

MIT — free to use, modify, and share.
