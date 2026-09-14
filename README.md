# Construction Conundrum: Modeling the Impact of the 2008 Financial Crisis on Housing Starts Forecasting

Final project for STAT 5170 (Time Series), University of Virginia — Max Van Zandt and Sami Adam.

## Description

Analyzed 1959–2010 monthly housing starts (HOUST) data (612 observations) using a SARIMA(1,0,1)(1,0,1)[12] model to quantify the impact of the 2008 Financial Crisis structural break on forecasting performance; models trained on post-crisis data (pre-2010) produced prediction intervals capturing observed recovery, while pre-crisis models (pre-2006) systematically overpredicted housing activity. Applied spectral analysis via periodogram smoothing to identify dominant frequency cycles, revealing a shift from 8-year (96-month) to 10.4-year (125-month) dominant periods between training regimes, with low-frequency cyclical behavior contributing more variance than seasonal components across both pre-crisis and post-crisis data splits.

Full writeup, literature review, and results: [`latex/housing_starts_paper.pdf`](latex/housing_starts_paper.pdf).

## Data Sources

- **HOUST** — New Privately-Owned Housing Units Started: Total Units. Federal Reserve Bank of St. Louis (FRED): https://fred.stlouisfed.org/series/HOUST

## Data Dictionary

| Variable | Description | Units | Frequency | Source |
|---|---|---|---|---|
| `HOUST` | New privately-owned residential units on which construction has begun (defined as initiation of excavation for the building's footings) | Thousands of units | Monthly, Jan 1959–Aug 2025 | FRED (HOUST) |

## Reproduction Steps

1. Download `HOUST.csv` from the FRED link above and place it alongside the `.Rmd` files in `analysis/`.
2. Each `.Rmd` file is self-contained (loads its own libraries and data) and can be knit independently:
   - `analysis/max-pre-2006.Rmd` — pre-2006 training regime (SARIMA + spectral analysis)
   - `analysis/sami-pre-2010.Rmd` — pre-2010 training regime (SARIMA + spectral analysis)
   - Required R packages: `tidyverse`, `astsa`, `readr`, `forecast`, `tseries`
3. Figures in `images/` were manually reviewed and copied into the LaTeX source — the analysis notebooks are not wired to auto-export figures with matching filenames.
4. To compile the paper: `latex/housing_starts_paper.tex` compiles with `pdflatex` + `bibtex` (standard two-pass bibliography build). Requires `cvpr.sty` and `ieee_fullname.bst` to be present in the same directory.

## Files

```
├── analysis/
│   ├── max-pre-2006.Rmd       # SARIMA + spectral analysis, pre-2006 training regime
│   └── sami-pre-2010.Rmd      # SARIMA + spectral analysis, pre-2010 training regime
├── images/                    # Figures used in the paper (exported manually from analysis)
├── latex/
│   ├── housing_starts_paper.tex
│   ├── housing_starts_paper.pdf
│   ├── cvpr.sty                # Formatting template (see Acknowledgments)
│   ├── ieee_fullname.bst       # Bibliography style
│   ├── references.bib
│   └── README.md                # Template attribution notes
├── LICENSE
└── README.md
```

## Authorship

- **Sections 4.2–4.3** (pre-2006 SARIMA and spectral analysis): Max Van Zandt
- **Section 4.4** (pre-2010 SARIMA and spectral analysis): Sami Adam
- Introduction, literature review, and final remarks: joint work

## Acknowledgments

The LaTeX formatting is based on the CVPR paper template (originally by Paolo Ienne and Andrew Fitzgibbon; modernized by Ming-Ming Cheng — https://github.com/MCG-NKU/CVPR_Template — and further updated by Stefan Roth). It is reused here solely for its two-column academic layout; this is not a CVPR submission and is not affiliated with the conference. The bibliography style (`ieee_fullname.bst`) is a modification of the standard IEEE style by Jonathan Barron, adapted to print full author first names.

## License

BSD 3-Clause — see [LICENSE](LICENSE) for details.
