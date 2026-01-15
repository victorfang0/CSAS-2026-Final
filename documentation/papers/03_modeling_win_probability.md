# Part 3: Win Probability Model

## 1. The Challenge: Sparse Data
A common approach to estimating win probability is a simple lookup table (i.e., historical win rates for a given state). However, this method suffers from **data sparsity** in specific scenarios.
*   *Issue:* Rare game states (e.g., Trailing by 2 in End 6 with Hammer) may have insufficient historical examples to form a statistically significant probability.

## 2. Model Selection: Random Forest
To address sparsity and capture non-linear interactions, we employed a **Random Forest Classifier**. As an ensemble learning method, it mimics the "Expert Committee" approach by aggregating predictions from multiple decision trees.

### Feature Interaction
The model evaluates features simultaneously, allowing it to learn complex heuristics.
*   *Example:* Scores in early ends might weigh less than scores in late ends.
*   *Example:* Identifying that "Hammer" combined with "Trailing" has a different value proposition than "Hammer" with "Leading".

## 3. Model Results & Calibration
We evaluated the model using a Stratified 80/20 Train-Test split to ensure robust performance.
*   **Performance:** The model achieved an **AUC of 0.89** on the test set.
*   **Interpretation:** This high Area Under Curve score indicates precise discrimination between winning and losing positions, validating the model as a reliable "Virtual Expert" for simulating counterfactual strategic scenarios.
