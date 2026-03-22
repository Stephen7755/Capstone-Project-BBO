# Model Card: GP-EI Bayesian Optimiser

## Overview

Model Name: GP-EI Bayesian Optimiser  
Version: v1.0 Final Submission  
Model Type: Surrogate-based Bayesian Optimisation  

---

## Intended Use

Suitable for:

- Expensive black-box optimisation problems
- Continuous low- to moderate-dimensional spaces
- Educational research

Not suitable for:

- Highly discontinuous functions
- Very high-dimensional problems (>15D)
- Real-time large-scale industrial optimisation

---

## Model Description

The model uses:

1. Gaussian Process surrogate modelling
2. Expected Improvement acquisition function
3. Large-scale random sampling
4. Local refinement with L-BFGS-B

The strategy evolved from exploration-heavy early rounds to more exploitative later rounds.

---

## Performance Summary

- Strong improvements in early rounds
- Gradual convergence in mid-phase
- Diminishing returns in final iterations
- Increased instability in higher dimensions (6D–8D)

---

## Assumptions

- Underlying function smoothness
- Bounded search space
- Reliable GP uncertainty estimation

---

## Limitations

- Computational scaling of Gaussian Processes
- Risk of local optima trapping
- Curse of dimensionality
- Candidate sampling inefficiency in higher dimensions

---

## Ethical Considerations

Full transparency of code, dataset, and assumptions supports reproducibility. This project is educational and avoids high-stakes deployment contexts.
