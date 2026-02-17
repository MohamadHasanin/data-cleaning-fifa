# FIFA World Cup Data Cleaning

Data cleaning project across three FIFA World Cup datasets covering every tournament, match, and squad record from 1930 to 2014.

## Datasets

| Dataset               | Rows   | Focus                |
|-----------------------|--------|----------------------|
| `WorldCups.csv`       | 20     | Tournament summaries |
| `WorldCupMatches.csv` | 4,572  | Match-level records  |
| `WorldCupPlayers.csv` | 37,784 | Player participation |

## What's Done

**WorldCups**
- No nulls or duplicates found
- Dtype optimisation (float64 → uint8/uint16/uint32)
- Deprecated country names standardised with documented rationale

**WorldCupMatches** (most complex)
- 128 fully null rows dropped, 16 duplicate matches removed
- 1 missing attendance researched externally (Transfermarkt) and filled
- Datetime parsed from inconsistent strings; Stage values unified across eras
- Win Conditions column rebuilt with consistent format across all 4,444 valid matches
- Cross-validation: Year vs parsed Datetime — 0 mismatches

**WorldCupPlayers**
- 736 duplicates verified as complete row-level copies before removal
- Nulls in Position and Event filled with domain-appropriate values
- Position notation standardised to 4 categories

## Project Structure

```
fifa-world-cup-data-cleaning/
├── data/
│   ├── WorldCups.csv
│   ├── WorldCupMatches.csv
│   ├── WorldCupPlayers.csv
│   └── generated/
│       ├── WorldCups_Clean.csv
│       ├── WorldCupsMatches_Clean.csv
│       └── WorldCupsPlayers_Clean.csv
├── notebooks/
│   ├── data-cleaning-fifa_WorldCups.ipynb
│   ├── data-cleaning-fifa_WorldCupMatches.ipynb
│   └── data-cleaning-fifa_WorldCupsPlayers.ipynb
├── scripts/
│   └── fix_worldcup_players_encoding.py
└── README.md
```

## Setup

```bash
pip install pandas numpy jupyter
```

Then open notebooks in this order:
1. `WorldCups` — good starting point, simplest dataset
2. `WorldCupPlayers` — moderate complexity
3. `WorldCupMatches` — most involved, tackles encoding, datetime, and win condition logic

## Stack

Python · pandas · numpy · re
