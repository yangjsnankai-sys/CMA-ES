
Overview
This code implements a CMA-ES optimization framework for tuning system parameters using Simulink simulation. While originally developed for parafoil landing optimization, the framework is generic and can be adapted to various Simulink models. The parafoil controller model has been fully processed and serves as a ready-to-use template - readers can directly embed their own models for optimization.

File Structure
run_cmaes_parafoil.m - Main optimization driver

objective_parafoil_height_wrapper.m - Objective function evaluator

parafoil_CMA.slx - Pre-processed Simulink template (parafoil controller model)

Key Features
Parallel Evaluation: Uses MATLAB parallel computing for efficient population evaluation

Vectorized CMA-ES: Optimized for batch processing of candidate solutions

Robust Simulation: Handles simulation failures gracefully with penalty assignment

Noise Reduction: Multiple simulation repetitions with median aggregation

Fixed Initial Conditions: Ensures consistent simulation starting points

Plug-and-Play Architecture: The provided parafoil model is fully processed - users can directly replace it with their own models

Quick Start
Integrate Your Model: Replace the pre-processed parafoil_CMA.slx with your own Simulink model

Configure Variables: Ensure your model has tunable parameters (like height_action in the example)

Set Up Logging: Model must output evaluation signals (like episodeReward)

Run Optimization: Execute run_cmaes_parafoil() directly - no additional coding required

Configuration Parameters
Search Range: 3.0-20.0 meters with 0.2m quantization step (adjustable for your model)

Population Size: 12 candidates per generation

Max Evaluations: 200 total function evaluations

Repetitions: 5 simulations per candidate for noise reduction

Output Results
Optimal Parameters: Best solution (like trigger height h*) 

Performance Metrics: Corresponding evaluation results (like reward value)

Results File: cma_out1.mat containing all optimization data
