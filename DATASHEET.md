# Datasheet for the BBO Capstone Dataset

## Motivation

This dataset was created to support iterative Bayesian Black-Box Optimisation experiments. The objective is to evaluate how surrogate modelling and acquisition-based strategies perform when optimising unknown functions under limited evaluation budgets.

---

## Composition

The dataset consists of:

- Input query points (NumPy arrays, shape: N × D)
- Output values (NumPy arrays, shape: N)

Dimensions evaluated: 2D–8D  
Data grows sequentially across rounds.

No missing values exist. Later rounds exhibit clustering due to exploitation behaviour.

---

## Collection Process

Queries were generated using:

- Gaussian Process surrogate modelling
- Expected Improvement acquisition
- Random global candidate search
- Local refinement via gradient-based optimisation

Early rounds emphasised exploration. Later rounds focused on refining promising regions.

---

## Preprocessing

Minimal preprocessing was applied. In some iterations, feature scaling was used for numerical stability of GP length scales.

---

## Intended Uses

- Educational optimisation research
- Demonstrating Bayesian optimisation principles
- Surrogate modelling experiments

---

## Inappropriate Uses

- Real-world decision-making
- Safety-critical optimisation
- High-dimensional large-scale industrial systems

---

## Distribution and Maintenance

The dataset is publicly available in this GitHub repository. It is maintained by the project author for academic use.
