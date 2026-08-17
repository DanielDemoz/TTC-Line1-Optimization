# TTC Line 1 — Delay Reduction & Scheduling Optimization

Risk-aware scheduling framework for Toronto's Line 1 (Yonge–University) subway that combines delay forecasting with MILP-based train frequency optimization.

> **Topic:** `toronto-transit` — Toronto Transit Commission (TTC) analytics series.

Part of a Toronto transit analytics series: [ttc-predict](https://github.com/DanielDemoz/ttc-predict) | [TTC-Line1-Optimization](https://github.com/DanielDemoz/TTC-Line1-Optimization) | [toronto-transit-sentiment-nlp](https://github.com/DanielDemoz/toronto-transit-sentiment-nlp) | [interactive-transit-dashboard](https://github.com/DanielDemoz/interactive-transit-dashboard)

## Problem

Line 1 is the TTC's busiest corridor, but passenger-related delays (overcrowding, alarm misuse, track entry) reduce reliability and increase operational cost.

## Approach

Analyzed historical delay data from City of Toronto Open Data, forecast hourly disruption risk with Facebook Prophet, and optimized train frequency using mixed-integer linear programming (PuLP). Compared three scheduling strategies, selecting Modified Option 2 as the best cost–reliability balance.

## Results

| Strategy | Avg Delay (min) | Daily Savings |
|----------|-----------------|---------------|
| Option 1 – Min Freq | 4.20 | $47.7k |
| Modified Option 2 | 3.14 | $6.6k |
| Option 3 – Max-Min | 3.00 | $0 |

Modified Option 2 reduced average peak-hour delay to 3.14 minutes while saving approximately $6,600 per day versus baseline scheduling.

## Tech stack

Python, Facebook Prophet, PuLP, pandas, Jupyter notebooks

## How to run

**Recommended (Google Colab):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DanielDemoz/TTC-Line1-Optimization/blob/main/notebooks/Final_Analysis_TTC_line_1%20%281%29.ipynb)

1. Download the [TTC subway delay dataset](https://open.toronto.ca/dataset/ttc-subway-delay-data/) and upload to `/data/`.
2. Run all cells in the notebook.

**Local:** clone the repo, install `requirements.txt`, place the CSV in `data/`, then run `src/forecasting.py` and `src/optimization.py`.

## Screenshot / demo

See `report/final_report.pdf` and notebook outputs for forecast charts and optimized schedules. Project banner: `TTC optimization .png`.
