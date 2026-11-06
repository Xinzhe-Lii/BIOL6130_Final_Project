# Abstract

Roads may help plants spread by moving seeds through the landscape. We tested whether roads were associated with eucalyptus forest expansion in central Portugal between 2018 and 2025. We predicted more new eucalyptus cover near roads and a slower decline in new cover with increasing distance from existing eucalyptus forest.

We combined official land-cover maps with the 2018 road network and environmental data. Initially non-eucalyptus land within 100 m of existing eucalyptus forest was divided into a 20 m accounting grid. Comparisons were grouped by source forest and initial land cover. Area-weighted models accounted for terrain, climate, wind, fire history and forest management. Main roads, residential roads and forest-access routes were included in the road-distance measure.

Of 26,309 ha of eligible land, 766 ha changed to mapped eucalyptus cover. At reference road distances of 36 m and 169 m, the adjusted near–far difference in gain was +0.03 percentage points (95% confidence interval: −0.64 to +0.69). Gain declined similarly near and far from roads as distance from existing forest increased from 25 to 75 m. The near–far difference in this change was −0.003 percentage points (95% confidence interval: −0.130 to +0.124). Exploratory examination of burned sites found pine-to-eucalyptus transitions beside both a passage and an existing forest edge.

Neither prediction was supported by this analysis, but the results do not establish that roads have no effect. Forest-cover maps cannot distinguish natural establishment from planting or regrowth, or determine whether conversion preceded or followed fire. Linear model predictions also fell outside 0–1 over 40.7% of the analysed area, and estimates depended on which forest groups were included. Linking dated forest changes with planting and regeneration records would help explain when roads matter for forest expansion.

# Reproduce the analysis

Install R, Quarto and a LaTeX distribution such as TinyTeX. The analysis uses R 4.3.3 and Quarto 1.9.38. Install the R packages below; `sf` and `terra` also need their system libraries when built from source.

```r
install.packages(c("sf", "terra", "dplyr", "ggplot2", "tidyterra", "fixest",
                   "tidyr", "readr", "jsonlite", "digest", "knitr", "png"))
```

Package versions used:

| Package | Version |
| --- | --- |
| sf | 1.0.15 |
| terra | 1.7.65 |
| dplyr | 1.2.1 |
| ggplot2 | 4.0.3 |
| tidyterra | 0.6.2 |
| fixest | 0.14.2 |
| tidyr | 1.3.2 |
| readr | 2.2.0 |
| jsonlite | 2.0.0 |
| digest | 0.6.39 |
| knitr | 1.51 |
| png | 0.1.9 |

Clone the repository, then render from its root folder:

```sh
git clone https://github.com/Xinzhe-Lii/BIOL6130_Final_Project.git
cd BIOL6130_Final_Project
quarto render analysis.qmd
```

The input files are in `Raw Data/`. These include clipped datasets and the derived spatial subsets in `poster_map_inputs.gpkg`, rather than only untouched source files. The two 2025 orthophoto PNGs are DGT imagery. On the first run, `analysis.qmd` downloads the WorldClim pilot climate file if it is missing, so an internet connection is needed. That file is excluded from Git; the regional climate data are included. Dataset sources, licences and citations are listed at the end of `analysis.qmd`.

The first render computes the spatial overlays and models and creates `analysis.pdf`. Derived files are saved in the ignored `_cache/` folder, which speeds up later renders. A fresh clone recomputes these files. The analysis does not use random sampling; a fixed seed is set for reproducibility.

`LICENSE` applies to the project code. The source datasets and imagery retain their own licences and attribution requirements, listed in the QMD. The 20 m grid is an area-accounting grid; it does not increase the resolution of the source maps.

# Generative AI Use

ChatGPT and OpenAI Codex were used to help set up folders, find and download data and literature, write and revise R code, debug the analysis, prepare figures and the poster layout,  revise the text.
