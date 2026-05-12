# Deployment

This repository deploys to GitHub Pages at https://arcadia-science.github.io/2026-raman-mapping-algae/.

## How to deploy

Render and publish from your local machine:

```bash
conda activate 2026-raman-mapping-algae
make execute              # render the site locally (executes the notebook)
quarto publish gh-pages   # push the rendered site directly to the gh-pages branch
```

The first time you run `quarto publish gh-pages`, it will prompt for confirmation. Subsequent deploys are quick.

## Why local-deploy instead of CI

The repository originally shipped with an auto-deploy GitHub Actions workflow that rendered the site on a runner and pushed to `gh-pages` whenever a PR was merged into the `publish` branch. We tried to use it for this publication but ran into issues that made local deploy the more practical choice:

- The notebook's execution is non-trivial: airPLS baseline correction over ~1,000 spectra plus NMF on the masked dataset takes several minutes. During render, Quarto encountered a kernel cleanup error (`TypeError: Child process has already terminated`) on the runner — a known Quarto issue for long-running Jupyter notebooks.
- Embedding Plotly outputs from the spectral maps inflated the executed notebook beyond what the default `ubuntu-latest` runner could process without hitting memory pressure, causing the render step to be canceled mid-execution.
- The notebook already renders cleanly on a local machine with enough RAM (this work was developed on a MacBook Pro M3 Max with 36 GB). `quarto publish gh-pages` from a working local environment sidesteps both issues.

Manual deploy keeps things simple, but requires someone to have the project locally and make changes that can be pushed directly. 

## Workflow file status

The original GitHub Actions workflow is preserved at `.github/workflows/publish.yml.disabled`. GitHub Actions ignores files that don't end in `.yml` or `.yaml`, so it will not run. If a future maintainer wants to revive CI deploy (for example with a larger runner that can handle the memory load, or after the notebook is restructured to reduce per-render cost), rename the file back to `publish.yml` and adjust as needed.
