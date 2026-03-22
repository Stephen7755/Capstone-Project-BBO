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
BBO-Capstone/
│
├── BBO_Optimisation_Notebook.ipynb
├── initial_inputs.npy
├── initial_outputs.npy
├── DATASHEET.md
├── MODEL_CARD.md
├── requirements.txt
└── README.md

---

## Key Results

- Strong early improvement from exploratory sampling
- Gradual convergence toward high-performing regions
- Increased dimensional sensitivity at 6D–8D
- Clear transition from exploration to exploitation

---

## Reproducibility

1. Install dependencies: pip install -r requirements.txt
2. Open and run: BBO_Optimisation_Notebook.ipynb


All query points will be regenerated automatically.

---

## Author: STEPHEN SEFA

Final Submission – Bayesian Black-Box Optimisation Capstone
