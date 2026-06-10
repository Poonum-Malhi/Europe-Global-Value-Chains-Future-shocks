# GVC Position and Reshoring Vulnerability
### Part 5 of the *Europe Under Pressure* Series
Mapping EU-27 countries' exposure to reshoring risk using OECD Trade in Value Added (TiVA) data and a composite Reshoring Vulnerability Index.

---

## Research Question
Which EU-27 countries are most exposed to reshoring risk, based on their position in Global Value Chains (2020)?

## Key Finding
Central European manufacturing economies — **Czechia (100), Ireland (89), Slovakia (87), Hungary (81)** — are most vulnerable to supply chain shortening.  
Countries with GVC integration through **services** (Luxembourg, Cyprus) are structurally insulated from reshoring pressure.

> This is consistent with the recurring pattern across the series: Europe's exposure to structural shocks is **heterogeneous** and driven by industrial structure, not geography alone.

## Methodology
A **Reshoring Vulnerability Index (RVI)** is constructed for all 27 EU member states:

$$\text{RVI}_i = \text{GVC Depth}_i \times \text{Manufacturing Share}_i$$

$$\text{GVC Depth}_i = \frac{\text{Forward Linkage (USD mn)}_i}{\text{GDP (USD mn)}_i}$$

Normalised to 0–100 across EU-27.  
**Root paper:** Antràs & Chor (2013) — *Organizing the Global Value Chain*, Econometrica.

## Results
| Metric | Value |
|--------|-------|
| Most vulnerable country | Czechia (RVI = 100) |
| Least vulnerable country | Cyprus (RVI = 0) |
| Countries with RVI > 70 | 6 (Czechia, Ireland, Slovakia, Hungary, Romania, Slovenia) |
| EU-27 average RVI | 52.4 |
| Data year | 2020 (OECD TiVA) |

Note: No regression is run in this project — the RVI is a **descriptive index**, not a causal estimate. Regression analysis is planned for Part 6.

## Data Sources
- **OECD TiVA 2023** (FDVA dataset) — Forward linkages, domestic value added in world final demand
- **World Bank WDI** — Manufacturing value added (% of GDP), GDP current USD, 2020

## Tools
`Python` `pandas` `numpy` `plotly` `Jupyter`

## Limitations
1. Manufacturing share is sector-level, not GVC-specific
2. 2020 is a COVID-affected year — 2019 would be a cleaner baseline
3. Only forward linkages used — backward linkages omitted
4. Descriptive index only — no causal identification

## Europe Under Pressure — Full Series
| Project | Question | Key Result |
|---------|----------|------------|
| [Part 1 — China Shock](https://github.com/Poonum-Malhi/china-shock-europe) | Did Chinese imports raise EU unemployment? | p=0.3 — No. Industrial upgrading offset the shock |
| [Part 2 — AI Shock](https://github.com/Poonum-Malhi/Europe-under-pressure-first-China-now-AI) | Does AI exposure raise EU unemployment? | p=0.518 — Not yet significant |
| [Part 3 — Climate Shock](https://github.com/Poonum-Malhi/climate-shock-europe) | Does CBAM exposure raise EU unemployment? | p=0.009 — Significant, but negative direction |
| [Part 4 — Housing Shock](https://github.com/Poonum-Malhi/Housing-Affordability-Shock-Index) | Does housing unaffordability raise unemployment? | p=0.66 — No. Labour markets resilient |
| **Part 5 — GVC & Reshoring** (this repo) | **Which EU countries are most reshoring-exposed?** | **Czechia, Ireland, Slovakia most vulnerable** |
| Part 6 (planned) | Does reshoring vulnerability predict post-2020 trade balance shifts? | Panel regression, 2019 baseline |

## Root Paper
Antràs, P., & Chor, D. (2013). Organizing the Global Value Chain. *Econometrica*, 81(6), 2127–2204.

---
*Part of the Europe Under Pressure research series — exploring structural economic shocks across the EU.*
