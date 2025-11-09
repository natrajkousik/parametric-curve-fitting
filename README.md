# parametric-curve-fitting
## Results Overview

**Estimated parameters**

- \(\theta = 0.490759 \text{ rad} \approx 28.118416^\circ\)
- \(M = 0.021389\)
- \(X = 54.900351\)

**Submission parametric equation** (Desmos/LaTeX):

\[
\left(
t\cos(0.490759)-e^{0.021389|t|}\sin(0.3t)\sin(0.490759)+54.900351,\;
42+t\sin(0.490759)+e^{0.021389|t|}\sin(0.3t)\cos(0.490759)
\right),
\quad 6 \le t \le 60
\]

### Plots

<p align="center">
  <img src="images/observed_vs_fitted.png" alt="Observed vs Fitted" width="75%">
</p>

<p align="center">
  <img src="images/errors_vs_t.png" alt="Absolute Errors vs t" width="75%">
</p>

<p align="center">
  <img src="images/cumulative_l1.png" alt="Cumulative L1 Distance" width="75%">
</p>

### Reproduce locally

```bash
pip install numpy pandas matplotlib
python src/fit_parameters.py
