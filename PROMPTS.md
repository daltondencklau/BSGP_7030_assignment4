# Prompts log (AI branch)

This file records the prompts used to generate the notebooks under `ai/`.  
The SciPy lecture source was **not** pasted into the model. Datasets and questions were described in plain language.

---

## Prompt 1 — Main analysis → `stats_python.ipynb`

```text
I have three datasets for a biostatistics assignment:

1) brain_size.csv (Willerman et al. 1991) — semicolon-separated, with "." for missing
   values. Columns: Gender, FSIQ, VIQ, PIQ, Weight, Height, MRI_Count for 40 adults.

2) iris.csv — sepal/petal length and width plus species name.

3) wages.txt — 1985 CPS wage sample from CMU (documentation header/footer; numeric
   table starts after ~27 lines). Columns include education, sex, experience, wage,
   age, etc.

Please write a Jupyter notebook that analyzes these data to answer, in order:

- Summarize the brain-size table and compare mean VIQ / MRI volume by gender
  (including mean log10 MRI counts).
- Run classical hypothesis tests: 1-sample t-test of VIQ vs 0; two-sample t-test of
  VIQ by gender; paired t-test and Wilcoxon test of FSIQ vs PIQ; t-test of weight by
  gender; Mann–Whitney test of VIQ by gender.
- Fit OLS models: VIQ ~ Gender; long-format iq ~ type for FSIQ vs PIQ; for iris,
  sepal_width ~ species + petal_length and an F-test contrast of versicolor vs
  virginica; optionally VIQ ~ Gender + MRI_Count + Height + Weight.
- For wages: log10-transform wage, make a seaborn pairplot of wage/age/education by
  sex, and fit wage ~ education * gender to test an education×gender interaction.

Use pandas, scipy.stats, statsmodels formulas, seaborn, and matplotlib. Add short
markdown between sections explaining the scientific question for each block. Save as
ai/stats_python.ipynb. Do not copy code from a tutorial page — derive the analysis
from the questions above.
```

---

## Prompt 2 — Extension → `stats_extension.ipynb`

```text
Using the same brain_size.csv data, extend the analysis with one method that is not
covered in the SciPy “Statistics in Python” lecture.

Please use nonparametric bootstrap confidence intervals:

1) Bootstrap a 95% percentile CI for the male−female mean VIQ difference (resample
   within each gender). Compare to a classical two-sample / Welch-style interval and
   plot the bootstrap distribution.

2) Fit OLS VIQ ~ Gender + MRI_Count, then bootstrap rows of the data frame to get a
   95% CI for the Gender[T.Male] coefficient. Compare to the parametric OLS interval
   and plot the bootstrap distribution.

Explain briefly why bootstrap is useful for this small sample. Save as
ai/stats_extension.ipynb.
```

---

## Notes

- Model used: Cursor AI coding agent (Composer), prompted as above in this assignment session.
- Data files were placed next to the notebooks (`ai/brain_size.csv`, `ai/iris.csv`, `ai/wages.txt`) so relative paths work when the notebook kernel’s cwd is `ai/`.
- Extension choice: **bootstrap CIs** (alternatives considered: robust regression / RLM, mixed-effects, Bayesian). Bootstrap was chosen because it directly revisits the same gender–VIQ and adjusted OLS questions with a different uncertainty method.
