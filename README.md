# Statistics of Stochastic Processes

**Python laboratory notebooks and an applied research project on stochastic processes, stochastic differential equations (SDEs), and statistical inference.**

This repository brings together five computational laboratory assignments and a final project on the dynamics of US interest rates. The notebooks progress from simulating Wiener processes to constructing stochastic models, analyzing numerical methods, estimating model parameters, and studying diffusion models using nonparametric techniques.

## Contents

| Notebook | Topics |
| --- | --- |
| [01 · Wiener Process](01_wiener_process.ipynb) | Brownian motion simulation, random-walk limits, Karhunen–Loève expansion, Brownian bridges, quadratic variation, covariance, martingales, and independent increments. |
| [02 · Advanced Stochastic Models and Calibration](02_advanced_stochastic_models_and_calibration.ipynb) | OU, CIR, Black–Scholes–Merton and other diffusions; stochastic volatility, regime switching, theoretical moments, mean reversion, and simulation-based calibration. |
| [03 · SDE Numerical Schemes and Convergence](03_sde_numerical_schemes_and_convergence_ipynb.ipynb) | Euler–Maruyama, Milstein, predictor–corrector methods, strong convergence experiments, conditional moments, and distributional comparisons. |
| [04 · SDE Parameter Estimation and Statistical Inference](04_sde_parameter_estimation_and_statistical_inference.ipynb) | Exact and approximate maximum likelihood, CKLS estimation, Ozaki and Kessler approximations, confidence intervals, and sampling-frequency experiments. |
| [05 · Nonparametric SDE Estimation and Kernel Methods](05_nonparametric_sde_estimation_and_kernel_methods.ipynb) | Kernel density estimation, bandwidth selection, nonparametric drift and diffusion estimation, ergodicity/mixing experiments, and statistical validation. |
| **[Final Project · US Interest Rates](Project_US_Interest_Rates_SDE_Modeling.ipynb)** | Historical interest-rate data, six SDE specifications, numerical MLE, model comparison, structural-change exploration, and innovation diagnostics. |

The notebooks are self-contained teaching and experimentation materials, with explanations, code, figures, and interpretations alongside the computations.

## Final Project: Modeling US Interest Rates (1964–1989)

The final project analyzes **307 monthly observations of US interest rates**, covering **June 1964 through December 1989**, to examine how alternative continuous-time stochastic models describe interest-rate dynamics.

**Research workflow**

1. **Exploratory analysis:** Plot the historical series and rate changes; calculate descriptive statistics; examine outliers, distributional shape, normality, and temporal dependence.
2. **Exploratory structural-change analysis:** Apply CUSUM-based change-point detection with a moving-block bootstrap, while recognizing the limitations of structural-break inference.
3. **Specify SDE models:** Brownian motion (BM), geometric Brownian motion (GBM), Ornstein–Uhlenbeck (OU), Cox–Ingersoll–Ross (CIR), constant elasticity of variance (CEV), and Chan–Karolyi–Longstaff–Sanders (CKLS).
4. **Estimate parameters:** Use Gaussian transition-density approximations based on **Euler, Kessler, and Shoji–Ozaki** methods and numerical maximum likelihood optimization with multiple starting points.
5. **Cross-check implementations:** Compare a custom estimation implementation with the [`pymle`](https://github.com/jkirkby3/pymle) library.
6. **Select and diagnose models:** Compare log-likelihoods, **AIC**, and **BIC**, visualize fitted dynamics, and inspect conditional one-step predictions and standardized innovations using histograms, Q–Q plots, and autocorrelation.

### Interpretation and limitations

The analysis examines whether level-dependent volatility and mean reversion help explain the observed rate dynamics. Flexible CEV/CKLS-type specifications are compared with simpler benchmark models, but **AIC/BIC rankings measure relative in-sample fit, not out-of-sample predictive accuracy**. Differences between transition-density implementations and numerical optimizers should be interpreted carefully. Detected structural changes are exploratory; residual diagnostics and one-step *in-sample* predictions do not constitute an independent forecasting test.

**Notebook:** [Project_US_Interest_Rates_SDE_Modeling.ipynb](Project_US_Interest_Rates_SDE_Modeling.ipynb)  
**Dataset:** [data/Project_3.xlsx](data/Project_3.xlsx)

## Repository Structure

```text
Statistics-of-Stochastic-Processes/
├── 01_wiener_process.ipynb
├── 02_advanced_stochastic_models_and_calibration.ipynb
├── 03_sde_numerical_schemes_and_convergence_ipynb.ipynb
├── 04_sde_parameter_estimation_and_statistical_inference.ipynb
├── 05_nonparametric_sde_estimation_and_kernel_methods.ipynb
├── Project_US_Interest_Rates_SDE_Modeling.ipynb
├── data/
│   └── Project_3.xlsx
└── README.md
```

## Requirements

- Python 3 and Jupyter Notebook or JupyterLab
- NumPy, Pandas, SciPy, Matplotlib
- Statsmodels, scikit-learn, Numba, and openpyxl
- [`pymle`](https://github.com/jkirkby3/pymle) for the final project's library-based estimation section

Install the main dependencies:

```bash
python -m pip install jupyter numpy pandas scipy matplotlib statsmodels scikit-learn numba openpyxl
python -m pip install git+https://github.com/jkirkby3/pymle.git
```

## Running the Notebooks

1. Clone the repository:

   ```bash
   git clone https://github.com/Saharochek98/Statistics-of-Stochastic-Processes.git
   cd Statistics-of-Stochastic-Processes
   ```

2. Install the dependencies listed above.
3. Start Jupyter:

   ```bash
   jupyter notebook
   ```

4. Open a laboratory notebook or the [final project](Project_US_Interest_Rates_SDE_Modeling.ipynb) and run its cells in order.

**Dataset path note:** The final project currently loads the Excel data using `load_rates_excel('Project_3.xlsx')`, while the tracked file is located at `data/Project_3.xlsx`. To run the notebook from the repository root, change that call to:

```python
rates = load_rates_excel('data/Project_3.xlsx')
```

Alternatively, place a copy of `Project_3.xlsx` in the notebook's working directory. The workbook is read from the sheet named `Лист1`.

Some simulation cells generate random realizations; numerical figures may vary across runs. Optimization outcomes may also depend on starting values, parameter bounds, and numerical approximations.

## Methods at a Glance

| Area | Methods and concepts |
| --- | --- |
| Stochastic processes | Wiener process, geometric Brownian motion, Brownian bridge, martingales |
| Diffusion models | OU/Vasicek, CIR, CKLS, CEV, Black–Scholes–Merton, other nonlinear diffusions |
| Numerical SDE methods | Euler–Maruyama, Milstein, predictor–corrector, Ozaki/Shoji–Ozaki, Kessler |
| Statistical estimation | Maximum likelihood, Gaussian pseudo-likelihood, confidence intervals, Monte Carlo comparisons |
| Nonparametric inference | Kernel density estimation, drift/diffusion coefficient recovery, bandwidth analysis |
| Model diagnostics | AIC/BIC, normality checks, Q–Q plots, autocorrelation, standardized innovations |

## Academic Purpose

This repository documents laboratory and project work in **Statistics of Stochastic Processes**. Its primary purpose is educational: to connect stochastic-process theory with reproducible Python experiments and empirical financial modeling.
