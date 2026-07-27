# Cox Proportional Hazards Model — Survival Analysis of Lung Cancer Data

**STA 6257 – Advanced Statistical Modeling**
**Authors:** Halley Deleeuw and Jasmine Sawh

A survival-analysis project applying the Cox Proportional Hazards model to the
NCCTG lung cancer data set, written in [Quarto](https://quarto.org/) with R.

📄 **[Read the rendered report](https://halleyd18.github.io/STA6257_Project_Cox_Proportional_Hazards/)**
*(or open [`index.html`](index.html) locally)*

## Overview

The Cox Proportional Hazards (Cox PH) model is a semi-parametric method for
survival analysis: it models the *hazard* — the instantaneous risk of an event —
without assuming a shape for the baseline hazard over time. This project:

- explains the hazard function, the partial likelihood, and hazard ratios;
- fits a Cox model to the `lung` data set (228 advanced lung cancer patients);
- interprets which patient characteristics predict survival; and
- checks the proportional-hazards assumption using scaled Schoenfeld residuals.

## Key findings

- **Sex** is the strongest predictor: female patients have roughly **half** the
  hazard of death of males (HR ≈ 0.53, p < 0.001).
- **ECOG performance status** more than **doubles** the hazard for each one-point
  increase (HR ≈ 2.10, p < 0.001).
- Age, Karnofsky score, and weight loss were not significant once sex and ECOG
  status were included.
- The proportional-hazards assumption holds globally (Schoenfeld test p ≈ 0.21).

## Repository contents

| File | Description |
|------|-------------|
| `index.qmd` | The Quarto source for the report (analysis + write-up). |
| `index.html` | The rendered report (also served via GitHub Pages). |
| `references.bib` | Bibliography (BibTeX). |
| `docs/literature-review.md` | Annotated list of peer-reviewed sources reviewed. |
| `docs/reading-journal-halley.md` | Weekly reading journal with article summaries. |
| `docs/reading-journal-2.md` | Additional reading journal entries. |

## Reproducing the report

Requires [R](https://www.r-project.org/) and
[Quarto](https://quarto.org/docs/get-started/).

```bash
# Install the R packages used by the report
Rscript -e 'install.packages(c("survival", "ggplot2", "knitr", "scales", "rmarkdown"))'

# Render index.qmd -> index.html
quarto render index.qmd
```

The `lung` data set ships with the `survival` package, so no external data files
are needed.

## Methods & tools

Kaplan–Meier estimation, the log-rank test, Cox proportional hazards regression,
and Schoenfeld-residual diagnostics — all via R's `survival` package.
