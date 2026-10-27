# Kelp_ES_Map

Data and R code for the systematic map:

> **Characterising ecosystem service provision by two morphologically distinct kelp species (*Laminaria hyperborea* and *Saccharina latissima*) and the biophysical drivers shaping these services: a systematic map**
> Hall, B., Eskuche-Keith, P., Ren, Y., Moore, P. J., Fitzsimmons, C., & Stephenson, F.

This repository is the research compendium for the systematic map. It contains the extracted dataset (codebook), the R code used for all analyses and figures, and the supporting files, so that the results reported in the manuscript can be reproduced.

The map was conducted in accordance with an *a priori*, peer-reviewed protocol published in *Environmental Evidence*:

> Hall, B., Eskuche-Keith, P., Ren, Y., Moore, P. J., Fitzsimmons, C., & Stephenson, F. (2026). *Characterising ecosystem service provision by two morphologically distinct kelp species (Laminaria hyperborea and Saccharina latissima) and the biophysical drivers shaping these services: a systematic map protocol.* Environmental Evidence, 15:6. https://doi.org/10.1186/s13750-026-00385-w

## Overview

The map consolidates and characterises the peer-reviewed and grey literature on ecosystem service (ES) provision by two NE Atlantic kelp species with contrasting growth forms — stipitate *Laminaria hyperborea* and prostrate *Saccharina latissima* — and the biophysical drivers shaping these services. From an initial 6,979 records, **206 articles** met the inclusion criteria and were coded. Evidence was characterised by ES category and individual service, by species, by biophysical driver, geographically, and over time, following Collaboration for Environmental Evidence (CEE) guidance and ROSES reporting standards. No quantitative meta-analysis was conducted.

## Contents

All files sit at the top level of the repository.

### Data
- `Codebook_Kelp_Long.csv` — long-format coded dataset of the 206 included articles (one row per study, with ES, biophysical driver, measurement-type and species-focus fields). **This is the main input for every script.**
- `Codebook_Kelp_ES.xlsx` — the full codebook (Additional file 4): data-coding framework, coded metadata, full-text exclusions with reasons, unretrievable full texts, and categorical coding variables.
- `ES_Service_Type.csv` — lookup table mapping each individual ecosystem service to its MEA category (Provisioning / Regulating / Supporting / Cultural).

### Code
Each script reads `Codebook_Kelp_Long.csv`; the category plot and the table scripts also read `ES_Service_Type.csv`.

| Script | Produces (manuscript item) |
|---|---|
| `Plot_studies_by_year.R` | Figure 2 — ES mentions per year + cumulative articles |
| `plot_world_map.R` | Figure 3 — global map of research effort, Europe inset |
| `plot_services_barplot.R` | Figure 4 — individual services coloured by MEA category |
| `plot_services_by_species.R` | Figure 5 — services split by species focus |
| `Plot_Biophysical_Driver_VS_ES.R` | Figure 6 — biophysical driver × ES heatmap |
| `Plot_Measurement_type_vs_ES.R` | Supplementary Figure 1 — measurement type × ES heatmap |
| `Table_creation_Countries_services.R` | Country / ES / species summary tables (incl. Supplementary Table 4) |
| `Table_creation_ES_Measurement_type.R` | Measurement-type summary tables |
| `Total_Biophysical_Drivers_Identified.R` | Biophysical-driver counts by species (Supplementary Table 6) |

## Reproducing the analysis

Analyses were run in **R version 4.5.1** within RStudio. Install the required packages once:

```r
install.packages(c(
  "tidyverse",                    # dplyr, tidyr, ggplot2, readr, stringr, forcats
  "scales", "viridis", "ggtext",  # scales, palettes, markdown text in labels
  "sf", "rnaturalearth", "rnaturalearthdata", "countrycode",  # map (Figure 3)
  "rcartocolor", "ggspatial", "cowplot"                        # map composition
))
```

Then, in R, set your working directory to the folder that contains these files and `source()` whichever script you want, e.g.:

```r
setwd("path/to/Kelp_ES_Map")   # the folder holding Codebook_Kelp_Long.csv
source("Plot_studies_by_year.R")
```

Because every file is in the same folder, the scripts find `Codebook_Kelp_Long.csv` and `ES_Service_Type.csv` automatically. Each script writes its figure/table outputs (PNG/PDF/CSV) into the same folder. The scripts are independent and can be run in any order.

## Licence

- **Code** (the `.R` scripts): MIT License — see [`LICENSE`](LICENSE).
- **Data and the codebook** (`Codebook_Kelp_Long.csv`, `Codebook_Kelp_ES.xlsx`, `ES_Service_Type.csv`): Creative Commons Attribution 4.0 International (CC BY 4.0) — see [`DATA_LICENSE.txt`](DATA_LICENSE.txt).

## How to cite

Please cite both the repository (see the "Cite this repository" button, generated from `CITATION.cff`) and the published protocol (DOI above). A permanent archived version with a Zenodo DOI will be added on publication of the map.

## Contact

Benjamin Hall — b.hall8@newcastle.ac.uk
Dove Marine Laboratory, School of Natural and Environmental Sciences, Newcastle University, UK
