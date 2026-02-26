# Model Card: GP-EI Bayesian Optimiser

## 1. Overview

**Model Name:** GP-EI Bayesian Optimiser  
**Type:** Surrogate-based Black-Box Optimisation  
**Version:** v1.0 (10-round iterative optimisation)

This approach uses a Gaussian Process surrogate model with an Expected Improvement acquisition function to propose new query points.

---

## 2. Intended Use

### Suitable For

- Expensive black-box optimisation problems
- Continuous search spaces (2D–8D)
- Limited evaluation budgets
- Educational or experimental optimisation tasks

### Not Suitable For

- Highly discontinuous or non-smooth functions
- Very high-dimensional problems (>15 dimensions)
- Real-time optimisation requiring instant responses

---

## 3. Strategy and Evolution Across Ten Rounds

### Rounds 1–3: Exploration-Focused

- Broad sampling to reduce global uncertainty
- Emphasis on learning function structure

### Rounds 4–7: Balanced Strategy

- Combined exploration and exploitation
- Expected Improvement used to guide trade-offs

### Rounds 8–10: Exploitation-Focused

- Concentrated sampling near best-performing regions
- Refinement of local optima
- Reduced exploration parameter (ξ)

### Core Techniques Used

- Gaussian Process regression (RBF kernel)
- Hyperparameter optimisation via log marginal likelihood
- Expected Improvement acquisition function
- Random candidate sampling
- Local optimisation with L-BFGS-B

---

## 4. Performance Summary

Performance was evaluated using:

- Best observed function value per round
- Convergence trends over iterations
- Stability of surrogate predictions

Across eight benchmark functions, the approach showed:

- Rapid early improvement
- Diminishing returns in later rounds
- Increased sensitivity in higher dimensions (6D–8D)

---

## 5. Assumptions and Limitations

### Key Assumptions

- The objective function is smooth
- Nearby inputs produce correlated outputs
- The search space is continuous and bounded

### Limitations

- Gaussian Processes scale poorly with large datasets
- Candidate sampling becomes less efficient in higher dimensions
- Risk of converging to local optima
- Potential sampling bias toward already promising regions

---

## 6. Ethical and Reproducibility Considerations

Transparency in documentation supports:

- Reproducibility of optimisation results
- Clear understanding of model assumptions
- Responsible adaptation in real-world settings

This repository includes:
- Full optimisation scripts
- Dataset files
- Explicit acquisition and kernel definitions

These details allow peers and reviewers to replicate and critique the approach.
