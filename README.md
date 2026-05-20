# Multi-wavelength Raman mapping of unicellular algae

This code repository contains all materials required for creating and hosting the publication entitled, *"Multi-wavelength Raman mapping of unicellular algae"*.

The publication is hosted at [this URL](https://arcadia-science.github.io/raman-mapping-algae/).

## Data Description

The data in this project is spectral map data in TXT format and a UV-Vis absorbance file in TSV format, all in the `data/` directory:

- `Cells- 473nm-Map-ForPeng 1.txt` — 473 nm Raman map of *C. reinhardtii* CC-124 cells (Horiba LabRam)
- `Cells- 532nm-Map-ForPeng 1.txt` — 532 nm Raman map of *C. reinhardtii* CC-124 cells (Horiba LabRam)
- `2024-11-12_CC-1373_TAP_slide_10_singlecellmap.txt` — 785 nm Raman map of *C. smithii* CC-1373 (Renishaw inVia)
- `2024-11-12_TAP_slide_single.txt` — 785 nm background spectrum on TAP medium
- `UV-Vis 5_1_2025 7_19_21 PM.tsv` — UV-Vis absorbance spectra of pigment standards

## Environment

This analysis was developed and tested on a MacBook Pro (Apple M3 Max, 36 GB RAM) running macOS Sonoma 14.7.3, with Python 3.12.13. The environment is captured in `env.yml` with exact version pins to support reproducibility.

## Reproduce

Please see [pages/SETUP.qmd](pages/SETUP.qmd).

## Contribute

Please see [pages/CONTRIBUTING.qmd](pages/CONTRIBUTING.qmd).
