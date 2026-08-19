# Data and Statistical Reasoning Project: The AG Share of New Company Registrations in Basel-Landschaft, 2017 vs 2025

**GitHub repository:** https://github.com/mauroreverberi/conduct-a-statistical-analysis-using-python
(all commits and the `develop` branch as well as the `main` branch are visible there)

## Project Description
I analyze new company registrations in the Swiss canton of Basel-Landschaft and ask one question. Did the share of stock corporations (Aktiengesellschaft, AG) among new company registrations change between 2017 and 2025?

The question connects to my first capstone project, where I analyzed the Swiss entries of the global LEI dataset and found that the AG / SA is the largest legal form group in that register. The two projects use different datasets and different populations, so their percentages must not be compared directly. Project 1 looked at the stock of LEI-registered entities, this project looks at individual new registrations published in the SHAB for one canton.

## What Was Built
- A Jupyter notebook (`analysis.ipynb`) with the whole analysis: loading
  the frozen dataset, data checks and cleaning, descriptive statistics,
  three visual models, a simulation-based hypothesis test with an
  analytical chi-square cross-check and a short summary.
- A written report (`Statistical_Analysis_Report.pdf`) that explains the
  question, methods, results and limitations for technical and
  non-technical readers.
- A reproducibility file (`requirements.txt`), generated with `pip freeze`
  inside the project's own virtual environment.

## Dataset
"Firmenmutationen nach Rechtsform und Gemeinde" (company mutations by legal
form and municipality, published since February 2016), from Open Government
Data Kanton Basel-Landschaft:
https://data.bl.ch/explore/dataset/12460/

The frozen snapshot `firmenmutationen.csv` (28,992 rows x 11 columns) is
included in this repository. I downloaded it on 2026-08-13 through the
direct CSV export:
https://data.bl.ch/explore/dataset/12460/download/?format=csv

SHA-256 of the frozen file:
`7583eb3569ba895e479571b09465372ad9809f62681a3f3f0ececcf3c03bfc41`

Note: the online dataset is updated continuously, so a fresh download can
give different numbers than the snapshot used in this project. The notebook
therefore reads only the frozen local copy, which keeps every result
reproducible.

## Main Results
Between 2017 and 2025 the yearly number of new registrations grew from
1,156 to 1,444, while the AG share fell from 16.00% to 12.74%. The
absolute number of AG registrations stayed almost constant (185 vs 184).
A simulation-based two-sided test (100,000 simulations, seed 42) rejects
the hypothesis of an equal AG share in both years, with p = 0.0182 at
alpha = 0.05, and a simulated 95% confidence interval puts the difference
between -5.98 and -0.54 percentage points. A descriptive check of the
inner year pairs (2018 vs 2024, 2019 vs 2023) shows the same downward
direction. The comparison is observational, so the data does not tell
me why the share fell.

## How to Run the Project
1. Clone this repository.
2. Create and activate a virtual environment (Python 3.12 or newer, tested with 3.14):
   ```
   python -m venv .venv
   source .venv/bin/activate   # on Windows: .venv\Scripts\activate
   ```
3. Install the dependencies:
   ```
   pip install -r requirements.txt
   ```
4. Start Jupyter:
   ```
   jupyter notebook
   ```
5. Open `analysis.ipynb` and run all cells
   (Kernel > Restart Kernel and Run All Cells).

The dataset `firmenmutationen.csv` is already part of the repository, so
no download is needed to run the notebook. The notebook uses relative
paths and a fixed random seed (42), so a full run reproduces every number
in the report.

## Dependencies
`requirements.txt` was created inside the project's own virtual
environment with:
```
pip freeze > requirements.txt
```

## Connection to Future AI Work
I stay in the same domain as Project 1, official company register data.
The habits from this project (a frozen snapshot, stated hypotheses,
quantified uncertainty, a fixed seed) are exactly what the next projects
need when I train and evaluate machine learning models on company data.
For the planned entity matching work, the legal form is one of the fields
that helps to decide whether two records describe the same company, and
this project showed me that its distribution shifts over time even within
one canton, which a matching model has to tolerate.
