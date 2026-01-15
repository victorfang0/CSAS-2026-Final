# Part 5: Visualization & Mapping

## 1. Coordinate System Calibration
To map the raw stone coordinates $(x_i, y_i)$ to physical sheet dimensions, we performed a density-based spatial analysis.

### Centroid Identification ("The Button")
We modeled the aggregate stone locations as a 2D probability density function:
$$
D(x, y) = \frac{1}{N} \sum_{i=1}^{N} \mathbb{I}(x_i, y_i)
$$

**Calibration Point:**
The centroid $(\mu_x, \mu_y)$ of the high-density cluster corresponds to the geometric center of the House (the "Button").
$$
\mu_x \approx 765, \quad \mu_y \approx 740
$$


## 2. Finding the Scale ($\lambda$)
We needed to determine the conversion factor $\lambda$ (pixels per foot).
*   We measured the variance of the stone cluster distribution.
*   We observed that the cluster density drops to near-zero at a radius $r_{pixel} \approx 600$.
*   We know the standard World Curling Federation House radius is $r_{real} = 6$ feet.
$$
\lambda = \frac{r_{pixel}}{r_{real}} = \frac{600 \text{ px}}{6 \text{ ft}} = 100 \text{ px/ft}
$$

## 3. Drawing the Diagram
Once we had the Center $C(765, 740)$ and the Scale $\lambda = 100$, we could define the House geometrically.
We drew circles for the standard rings:
*   **12-Foot Ring:** $R_{12} = 6 \text{ ft} \times 100 = 600 \text{ px}$
*   **8-Foot Ring:** $R_{8} = 4 \text{ ft} \times 100 = 400 \text{ px}$
*   **4-Foot Ring:** $R_{4} = 2 \text{ ft} \times 100 = 200 \text{ px}$
*   **Button:** $R_{1} = 0.5 \text{ ft} \times 100 = 50 \text{ px}$

When we overlaid the actual data on top of our drawing, it lined up perfectly. This confirms our linear transformation model was correct.

## 4. Strategic Application
This coordinate mapping enables precise spatial analysis, specifically for evaluating guard placement efficacy.
*   **Optimization Function:** We can now determine the optimal guard vector $\vec{v}_{opt}$ by maximizing the conditional probability of winning:
$$
\vec{v}_{opt} = \text{argmax}_{\vec{v}} P(Win | \vec{v})
$$

