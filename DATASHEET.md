# Datasheet for the BBO Capstone Dataset

## 1. Motivation

This dataset was created to support a Bayesian Black-Box Optimisation (BBO) capstone project. The purpose of the dataset is to iteratively optimise unknown objective functions under a strict query budget.

The dataset supports:
- Minimisation of unknown functions
- Evaluation of exploration–exploitation trade-offs
- Analysis of surrogate modelling behaviour in 2D–8D search spaces

The project simulates real-world optimisation scenarios where evaluations are expensive and the true objective function is not directly accessible.

---

## 2. Composition

The dataset consists of:

- Input query points stored as NumPy arrays of shape `(N, d)`
- Corresponding observed outputs stored as arrays of shape `(N,)`
- Multiple dimensional configurations (2D–8D)

The dataset grows incrementally across ten optimisation rounds. Each round adds one new query point and its observed output.

There are no missing values. However, later rounds show clustering of samples near promising regions due to increased exploitation.

---

## 3. Collection Process

The dataset was generated sequentially through Bayesian optimisation.

Each new query point was selected using:
- A Gaussian Process (GP) surrogate model
- Expected Improvement (EI) acquisition function
- Random candidate sampling
- Local optimisation refinement (L-BFGS-B)

Early rounds emphasised exploration due to high uncertainty.
Later rounds prioritised exploitation near regions predicted to yield better performance.

The dataset was collected iteratively over ten rounds, with each submission informed by previous observations.

---

## 4. Preprocessing and Uses

Minimal preprocessing was applied.

In some iterations:
- Inputs were standardised before GP fitting
- Search bounds were inferred from observed data

No synthetic data augmentation was used.

### Intended Uses

- Benchmarking black-box optimisation strategies
- Studying surrogate model behaviour
- Educational demonstrations of Bayesian optimisation

### Inappropriate Uses

- Training supervised prediction models unrelated to optimisation
- Drawing conclusions about real-world systems (as the functions are synthetic benchmarks)

---

## 5. Distribution and Maintenance

The dataset is stored in this public GitHub repository as `.npy` files.

It is intended for academic and educational use.

The repository owner maintains the dataset and updates it with each optimisation round.
