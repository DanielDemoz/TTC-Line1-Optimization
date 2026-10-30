# TTC Line 1 Scheduling Optimization

Can Line 1 (Yonge–University) trains be scheduled to follow hourly delay risk, and what would that save?

**Case study page:** https://danieldemoz.github.io/TTC-Line1-Optimization/
**Status:** completed study in a Jupyter notebook. A planning exercise, not a TTC schedule.

Part of a Toronto transit series: [ttc-predict](https://github.com/DanielDemoz/ttc-predict) | [TTC-Line1-Optimization](https://github.com/DanielDemoz/TTC-Line1-Optimization) | [toronto-transit-sentiment-nlp](https://github.com/DanielDemoz/toronto-transit-sentiment-nlp) | [interactive-transit-dashboard](https://github.com/DanielDemoz/interactive-transit-dashboard)

## Approach

- 14,142 Line 1 delay records from 2024 (City of Toronto Open Data), in `Data/`.
- Five delay causes are weighted into an hourly "risk pressure" score.
- Linear programming (PuLP) chooses trains per hour (25 to 35) from 6 am to midnight, under a fleet limit.
- Three strategies are compared with running 35 trains per hour all day.

## Results (one service day)

| Strategy | Train-hours | Cost | Saved | Modelled avg delay (min) |
|---|---|---|---|---|
| Baseline: 35 tph all day | 630 | $166,950 | – | 3.00 |
| Option 1: lowest cost | 450 | $119,250 | $47,700 | 4.20 |
| **Option 2: risk-weighted (chosen)** | **605** | **$160,325** | **$6,625** | **3.14** |
| Option 3: highest minimum | 630 | $166,950 | $0 | 3.00 |

**Honest reading:** Option 2 does not lower delay compared with maximum service. It keeps high-risk hours at full service and saves about $6,600 a day in quieter hours, for a small rise in modelled delay.

## Assumptions

- Delay per hour = 105 / trains per hour. This is assumed, not fitted to the data.
- Cost is about $265 per train-hour.
- Risk weights for the five causes (1.1 to 1.5) were set by judgment.

## Responsible AI, following the Reliable AI Adoption Framework

1. **Business problem:** put scarce train service where delay risk is highest, and know what it costs.
2. **Data readiness:** 2024 Line 1 delay records, City of Toronto Open Data. Incident counts, not measured travel times.
3. **Governance and risk:** service cuts affect riders. Savings must be weighed against who waits longer, and when.
4. **Technology and tools:** linear programming makes the trade-off explicit and repeatable.
5. **People and adoption:** planners choose between options. The model shows the cost and modelled delay of each.
6. **Outcomes and monitoring:** after any change, compare real delays by hour with the modelled values and revisit the assumptions.

## How to run

Open the notebook in Google Colab or Jupyter, install `requirements.txt`, and point the data path at the CSV in `Data/`.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DanielDemoz/TTC-Line1-Optimization/blob/main/notebooks/Final_Analysis_TTC_line_1%20%281%29.ipynb)

Slides: `report/TTC Line 1 Optimization PPT.pptx`. Charts: `results/`.

## Project history

The earlier README said the project forecast risk with Prophet and "reduced" delay to 3.14 minutes, and it pointed to scripts and a PDF that are not in the repository. The notebook does not use Prophet, and 3.14 minutes is slightly above the 3.00-minute baseline. The README was corrected in October 2026.

## Tech stack

Python, pandas, PuLP, matplotlib, Jupyter.
