# FLAM
REPORT — Parameter Estimation using L1 Optimization

🔹 Problem Statement
The given dataset (xy_data.csv) contains two columns — x and y — representing observed values of a parametric curve. 
We are required to estimate the unknown parameters θ, M, and X from the following parametric equations:

x(t) = t*cos(θ) - e^(M|t|)*sin(0.3t)*sin(θ) + X
y(t) = 42 + t*sin(θ) + e^(M|t|)*sin(0.3t)*cos(θ)

for 6 < t < 60.

The objective is to find values of θ, M, and X that minimize the L1 distance (sum of absolute differences) 
between observed and predicted data points.

🔹 Input Description
- Input file: xy_data.csv
- Columns:
  • x → observed x-values
  • y → observed y-values
- Number of data points: 1500
- Parameter t: uniformly sampled from 6 to 60.

🔹 Approach / Methodology
1. Model Formulation:
   Implemented the given parametric equations using NumPy.

2. Loss Function (L1 Distance):
   L1 = Σ|x_pred - x_obs| + Σ|y_pred - y_obs|

3. Optimization Technique:
   - Used scipy.optimize.minimize() with Nelder–Mead method.
   - Parameter bounds:
       0° ≤ θ ≤ 50°
       -0.05 ≤ M ≤ 0.05
       0 ≤ X ≤ 100
   - Initial guess: [20.0, 0.0, 10.0]
   - Recorded L1 loss convergence during optimization.

4. Visualization:
   - L1 loss convergence curve
   - x vs t and y vs t plots
   - (x, y) parametric curve visualization

5. Output Files Generated:
   - xy_fit_L1_results.csv → t, x_obs, y_obs, x_pred, y_pred
   - Find_Parameters_L1.ipynb → code + plots

🔹 Results
Estimated Parameters:
  θ (degrees) = 29.582815
  θ (radians) = 0.51655
  M = -0.05000000
  X = 55.013610
  Final L1 Loss ≈ (see notebook output)

Optimization:
  ✓ Converged successfully (ftol termination condition met)
  ✓ M reached lower bound (-0.05)

🔹 Final LaTeX / Desmos Expression
(t*cos(0.51655) - e^(-0.05*abs(t))*sin(0.3*t)*sin(0.51655) + 55.0136,
 42 + t*sin(0.51655) + e^(-0.05*abs(t))*sin(0.3*t)*cos(0.51655))

🔹 Observations
- The predicted curve closely matches the observed data.
- L1 loss ensures robustness against outliers.
- The convergence graph confirms successful optimization.

🔹 Conclusion
The parameters θ, M, and X were successfully estimated using L1 optimization.
The final values θ = 29.58°, M = -0.05, and X = 55.01 provide a strong fit to the observed data.
This approach achieves minimal L1 distance and high accuracy.

🔹 Files Submitted
1. Find_Parameters_L1.ipynb  → Main notebook with code + visualizations
2. xy_data.csv               → Input data
3. xy_fit_L1_results.csv     → Predicted output
4. Report.txt                → Explanation and results summary
