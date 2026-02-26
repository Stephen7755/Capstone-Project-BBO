Bayesian Black-Box Optimisation (BBO) Capstone Project
1. Project Overview

This capstone project investigates Bayesian Black Box Optimisation (BBO), a method for optimising unknown functions when evaluations are expensive, limited, or slow. In this setting, the true objective function is not directly accessible and can only be queried occasionally, so each query must be selected carefully.

The aim of the project is to efficiently identify input values that minimise or maximise the unknown function using as few evaluations as possible. This is achieved by learning a surrogate model from previously observed data and using it to guide the selection of future query points.

This problem setting reflects many real world machine learning and data science tasks, such as hyperparameter tuning, simulation based optimisation, and experimental design, where evaluations are costly and information is incomplete.

2. Inputs, Outputs, and Objectives
Inputs

The optimisation procedure uses:

Previously evaluated input points stored in a NumPy array of shape (N, d)

Corresponding observed outputs stored in a NumPy array of shape (N,)

The input space is continuous and may be multi dimensional. True domain bounds are not always known in advance and are inferred from the observed data. In later stages of the project, engineered features are used to extend the inputs from lower dimensions (e.g. 2D) to higher dimensional settings (up to 8D).

Outputs

The model produces:

A single proposed next query point of shape (d,)

This output represents the next input to be evaluated by the black-box function.

Objective

The objective is to optimise an unknown black box function under a strict query budget. Depending on the task, this involves either minimising or maximising the function while accounting for:

Limited evaluations

Delayed feedback

No access to gradients or analytical structure

3. Technical Approach

A Gaussian Process (GP) is used as the surrogate model to approximate the unknown objective function. GPs are chosen because they provide both:

Predictive mean estimates

Quantified uncertainty

This uncertainty information is critical for deciding where to sample next.

New query points are selected using the Expected Improvement (EI) acquisition function. EI balances:

Exploitation of regions predicted to perform well

Exploration of regions where the model is uncertain

The acquisition function is optimised using a two stage approach:

Random candidate sampling to provide global coverage of the input space

Local optimisation using L-BFGS-B to refine promising candidates

This approach improves robustness and reduces the risk of poor local solutions.

4. Strategy Evolution, Limitations, and Lessons

In early rounds, the optimisation strategy prioritises exploration to reduce global uncertainty and learn the broad structure of the function. As more data are collected, the strategy gradually shifts toward exploitation, focusing on refining regions that are known to perform well.

To study higher dimensional behaviour, the project extends the original inputs using structured feature expansion (e.g. interaction terms and smooth nonlinear features). This allows the same optimisation logic to be applied consistently from 2D up to 8D.

Key limitations of the current approach include:

The computational cost of Gaussian Processes as the dataset grows

Reduced performance in higher dimensional spaces with limited data

The possibility of irrelevant or weakly informative input dimensions

Despite these limitations, the project demonstrates the value of uncertainty aware decision making, iterative refinement, and careful experiment design.

Overall, this capstone reflects real world data science scenarios where information is incomplete, data are expensive to obtain, and progress depends on making informed, sequential decisions rather than relying on exhaustive search.

## Documentation

- [Datasheet](DATASHEET.md)
- [Model Card](MODEL_CARD.md)
