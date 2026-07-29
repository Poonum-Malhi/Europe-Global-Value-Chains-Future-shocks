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

## Visualisations
| Figure | Description | Link |
|--------|-------------|------|
| Reshoring Vulnerability Index | EU-27 ranked + bubble chart | [🗺️ View Interactive Chart](https://poonum-malhi.github.io/Europe-Global-Value-Chains-Future-shocks/fig_project5_reshoring.html) |

## Europe Under Pressure — Full Series
| Project | Question | Key Result |
|---------|----------|------------|
| [Part 1 — China Shock](https://github.com/Poonum-Malhi/china-shock-europe) | Did Chinese imports raise EU unemployment? | p=0.3 — No. Industrial upgrading offset the shock |
| [Part 2 — AI Shock](https://github.com/Poonum-Malhi/Europe-under-pressure-first-China-now-AI) | Does AI exposure raise EU unemployment? | p=0.518 — Not yet significant |
| [Part 3 — Climate Shock](https://github.com/Poonum-Malhi/climate-shock-europe) | Does CBAM exposure raise EU unemployment? | p=0.009 — Significant, but negative direction |
| [Part 4 — Housing Shock](https://github.com/Poonum-Malhi/Housing-Affordability-Shock-Index) | Does housing unaffordability raise unemployment? | p=0.66 — No. Labour markets resilient |
| **Part 5 — GVC & Reshoring** (this repo) | **Which EU countries are most reshoring-exposed?** | **Czechia, Ireland, Slovakia most vulnerable** |
| [Part 6 - GVC & Trade Balance](https://github.com/Poonum-Malhi/GVC-Reshoring-Trade-Balance-EU/blob/main/README.md) | Does reshoring vulnerability predict post-2020 trade balance shifts? | Panel regression, 2019 baseline |

## Root Paper
Antràs, P., & Chor, D. (2013). Organizing the Global Value Chain. *Econometrica*, 81(6), 2127–2204.

---

Thank you so much for being part of my project series! 

*Part of the Europe Under Pressure research series, exploring structural economic shocks across the EU.*

---------------------------
## Addendum — Panel Extension Test (20-28 July 2026)

Following feedback from Guillaume Gaulier (CEPII), who noted that the GVC-depth-vs-manufacturing relationship might differ for small economies (while flagging that a single-year, small-N subsample would lack robustness), this section extends the original 2020 cross-section into a panel to test the hypothesis properly.

Motivation
The original analysis (above) found no significant relationship between GVC depth and manufacturing intensity restricted to small economies (N=14, p=0.46) — consistent with the robustness concern raised. This addendum re-tests the same hypothesis using a full country-year panel to see whether a larger sample changes the result.

Data and Methodology
Sample: 26 EU countries, 2015–2023 (234 country-year observations)
Proxy note: OECD TiVA forward-linkage data (used for the original 2020 GVC Depth measure above) is not readily available as a multi-year panel. This extension uses Trade Openness — (Exports + Imports) / GDP, built from World Bank WDI indicators NE.EXP.GNFS.ZS and NE.IMP.GNFS.ZS — as a proxy for GVC integration. This is a broader measure of trade integration, not a direct substitute for GVC forward linkages, and this substitution is an explicit limitation of this extension.
Small vs. large split: countries are classified as "small" or "large" by GDP, split at the median within each year (so classification can shift slightly year to year as relative GDP changes).
Model: Pooled OLS of Manufacturing (% of GDP) on Trade Openness, with standard errors clustered by country, estimated separately for the small and large subsamples.

Results

Subsample	β (Trade Openness → Manufacturing)	p-value	N
Full panel	−0.005	0.857	234
Small economies	−0.027	0.018	117
Large economies	+0.073	0.067	117

Interpretation
With the larger panel, Gaulier's intuition holds up statistically: in small economies, higher trade openness is associated with a significantly lower manufacturing share (p < 0.05). Large economies show the opposite sign (higher openness associated with higher manufacturing share), though only at the 10% level. The full-sample regression shows no relationship at all — the two opposing subsample patterns cancel out, which is why the original pooled 2020 cross-section missed this.

An earlier version of this panel (2015–2022, 208 observations) found the same pattern at p = 0.029 for small economies. Extending the window by one further year (2023), using freshly pulled exports, imports, GDP, and manufacturing data, strengthens the result to p = 0.018 rather than weakening it — evidence the finding is not an artefact of the specific 2015–2022 window originally chosen.

A plausible reading: small open economies (Cyprus, Malta, Luxembourg, the Baltics) that increase trade integration tend to specialize further into services and finance rather than manufacturing, while large economies (Germany, France) use greater trade openness to reinforce an already-large manufacturing base that benefits from scale. This is offered as a descriptive pattern, not a causal claim — the panel does not include country or time fixed effects, and trade openness is an imperfect proxy for the original GVC-depth measure.

### Limitations

- Trade openness substitutes for GVC depth due to data availability; the two are correlated but not identical
- No fixed effects — this is a pooled regression, not a full two-way fixed-effects panel
- Small/large classification is a median split, not an established small-open-economy definition
- 2020 (COVID year) is included in the panel and may add noise

### Acknowledgment

Thanks to Guillaume Gaulier (CEPII / Banque de France) for the methodological suggestion that motivated this extension.

