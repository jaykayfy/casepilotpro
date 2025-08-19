
# eCourts Case Manager - Desktop Version

## Requirements
- Python 3.8+
- Internet connection (for sync features, if enabled)
- `streamlit`, `pandas` installed

## Installation
1. Place `ecourts_dashboard.py` in a folder of your choice.
2. Place your `myCases_clean.csv` or raw `myCases.txt` (exported from eCourts mobile app) in the same folder.

## Running
Open a terminal/PowerShell in that folder and run:
```
streamlit run ecourts_dashboard.py
```

## Usage
- Select a hearing date from the date picker.
- Optionally check "Include Tomorrow's Hearings".
- Filtered list will display in the table.
- Download CSV for printing or sharing.
