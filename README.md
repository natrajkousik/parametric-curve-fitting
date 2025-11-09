# Parametric Curve Fitting — Estimating θ, M, and X

This project focuses on estimating unknown parameters in a parametric curve using a given set of (x, y) data points. The main goal is to determine the values of **θ**, **M**, and **X** such that the generated curve matches the observed data as closely as possible.

I have explained everything in a simple and clear way so the approach is easy to understand and reproduce.

---

## 1) Problem Description

We are given the following parametric equations:

\[
x(t) = t\cos(\theta) - e^{M|t|}\sin(0.3t)\sin(\theta) + X
\]

\[
y(t) = 42 + t\sin(\theta) + e^{M|t|}\sin(0.3t)\cos(\theta)
\]

Here, the parameters **θ**, **M**, and **X** are unknown and must be estimated.

### Parameter Ranges

| Parameter | Range |
|----------|--------|
| θ (angle) | 0° < θ < 50° |
| M | -0.05 < M < 0.05 |
| X | 0 < X < 100 |
| t | 6 < t < 60 |

We are also given a CSV file (`xy_data.csv`) that contains a set of points that lie on this curve.

---

## 2) Key Idea and Approach

Since the dataset only provides (x, y) values but not the corresponding t values, we assume the points are sampled uniformly in the given range:

\[
t = \text{linspace}(6, 60, N)
\]

(where N is the number of data points)

To find θ, M, and X, we minimize the **L1 distance** between actual and predicted points:

\[
\text{Loss} = \sum |x_{\text{obs}} - x_{\text{pred}}| + |y_{\text{obs}} - y_{\text{pred}}|
\]

### Optimization Strategy Used

1. **Global random search** to find a good starting region  
2. **Local refinement step** (small adjustments to reduce error)

This method is reliable and avoids getting stuck in bad solutions.

---

## 3) Final Estimated Parameters

| Parameter | Value |
|----------|--------|
| θ (radians) | **0.490759** |
| θ (degrees) | **28.118416°** |
| M | **0.021389** |
| X | **54.900351** |

These values best match the given dataset according to the L1 loss criteria.

---

## 4) Final Curve 
(
tcos(0.490759) - e^(0.021389abs(t))sin(0.3t)sin(0.490759) + 54.900351,
42 + tsin(0.490759) + e^(0.021389abs(t))*sin(0.3t)*cos(0.490759)
)
Domain: 6 <= t <= 60

---

## 5) Result Plots

<p align="center">
  <img src="C:\Users\Nataraj\Downloads\obs_vs_fit.png" width="75%" alt="Observed vs Fitted">
</p>

<p align="center">
  <img src="C:\Users\Nataraj\Downloads\err_vs_t.png" width="75%" alt="Absolute Errors vs t">
</p>

<p align="center">
  <img src="C:\Users\Nataraj\Downloads\cum.png" width="75%" alt="Cumulative L1 Error">
</p>


## 6) Requirements
Python 3.x
numpy
pandas
matplotlib


