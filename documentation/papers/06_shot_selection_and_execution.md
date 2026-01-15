# Part 6: Shot Selection & Execution Analysis

## 1. Spatial Optimization Hypothesis
Following the strategic identification of *when* to use the Power Play, we investigated *how* to execute it. Specifically, we tested the hypothesis that successful outcomes are correlated with a distinct spatial distribution of the Corner Guard.

### Cohort Analysis
We segmented Power Play ends ($N=598$) into two performance cohorts:
1.  **High-Yield (Success):** Ends resulting in a score of $\ge 3$ points.
2.  **Low-Yield (Failure):** Ends resulting in a Steal ($\le 0$ points).


## 2. The Methodology
We used our Coordinate System from Step 5.
We extracted the location vector $\vec{v}_i = (x_i, y_i)$ for the first thrown stone in $N=598$ Power Play ends.
We calculated the **Centroid** (Average Position) for both groups:

$$
\vec{\mu}_{win} = \frac{1}{N_{win}} \sum \vec{v}_{win}
$$

$$
\vec{\mu}_{loss} = \frac{1}{N_{loss}} \sum \vec{v}_{loss}
$$

## 3. The Result (The Null Hypothesis)
We expected to see two different clusters.
Instead, we found this:

*   **Winning Guard Location:** $\mu_x \approx 796.9$ px
*   **Losing Guard Location:** $\mu_x \approx 803.2$ px
*   **Difference:** $\Delta x \approx 6.3$ pixels.

**Context:**
Since our scale is $\lambda = 100$ px/ft, a difference of 6 pixels is **0.06 feet**, or roughly **0.7 inches**.
In a game played on a 150-foot sheet of ice, with 40-pound rocks, a difference of 0.7 inches is **statistically negligible**.

## 4. Interpretation: Strategic Equilibrium
The lack of spatial separation confirms a **Strategic Equilibrium**.
*   The "Optimal Placement" is known and universally adopted by elite teams.
*   Variance in outcome is therefore driven by **Execution** (precision) and subsequent shot management, rather than initial strategic differentiation.

## 5. Implications for Training
*   **Mechanics over Tactics:** Since the initial guard placement is standardized, training should focus on the consistency of hitting this coordinate ($\sigma^2_{placement} \to 0$).
*   **Decision Weight:** The strategic leverage lies in the *binary decision* to call the Power Play (as derived in Part 4), rather than the micro-adjustments of stone placement.
