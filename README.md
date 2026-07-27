# BSGP 7030 — Assignment 4: Statistics in Python

Reproduce and extend the [Scipy Lecture Notes — Statistics in Python](https://scipy-lectures.org/packages/statistics/index.html) chapter (Gaël Varoquaux), then redo the analysis with an AI assistant using prompt-driven workflows.

## What this repository contains

| Path | Purpose |
|------|---------|
| `notebooks/stats_python.ipynb` (SciPy lecture walkthrough) | Line-by-line walkthrough of the SciPy lecture examples (one code cell per inline example, comments + section markdown) |
| `notebooks/stats_python.ipynb` | SciPy lecture walkthrough (one cell per example) |
| `notebooks/examples/` | `brain_size.csv`, `iris.csv`, `wages.txt` for the tutorial notebook |
| `stats_python.ipynb` | Prompt-driven AI redo of the analysis |
| `stats_extension.ipynb` | Extension: **bootstrap confidence intervals** |
| `PROMPTS.md` | Exact prompts used for the AI notebooks |
| `brain_size.csv`, `iris.csv`, `wages.txt` | Data for the AI notebooks (cwd = this folder) |
| `environment.yml` | Conda environment definition |
| `requirements.txt` | Pip-compatible dependency list |
| `.gitignore` | Ignores checkpoints, venvs, caches, OS junk |

## Datasets

1. **Brain size and IQ** (`brain_size.csv`) — Willerman et al. (1991). Semicolon-separated; missing values marked `.`.
2. **Iris** (`iris.csv`) — sepal/petal measurements by species.
3. **CPS wages** (`wages.txt`) — 1985 Current Population Survey sample ([CMU StatLib](https://lib.stat.cmu.edu/datasets/CPS_85_Wages)). Documentation header/footer surround the numeric table.

## Requirements

- Conda (Miniconda/Anaconda/Mamba) **or** Python 3.10+ with pip
- Packages: `numpy`, `scipy`, `pandas`, `matplotlib`, `seaborn`, `statsmodels`, `jupyter` / `notebook`

## Setup

### Option A — Conda (recommended)

```bash
cd ai   # or whatever you named this folder after upload
conda env create -f environment.yml
conda activate bsgp7030-assignment4
```

If the `pip: -r requirements.txt` block causes issues on your conda build, create from the YAML dependencies only, then:

```bash
pip install -r requirements.txt
```

### Option B — pip + venv

```bash
cd ai   # or whatever you named this folder after upload
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Register a Jupyter kernel (optional):

```bash
python -m ipykernel install --user --name bsgp7030-assignment4
```

## Running the notebooks

```bash
jupyter notebook
# or: jupyter lab
```

1. Open `notebooks/stats_python.ipynb` (SciPy lecture walkthrough) and run all cells (kernel working directory should be `notebooks/` so `examples/...` paths resolve).
2. Open `ai/stats_python.ipynb` and `ai/stats_extension.ipynb` with the working directory set to `ai/` (Jupyter usually uses the notebook’s folder).

From the command line you can also execute:

```bash
jupyter nbconvert --to notebook --execute notebooks/stats_python.ipynb --inplace
jupyter nbconvert --to notebook --execute stats_python.ipynb --inplace
jupyter nbconvert --to notebook --execute stats_extension.ipynb --inplace
```

## Analysis overview

### Tutorial notebook (`notebooks/stats_python.ipynb`)

Follows the lecture sections:

- Pandas DataFrames, groupby, scatter matrices  
- One- and two-sample t-tests, paired tests, Wilcoxon  
- Statsmodels OLS formulas, categorical predictors, multiple regression, ANOVA contrasts  
- Seaborn pairplot / lmplot on wages  
- Education × gender interaction model  

### AI notebooks (this folder)

- **Prompt-driven redo** of the same questions (see `ai/PROMPTS.md`).  
- **Extension:** nonparametric bootstrap 95% CIs for (1) the male−female VIQ mean difference and (2) an OLS `Gender` coefficient after adjusting for MRI volume — methods not covered in the SciPy chapter.

## Project status / roadmap

- [x] Tutorial notebook mirroring scipy-lectures examples  
- [x] AI prompt-driven analysis notebook  
- [x] One statistical extension (bootstrap CIs)  
- [x] Prompts log, environment files, `.gitignore`, README  

## Contributing

This is a course assignment repository. If you fork it for practice:

1. Keep data provenance clear (Willerman / iris / CPS).  
2. Prefer adding cells over silently rewriting existing tutorial cells.  
3. Log new AI prompts in `PROMPTS.md`.

## License / attribution

- Tutorial content adapted from [Scipy lecture notes](https://scipy-lectures.org/) (CC-BY / project license on that site).  
- Brain-size data: Willerman et al. (1991).  
- Wages data: CMU StatLib CPS_85_Wages / Berndt (1991).  
- Iris: classic Fisher / Anderson dataset.

## Contact

Course: **BSGP 7030 — Assignment 4**.

