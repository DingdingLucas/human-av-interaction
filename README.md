# Human Driver Responses to Autonomous Vehicles

## Overview

This project studies how human drivers respond differently to autonomous vehicles (AVs) compared to other human-driven vehicles. Using naturalistic driving data from the Waymo Open Motion Dataset, we examine whether and how the presence of AVs on the road alters the behavior, risk-taking, and decision-making of surrounding human drivers.

## Research Questions

- Do human drivers behave differently (e.g., following distance, lane-changing, speed) when interacting with AVs versus human-driven vehicles?
- Are behavioral responses heterogeneous across driver demographics, experience, or familiarity with AV technology?
- What are the safety and efficiency implications of human–AV interaction patterns?

## Authors

- Dingding Lucas Li
- [Co-author 2]
- [Co-author 3]

## Repository Structure

```
├── Code/
│   ├── data_cleaning/   # Scripts for parsing and cleaning Waymo tfrecord files
│   ├── analysis/        # Regression and statistical analysis
│   └── figures/         # Figure-generating scripts
├── Data/
│   ├── RawData/
│   │   └── WaymoMotion/     # Raw .tfrecord files (not tracked by git)
│   ├── MiddleData/
│   │   ├── trajectories/    # Extracted vehicle trajectories (parquet/csv)
│   │   └── interactions/    # Identified AV–human interaction events
│   └── RunningData/         # Analysis-ready panel datasets
├── Results/
│   ├── Figures/         # Output figures (.png, .pdf)
│   └── Tables/          # Output tables (.tex, .xlsx)
├── Draft/               # Paper drafts
├── Literature/          # Reference papers
└── Notes/               # Meeting notes, data documentation
```

## Data

**Primary Source: [Waymo Open Motion Dataset](https://waymo.com/open/data/motion/)**

- **Coverage**: Naturalistic driving scenarios collected in California (San Francisco, Los Altos)
- **Scale**: 103,354 twenty-second segments recorded at 10 Hz
- **Objects tracked**: Vehicles, pedestrians, and cyclists
- **Key variables per object per timestep**: 3D position (x, y, z), velocity, heading, and object dimensions
- **Map features**: Static road geometry and dynamic features (e.g., traffic signals)
- **File format**: Protocol buffer scenarios (`.tfrecord`); can be converted to `tf.Example` protos for ML pipelines
- **Splits**: Training (70%), validation (15%), test (15%)

The Waymo vehicle in each scenario is the ego AV. Surrounding tracked objects represent human-driven vehicles (and other road users), enabling comparison of human behavior when near the AV versus when interacting with other human drivers.

## Empirical Strategy

[To be filled in: identification strategy, estimation methods]

## Requirements

- **Python**: `tensorflow`, `waymo-open-dataset`, `pandas`, `pyarrow`
- **R**: `haven`, `dplyr`, `ggplot2`, `fixest`, `modelsummary`, `sandwich`
