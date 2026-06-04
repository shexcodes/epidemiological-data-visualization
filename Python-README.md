# Data Visualization — Part 2 (Python)

`matplotlib`/`pandas`/`numpy` recreations of figures from artificial genomics
data. See [`data_visualization_part2.ipynb`](data_visualization_part2.ipynb).

Contents:
1. Three views of four RNA-binding-protein signals over a genomic annotation
   track (stacked lines, `pcolormesh` heatmap, overlaid coloured lines) + a
   discussion of the trade-offs.
2. A single multi-panel figure (scatter + grouped bars + annotation track).
3. Positional 2-mer counts across DNA sequences.

## Run

```bash
pip install -r ../requirements.txt
jupyter notebook data_visualization_part2.ipynb
```

Place the course data files in [`data/`](data/) first (see `data/README.md`).
Figures are written to `figures/`.
