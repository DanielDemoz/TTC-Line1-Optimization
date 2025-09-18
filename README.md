📖 Project Overview

Toronto’s Line 1 (Yonge–University) subway is the busiest corridor in the TTC network, serving hundreds of thousands of riders daily. However, frequent delays — especially passenger-related incidents such as platform overcrowding, misuse of alarms, and unauthorized track entry — reduce reliability and increase operational costs.

This project develops a risk-aware, data-driven scheduling framework that combines:

📊 Historical Delay Data Analysis (City of Toronto Open Data)

🔮 Time-Series Risk Forecasting using Facebook Prophet

📐 Mixed-Integer Linear Programming (MILP) optimization using PuLP in Python

Our strategy, called Modified Option 2, dynamically adjusts train frequency in response to forecasted delay risk. Results show:

🚇 Average delay reduced to 3.14 minutes during peak hours

💰 Operational savings of ~$6,600 per day

⚖️ Balanced trade-off between cost control and service quality

🎯 Objectives

Delay Attribution: Identify and classify major passenger-related delay types.

Risk Forecasting: Predict hourly disruption risk using Prophet.

Schedule Optimization: Use MILP to dynamically adjust train frequencies.

Cost Control: Minimize operations cost while maintaining service standards.

Scalability: Provide a framework adaptable for future TTC expansion.

🛠️ Methodology

Data Analysis

Source: TTC Subway Delay Data (2024)

Focused on passenger-related delay codes (SUDP, MUPAA, PUMST, MUATC, MUO).

Risk Forecasting with Prophet

Hourly disruption risk scores built from historical data.

High-risk hours defined as risk score > 250.

MILP Optimization (PuLP)

Decision variable: number of trains per hour (25–35 tph).

Objective: balance cost vs. risk exposure.

Constraints: fleet size (65 trains), passenger capacity, delay threshold (≤ 3 min).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/TTC-Line1-Optimization/blob/main/notebooks/analysis.ipynb)


Evaluation of Strategies

Option 1 (Min Freq): Cheapest but highest delays.

Option 3 (Max-Min Freq): Lowest delays but highest cost.

Modified Option 2 (Dynamic Scheduling): Best balance.
