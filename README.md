# Zion Tech Hub: Ad Budget & Growth Analysis

## Overview

This project analyzes real registration data from two cohorts of Zion Tech Hub's Sales, Marketing and Supply Chain Analytics Program, submitted as part of the Zion Tech Hub Data Challenge.

Unlike a typical portfolio project built on a pre-cleaned Kaggle dataset, this analysis works with actual sign up form exports pulled directly from a live business. The data reflects everything that comes with real world collection: inconsistent phone number formats, free text country entries, a missing occupation field in one cohort, duplicate entries, and messy timestamps. None of it was cleaned or prepared in advance. Part of the work here was deciding, and documenting, what counted as noise versus signal.

Zion Tech Hub was preparing to launch its first ever paid advertising campaign, with no prior ad history to draw on. The only available evidence for where to invest that budget was sitting inside this registration data. This project treats that as the real business problem it is, not an academic exercise, but a recommendation a real marketing lead would need to act on.

**The core questions this analysis answers:**
- Where should ad budget be allocated, and to which audiences?
- What should change, beyond advertising, to grow the community and fill the next cohort?

Every recommendation in this project is tied directly to a specific, traceable pattern in the data, not a general assumption.

## Data

- `data/raw/` — original, untouched exports (Cohort 9: 1,092 registrations, Cohort 10: 171 registrations)
- `data/processed/` — cleaned versions used for analysis

## Tools Used

Python, pandas, numpy, matplotlib, seaborn, Jupyter Notebook (VS Code)

## Project Structure

```
zth-ad-budget-analysis/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
├── outputs/
├── README.md
└── requirements.txt
```


## How to Run

1. Clone this repo
2. Create a virtual environment and install dependencies: `pip install -r requirements.txt`
3. Open the notebooks in `notebooks/` in order

## Key Findings

*(To be added as analysis is completed)*

## Recommendations

*(To be added as analysis is completed)*