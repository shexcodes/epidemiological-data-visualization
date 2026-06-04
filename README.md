# Data — R measles analysis

The input data is **not** committed to the repository (it is ignored via
`.gitignore`, as the Project Tycho dataset is large and distributed under its
own terms). Place the following file in this folder before knitting
`measles_analysis.Rmd`:

| File | Description |
|------|-------------|
| `ProjectTycho_Level2_v1.1.0.csv` | Project Tycho Level 2 dataset (weekly U.S. notifiable-disease surveillance). The analysis filters it to `disease == "MEASLES"`. |

**Source:** Project Tycho, University of Pittsburgh — <https://www.tycho.pitt.edu>
Register/download the Level 2 dataset there and cite it per their data-use
terms.

The immunization-coverage figures used in the report are currently transcribed
into a `tribble()` inside the `.Rmd`. If you move them into a CSV here (e.g.
`measles_vaccination.csv` with columns `year`, `immunization_rate`), update the
corresponding chunk to `read_csv()` it so the numbers are auditable.
