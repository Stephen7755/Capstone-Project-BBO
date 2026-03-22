# Bayesian Black-Box Optimisation Capstone Project

## Overview

This project implements a Bayesian Optimisation framework to efficiently optimise unknown functions under a limited query budget. The objective is to identify high-performing regions in a continuous search space (2D–8D) while minimising unnecessary evaluations.

Instead of sampling randomly, the method builds a probabilistic surrogate model using a Gaussian Process (GP). The GP estimates both the predicted value and uncertainty of unexplored regions. An acquisition function — Expected Improvement (EI) — is then used to balance exploration and exploitation when selecting the next query point.

Over multiple rounds, the model transitions from broad exploration to more focused refinement, demonstrating how uncertainty-aware optimisation improves efficiency.

---

## Technical Approach

The optimisation pipeline includes:

- Gaussian Process surrogate modelling
- Expected Improvement acquisition function
- Large-scale random candidate sampling
- Local optimisation using L-BFGS-B
- Multi-dimensional support (2D–8D)

Each round:
1. Fit GP to current data
2. Compute EI across candidate points
3. Select the best candidate
4. Refine locally
5. Save next query point

---

## Repository Structure
