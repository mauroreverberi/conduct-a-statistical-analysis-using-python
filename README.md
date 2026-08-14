# Data and Statistical Reasoning Project: The AG Share of New Company Registrations in Basel-Landschaft, 2017 vs 2025

**GitHub repository:** https://github.com/mauroreverberi/conduct-a-statistical-analysis-using-python
(all commits and the `develop` branch as well as the `main` branch are visible there)

## Project Description
I analyze new company registrations in the Swiss canton of Basel-Landschaft and ask one question. Did the share of stock corporations (Aktiengesellschaft, AG) among new company registrations change between 2017 and 2025?

The question connects to my first capstone project, where I analyzed the Swiss entries of the global LEI dataset and found that the AG / SA is the largest legal form group in that register. The two projects use different datasets and different populations, so their percentages must not be compared directly. Project 1 looked at the stock of LEI-registered entities, this project looks at single new registrations published in the SHAB for one canton.

## Dataset
"Firmenmutationen nach Rechtsform und Gemeinde" (company mutations by legal
form and municipality, published since February 2016), from Open Government
Data Kanton Basel-Landschaft:
https://data.bl.ch/explore/dataset/12460/

The frozen snapshot `firmenmutationen.csv` (28,992 rows x 11 columns) is
included in this repository. I downloaded it on 2026-08-13 through the
direct CSV export:
https://data.bl.ch/explore/dataset/12460/download/?format=csv

Note: the online dataset is updated continuously, so a fresh download can
give different numbers than the snapshot used in this project. The notebook
therefore reads only the frozen local copy, which keeps every result
reproducible.