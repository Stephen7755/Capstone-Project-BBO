1. Project Overview

This capstone project investigates Bayesian Black-Box Optimisation (BBO), a method for optimising unknown functions when evaluations are expensive and limited. The true objective function is not accessible directly and can only be queried occasionally, so each query must be chosen carefully.

The goal of the project is to efficiently find inputs that minimise or maximise the unknown function using as few evaluations as possible. This is achieved by learning a surrogate model from past queries and using it to guide future sampling decisions. 

2. Inputs, Outputs, and Objectives
Inputs

Previously evaluated input points stored in a NumPy array of shape (N, d)

Corresponding observed outputs stored in a NumPy array of shape (N,)

The input space is continuous and may be high-dimensional. True bounds are not always known and are inferred from observed data.

Outputs

A single proposed next query point of shape (d,)

Objective

The objective is to optimise an unknown black-box function under a strict query budget. Depending on the task, this involves either minimising or maximising the function while accounting for delayed feedback and the absence of gradient or structural information.

3. Technical Approach

A Gaussian Process (GP) is used as a surrogate model to approximate the unknown function. GPs are chosen because they provide both predictions and uncertainty estimates, which are essential for guiding query decisions.

New query points are selected using the Expected Improvement (EI) acquisition function, which balances:

Exploitation of regions predicted to perform well

Exploration of regions with high uncertainty

The acquisition function is optimised using random candidate sampling combined with local optimisation (L-BFGS-B) to ensure both global coverage and local refinement.

4. Strategy Evolution, Limitations, and Lessons

Early query rounds focus on exploration to reduce overall uncertainty, while later rounds place greater emphasis on exploiting promising regions. This adaptive strategy improves efficiency as more data become available.

Key limitations include the computational cost of Gaussian Processes as data grow, reduced performance in high-dimensional spaces, and the presence of potentially irrelevant input dimensions. Despite these challenges, the project highlights the importance of uncertainty-aware decision-making and iterative learning.

Overall, this capstone reflects real world data science scenarios where information is incomplete, data are costly to obtain, and careful modelling and experimentation are required.
