# eCourts PC Dashboard (Desktop Case Manager)

This project gives you a **PC-based case dashboard** that pulls case data from an eCourts-compatible API and exports:
- A filterable **Excel dashboard** (`dashboard.xlsx`)
- An **iCalendar** file of upcoming hearings (`upcoming_hearings.ics`) you can import into Google/Outlook Calendar

> ⚠️ Default data source is a third-party *mirror-style* E‑Courts India API (`https://eciapi.akshit.me`) which exposes case details by CNR and advocate.
> You can switch to official endpoints when available by editing `config.yaml`.

## Quick Start (Windows/macOS/Linux)

1. Install Python 3.9+
2. Open a terminal in this folder and run:
   ```bash
   pip install -r requirements.txt
   python ecourts_pc_dashboard.py
   ```
3. Open `dashboard.xlsx` (refresh it anytime by re-running the script).
4. Import `upcoming_hearings.ics` into your calendar (Google/Outlook).

## Files You Edit

- `cases.csv` → your matter list (either **CNR** per row, or an **Advocate Search** row like `alias=Advocate Search: YOUR NAME` to pull all your cases).
- `config.yaml` → base URL, API key (if any), timezone, reminder minutes, etc.

## Adapters / Data Sources

- **CNR List:** For rows with a `cnr` value, the script calls `{base_url}/cases/cnr/<CNR>`.
- **Advocate Search:** For rows with `alias` like `Advocate Search: JAY SINGH`, the script searches by advocate and merges new cases into your dashboard.

### Swapping to Official Endpoints

If/when you have official endpoints, set `base_url` in `config.yaml` and optionally add headers (API key) in the code block marked **CONFIGURABLE HEADERS**.

## Output

- **Excel:** Sheets -> `Cases`, `Hearings`, `Orders`, `SyncLog`
- **ICS:** Future hearings within `calendar_days_ahead` with reminders (default 120 minutes)

## Automation (Windows)

Use **Task Scheduler** to run daily at 06:30:
```
Program/script: python
Add arguments: ecourts_pc_dashboard.py
Start in: <this folder>
```

## Disclaimer

Use responsibly and respect the terms of use of your data source. This tool is designed to put **your cases + public case metadata** into a private, lawyer-centric PC dashboard.
