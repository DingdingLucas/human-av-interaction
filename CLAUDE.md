# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This project studies how human drivers respond behaviorally to autonomous vehicles (AVs) relative to human-driven vehicles — examining differences in following distance, speed, lane changes, and other driving behaviors. The goal is to identify causal behavioral shifts and assess their safety and efficiency implications.

## Repository Structure

```
Code/
  data_cleaning/   — raw data ingestion and standardization scripts
  analysis/        — regression, statistical models, and robustness checks
  figures/         — figure-generating scripts (output to Results/Figures/)
Data/
  RawData/         — original, unmodified data; never overwrite
  MiddleData/      — intermediate outputs from cleaning steps
  RunningData/     — final analysis-ready datasets
Results/
  Figures/         — paper figures (.png, .pdf)
  Tables/          — LaTeX and Excel tables
Draft/             — paper drafts
Literature/        — reference papers
Notes/             — data documentation and meeting notes
```

## Coding Conventions

- **Language**: R is preferred for analysis and figures; Python is acceptable for data processing if necessary
- **Data pipeline**: Raw → Middle → Running. Scripts should read from one stage and write to the next; never overwrite RawData
- **File naming**: Use `snake_case` for scripts and output files (e.g., `clean_driving_logs.R`, `table1_main_results.tex`)
- **Working directory**: Always set `setwd()` explicitly at the top of each script using absolute paths; do not rely on relative paths
- **Standard errors**: Cluster at the appropriate unit (driver, road segment, or session) using `vcovCL(..., type="HC0")` from the `sandwich` package

## Data Documentation

Document any new dataset added to `RawData/` in `Notes/` with: source, collection method, unit of observation, key variables, and known data quality issues.

## Output

- Figures go to `Results/Figures/` using `ggsave()` with explicit `width`, `height`, and `dpi`
- Tables go to `Results/Tables/` using `modelsummary()` or `stargazer()` with `output = "latex"`
