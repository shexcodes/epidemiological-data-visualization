# Data Visualization Projects

![Python](https://img.shields.io/badge/Python-pandas%20%7C%20numpy%20%7C%20matplotlib-3776AB?logo=python&logoColor=white)
![R](https://img.shields.io/badge/R-tidyverse%20%7C%20ggplot2-276DC3?logo=r&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

Coursework for **Data Visualization (LSI-M-2, SS22)** in the M.Sc. Life Science
Informatics programme at the Deggendorf Institute of Technology. The repository
contains two self-contained projects:

- **[`r-measles-analysis/`](r-measles-analysis/)** — an R / `ggplot2` analysis
  of U.S. measles incidence over time and its relationship to vaccination,
  using the [Project Tycho](https://www.tycho.pitt.edu) surveillance dataset.
- **[`python-data-visualization/`](python-data-visualization/)** — Python
  (`matplotlib`) recreations of several figures from artificial genomics data
  (RNA-binding-protein signals, annotation tracks, and positional k-mer counts).

## Repository structure

```
Data-Visualization-Projects/
├── README.md
├── LICENSE
├── .gitignore
├── requirements.txt                     # Python dependencies
│
├── r-measles-analysis/                  # Project Part 1 (R)
│   ├── measles_analysis.Rmd             # the analysis (knit to HTML)
│   ├── data/                            # place ProjectTycho CSV here (not committed)
│   ├── figures/                         # generated on knit
│   └── slides/
│       └── measles_trend_analysis_slides.pptx
│
└── python-data-visualization/           # Project Part 2 (Python)
    ├── data_visualization_part2.ipynb   # the notebook
    ├── data/                            # place course CSV/TXT files here (not committed)
    └── figures/                         # generated when the notebook runs
```

Input data is intentionally **not** committed: the Project Tycho dataset is
large and externally licensed, and the Part 2 files are course-provided. Each
`data/` folder has a `README.md` listing exactly which files to drop in and
where to get them.

## Part 1 — Measles analysis (R)

Filters the Project Tycho data to measles and visualizes:

- cumulative cases per state (US choropleth + bar chart),
- annual cases over the full record, with the **1963 vaccine licensing date
  marked** — the clearest view of the vaccine's impact,
- cases vs. measles immunization coverage for 1981–2001, including a
  correlation and a simple linear model.

**Key finding.** U.S. measles incidence collapsed within a few years of the
1963 vaccine introduction and stayed low while coverage remained high.

> ⚠️ **Honest statistical caveat (read this).** A correlation between cases and
> coverage computed across the *whole* record mixes pre-vaccine years (0%
> coverage, very high counts) with post-vaccine years and therefore mostly
> measures a time trend, not a clean dose–response relationship. This analysis
> restricts the correlation/model to the vaccination era (1981–2001) on
> purpose, and treats the annual time-series plot — not a single correlation
> coefficient — as the real evidence for the vaccine's effect.

### Run it

```r
install.packages(c("tidyverse", "lubridate", "usmap", "patchwork", "modelr"))
# then, in RStudio, open measles_analysis.Rmd and click "Knit",
# or from the console:
rmarkdown::render("r-measles-analysis/measles_analysis.Rmd")
```

## Part 2 — Data visualization (Python)

Recreates, from artificial genomics data:

1. three alternative views of four RNA-binding-protein signals over a shared
   genomic annotation track (stacked line panels, a `pcolormesh` heatmap, and
   overlaid coloured lines), with a written discussion of the trade-offs;
2. a single multi-panel figure combining a scatter plot, a grouped bar plot,
   and the annotation track;
3. positional 2-mer (k-mer) counts across a set of DNA sequences.

The annotation-track drawing logic is factored into one reusable helper
(`draw_annotation_track`) rather than copied per figure, and all inputs load
via **relative paths**.

### Run it

```bash
python -m venv .venv && source .venv/bin/activate    # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cd python-data-visualization
jupyter notebook data_visualization_part2.ipynb
```

Running the notebook writes the figures to `python-data-visualization/figures/`.
To show them on this page, export the ones you want and embed them, e.g.:

```markdown
![Version 1](python-data-visualization/figures/ex1_version1.png)
```

## Authors

Shefali Badre — M.Sc. Life Science Informatics, DIT.

## License

Released under the [MIT License](LICENSE). The Project Tycho data and the
course-provided datasets are **not** covered by this license and remain subject
to their own terms.
