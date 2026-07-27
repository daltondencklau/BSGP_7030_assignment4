# BSGP_7030_assignment4_stats_script
# BSGP 7030 – Assignment 4

Statistical analysis in Python following the SciPy Lecture Notes. Done as part of BSGP 7030 at Ohio State.

## What's in here

```
├── BSGP_Assignment_4_stat_script.ipynb   # main notebook
├── brain_size.csv                         # brain size + IQ dataset
├── iris.csv                               # iris dataset
├── environment.yml                        # conda environment
└── README.md
```

## Setup


```bash
module load miniconda3/24.1.2-py310
conda env create -f environment.yml
conda activate assignment4
jupyter lab
```

## What the notebook covers

- Loading and cleaning messy CSVs (semicolon-delimited, missing values)
- Descriptive stats and groupby operations
- t-tests and Mann-Whitney U tests for group comparisons
- OLS regression with statsmodels, including interaction terms
- Scatter matrices and seaborn pairplots

## Data sources

- Brain size/IQ: Willerman et al. (1991)
- Wages: Berndt, E.R. (1991). *The Practice of Econometrics*
- Tutorial: https://scipy-lectures.org/packages/statistics/index.html
