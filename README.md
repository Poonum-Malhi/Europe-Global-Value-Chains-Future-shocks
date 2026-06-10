# Project 5 — Europe Under Pressure: GVC Position and Reshoring Vulnerability
**Series:** Europe Under Pressure (Part 5 of 6)  
---

## Research Question

> Which EU-27 countries are most exposed to reshoring risk, based on their depth of integration in Global Value Chains (2020)?

---

## Motivation

The COVID-19 pandemic, the Russia-Ukraine war, and rising US-China trade tensions have triggered a global debate about reshoring — the process of bringing supply chains back home. But reshoring is not painless. Countries that are deeply embedded in Global Value Chains (GVCs) face the greatest disruption if international production networks shorten.

This project builds a **Reshoring Vulnerability Index** for all 27 EU member states by combining two dimensions:

1. **GVC depth** — how much of a country's domestic value added flows into global production networks (measured via OECD TiVA forward linkages)
2. **Manufacturing intensity** — the share of GDP from manufacturing (World Bank, 2020)

The core hypothesis: countries that are both deeply embedded in GVCs *and* specialise in manufacturing — not services — face the highest cost if reshoring accelerates.

---

## Papers this builds on

| Paper | Contribution to this project |
|---|---|
| Antràs & Chor (2013) — *Organizing the Global Value Chain*, Econometrica | Framework for upstream/downstream positioning in production networks |
| Autor, Dorn & Hanson (2013) — *The China Syndrome*, American Economic Review | China Shock exposure methodology (used in Parts 1 and 2 of this series) |
| Frey & Osborne (2017) — *The Future of Employment*, Technological Forecasting | Automation risk framework (used in Part 2 of this series) |

This project also draws directly on the research agenda of the supervising professor, whose working paper *The True Cost of Reshoring* (Paris 1) addresses the same policy question from a theoretical and empirical perspective.

---

## Data Sources

| Source | Variable | Year |
|---|---|---|
| OECD TiVA 2023 (FDVA dataset) | Forward linkages — domestic value added embodied in world final demand | 2020 |
| World Bank World Development Indicators | Manufacturing value added (% of GDP) | 2020 |
| World Bank World Development Indicators | GDP in current USD | 2020 |

**Note on year choice:** 2020 is a COVID-affected year. A cleaner baseline would be 2019. This is flagged as a limitation and a priority for Part 6.

---

## Methodology

### Step 1 — GVC depth index
For each EU-27 country, GVC depth is calculated as:

```
GVC depth = Forward Linkage (USD mn) / GDP (USD mn)
```

This normalises by economic size so that Germany's large absolute forward linkage is not confused with a structurally deeper GVC position.

### Step 2 — Reshoring Vulnerability Index
```
Vulnerability (raw) = GVC depth × Manufacturing share of GDP (%)
```

The raw score is then normalised to a 0–100 scale across EU-27 countries:

```
Vulnerability (normalised) = (raw - min) / (max - min) × 100
```

### Step 3 — Visualisation
Two charts are produced:
- **Horizontal bar chart** — all 27 EU countries ranked by vulnerability score, colour-coded by risk tier
- **Bubble chart** — GVC depth (x) vs manufacturing share (y), bubble size proportional to vulnerability score

---

## Key Findings

### Most vulnerable (score > 70)
| Country | Score | Why |
|---|---|---|
| Czechia | 100 | Highest manufacturing share in EU (25% of GDP) + deep GVC integration via German automotive chains |
| Ireland | 89 | Deep pharma and tech GVC integration |
| Slovakia | 87 | Central European manufacturing hub in German/Austrian production networks |
| Hungary | 81 | Similar CEE manufacturing exposure |
| Romania | 81 | Assembly and manufacturing embedded in EU supply chains |
| Slovenia | 79 | Small but deeply integrated manufacturing economy |

### Least vulnerable (score < 25)
| Country | Score | Why |
|---|---|---|
| Cyprus | 0 | GVC integration almost entirely through financial services — not reshoring-relevant |
| Luxembourg | 0.4 | Same: finance-dominated GVC exposure |
| Greece | 18 | Low manufacturing share, services-heavy economy |
| France | 25 | Moderate manufacturing, strong services and luxury goods |

### The Germany result
Germany scores 71 — high but not the highest. It has a large manufacturing base, but its GVC depth relative to GDP is moderate. Crucially, Germany *anchors* GVCs rather than depending on them, which gives it more structural resilience than the Central European countries it supplies.

---

## Limitations

1. **Manufacturing share is sector-level, not GVC-specific** — a country with high manufacturing may produce mostly for domestic consumption, not for export GVCs
2. **2020 is a COVID year** — GVC participation was disrupted. 2019 would be a cleaner baseline
3. **Only forward linkages used** — backward linkages (how much a country depends on *imported* inputs) are equally important for a complete vulnerability picture
4. **No regression analysis** — this is a descriptive index, not a causal estimate. Correlation between the index and actual trade disruption outcomes is not tested here

---

## Connection to the Europe Under Pressure series

| Part | Research Question | Method |
|---|---|---|
| 1 | Did the China Shock raise unemployment in EU-12? | OLS, Autor et al. (2013) replication |
| 2 | Does AI exposure correlate with EU unemployment? | OLS, Frey & Osborne (2017) extension |
| 3–4 | TBA | TBA |
| **5** | **Which EU-27 countries are most exposed to reshoring risk?** | **GVC depth × manufacturing intensity index** |
| 6 (planned) | Does reshoring vulnerability predict post-2020 trade balance shifts? | Panel regression, 2019 baseline |

---

## Files

| File | Description |
|---|---|
| `project5_gvc_reshoring.ipynb` | Full Jupyter notebook with code, explanations and charts |
| `project5_data.csv` | Final dataset: GVC depth, manufacturing share, vulnerability index for EU-27 |
| `OECD_STI_PIE_DSD_TIVA_FDVA_DF_FDVA_1_1____T_W__T__A.csv` | Raw OECD TiVA data (source file) |

---

## How to run

```bash
git clone https://github.com/Poonum-Malhi/europe-under-pressure-gvc-reshoring
cd europe-under-pressure-gvc-reshoring
pip install pandas numpy plotly
jupyter notebook project5_gvc_reshoring.ipynb
```

Place the OECD TiVA CSV in the same folder as the notebook before running.

---

## Author

Poonum Malhi 
