Santa 2025 – Christmas Tree Packing Challenge

This repository contains my final solution for the **Kaggle Santa 2025 – Christmas Tree Packing Challenge.
The goal of the competition is to pack n = 1..200  identical Christmas tree shapes into the smallest possible **axis-aligned square**, minimizing the normalized area score:

\[\text{score} = \sum_{n=1}^{200} \frac{s_n^2}{n}\]
where \( s_n \) is the side length of the bounding square for the `n`-tree configuration.

 Key Constraints

- Exact tree shape **is not provided**
- Overlap checking and scoring are done **server-side**
- No local evaluator is available
- Solutions must rely on **blind geometric reasoning**

Approach

1. Hexagonal Lattice Packing
- Used a triangular (hex) lattice with a safe spacing:
 - HEX_STEP = 0.8
- Ensures no overlaps across all configurations

2. Metric-Aware Ordering
- Points are ordered by **Chebyshev distance**:
- Primary: max(|x|, |y|)
- Secondary: Euclidean distance
- Aligns directly with the square bounding box metric
3. Targeted Optimization for Small n
- For n ≤ 9, a slightly larger spacing is used:
- HEX_STEP_SMALL = 0.85
- This reduces bounding square size for early configurations
- Larger n use the global optimal lattice

4. No Rotation
- All trees use deg = 0
- Rotation attempts consistently caused overlaps due to unknown shape

Final Result

- Final Kaggle Score: 134.925769524
- Submission Status: Complete (no overlaps)
- Method:  Blind geometric optimization (no shape access)
