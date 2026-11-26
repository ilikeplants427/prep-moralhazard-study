# PrEP and Moral Hazard: Replication and Extension

Applied Econometrics I (ECON 6103), UTSA. By Samantha Morrow, Myranda Menn and Periale Noutaha.

This project replicates Eilam and Delhommer (2021), which asks whether PrEP, the HIV-prevention drug approved in 2012, led to higher rates of other STIs through moral hazard. Using a state-by-year panel (50 states, 2008–2018), it estimates difference-in-differences models with state and year fixed effects (`fixest`) for male and female chlamydia, gonorrhea and syphilis rates. The extension tests whether effects differ by the age of PrEP users and by regional dating-app engagement (Google Trends search interest for "Grindr"), controlling for each state's male same-sex partnership share.

## Main result
The replicated coefficient on the male PrEP rate for chlamydia is 0.414, compared with 0.371 in the original paper. Gonorrhea and syphilis estimates have the same direction and similar size, consistent with the paper's moral hazard finding. Differences likely come from omitted control variables and using the simple difference-in-differences model rather than the paper's triple-difference model.

## Files
| File | What it does |
| --- | --- |
| `prep_replication.qmd` | Main Quarto report: data description, replication tables and figures, extension, references |
| `scripts/00_setup.R` | Installs and loads packages, sets folder paths |
| `scripts/01_clean_data.R` | Loads and stacks the AIDSVu PrEP files, cleans the CDC STI files, merges them, and adds Google Trends data |
| `data/raw/` | Downloaded source files |
| `data/clean/merged_data.csv` | Final merged panel used by the report (550 state-years) |

## How to run
1. Open this folder as a project in RStudio or Posit Cloud.
2. Render `prep_replication.qmd`. It reads `data/clean/merged_data.csv`, so no other step is needed to reproduce the report.
3. `scripts/01_clean_data.R` shows how the raw files were cleaned and merged. The Google Trends step pulls live data with `gtrendsR` and needs an internet connection. The female STI rates and the same-sex partnership share (`data/raw/male_ssp_by_state.csv`) were added to the merged file in a separate step, so running this script overwrites `merged_data.csv` without those columns. Keep a copy of the included file if you run it.

## Data sources
| Data | Source |
| --- | --- |
| Chlamydia, gonorrhea, primary & secondary syphilis, HIV diagnoses (male and female, by state) | CDC NCHHSTP AtlasPlus |
| PrEP users and rates by state | AIDSVu (aidsvu.org) |
| Grindr search interest by state, 2010–2018 | Google Trends, via `gtrendsR` |
| Male same-sex partnership share by state | 2000 U.S. Census microdata, IPUMS USA |

Reference: Eilam, N., & Delhommer, S. (2021). PrEP and Moral Hazard. Working Paper, University of Texas at Austin.
