# Error Bounds in Observer-Based LTI System Identification

Jupyter Notebook examples associated with the paper **“Error bounds in observer-based LTI system identification”** by Fethi Bencherki and Hüseyin Akçay.

This repository contains the numerical experiments used to illustrate the paper’s observer-based system-identification results. The experiments compare least-squares estimation with constrained weighted LASSO under Gaussian and uniform measurement noise, visualize feasible parameter sets, and study how the estimation error changes with the noise amplitude.

## Repository Contents

- 📘 **Figures 1–4 — LS and Weighted-LASSO Estimator Comparison**  
  [`estimator_comparison.ipynb`](estimator_comparison.ipynb)  
  Compares the least-squares and constrained weighted-LASSO estimators for
  Gaussian and uniformly distributed measurement noise. The notebook reports
  Monte Carlo estimation errors as the sample size increases and generates the
  corresponding mean-error and box-plot figures.

- 📗 **Figures 5–8 — Feasible Parameter Sets**  
  [`feasible_parameter_sets.ipynb`](feasible_parameter_sets.ipynb)  
  Visualizes the feasible parameter sets for a first-order SISO model under
  Gaussian and uniform measurement noise. It also compares the locations of the
  least-squares and constrained weighted-LASSO estimates and illustrates how the
  feasible ellipse and its area change with the sample size.

- 📙 **Estimation Error versus Noise Amplitude**  
  [`estimation_error_vs_noise_amplitude.ipynb`](estimation_error_vs_noise_amplitude.ipynb)  
  Studies the dependence of the estimation error on the uniform-noise amplitude
  at a fixed large sample size. It compares least squares with constrained
  weighted LASSO over a logarithmic sweep of noise amplitudes. Numba is used
  automatically when available; otherwise the notebook falls back to the same
  non-Numba implementation.

Each notebook is self-contained and includes short documentation blocks and tables describing the main functions before the corresponding code cells.

## Installation

The main dependencies are:

```bash
python -m pip install numpy scipy matplotlib cvxpy
```

Optional packages for acceleration and figure export are:

```bash
python -m pip install numba tikzplotlib
```

- **Numba** optionally accelerates the large-data calculations in the noise-amplitude experiment. If Numba is not installed, the notebook automatically uses the non-Numba implementation.
- **tikzplotlib** is used to export Matplotlib figures as TikZ/PGFPlots `.tex` files where supported.
- **CVXPY** is used for the constrained weighted-LASSO optimization problems. The notebooks try available compatible solvers and include fallback solver choices where appropriate.

## Compared Estimators

| Experiment | Estimators / quantities |
|---|---|
| Figures 1–4 | Least squares and constrained weighted LASSO under Gaussian and uniform measurement noise |
| Figures 5–8 | Least squares, constrained weighted LASSO, and feasible parameter sets |
| Noise-amplitude sweep | Least squares and constrained weighted LASSO versus uniform-noise amplitude |

Within each Monte Carlo realization, the estimators are evaluated using the same generated data whenever a direct comparison is made.

## Figure Export

Running the notebooks creates figure files in the `Figures/` directory. Depending on the experiment, PDF, PNG, TikZ/PGFPlots `.tex`, NumPy `.npz`, and CSV outputs are generated.

Representative outputs include:

| Notebook | Generated output |
|---|---|
| Figures 1–4 | `Figures/ls_lasso_white_noise_two_stds.*` |
| Figures 1–4 | `Figures/ls_lasso_boxplot_two_stds.*` |
| Figures 1–4 | `Figures/ls_lasso_uniform_noise_two_mus_fast.*` |
| Figures 1–4 | `Figures/ls_lasso_uniform_boxplot_two_mus_fast.*` |
| Figures 5–8 | `Figures/all_realization_feasible_sets_gaussian_white_noise.*` |
| Figures 5–8 | `Figures/all_realization_feasible_sets_uniform_noise_5_percent.*` |
| Figures 5–8 | `Figures/single_uniform_realization_N_study/` |
| Noise-amplitude sweep | `Figures/ls_lasso_uniform_error_vs_mu_N1million.*` |

Here `.*` denotes the available exported formats, such as `.pdf`, `.png`, and `.tex`.

## Citation

If you use this code, please cite the associated paper:

```bibtex
@misc{bencherki2026error,
  title  = {Error Bounds in Observer-Based LTI System Identification},
  author = {Bencherki, Fethi and Akcay, Huseyin},
  year   = {2026}
}
```
