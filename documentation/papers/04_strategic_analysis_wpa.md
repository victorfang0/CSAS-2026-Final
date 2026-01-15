# Part 4: Strategic Analysis (WPA)

## 1. Counterfactual Simulation
Using the trained Win Probability model ($f(\vec{x})$), we conducted a comprehensive simulation to quantify the strategic value of the Power Play.

### Methodology
To isolate the effect of the Power Play, we compared two hypothetical game states for every combination of Score Differential ($S$) and End Number ($E$):
1.  **Scenario A (Power Play):** $\vec{x}_{pp} = \{E, S, H=1, PP=1\}$
2.  **Scenario B (Standard):** $\vec{x}_{norm} = \{E, S, H=1, PP=0\}$

We define the comparative gain as:
$$
WPA = P(Win | \vec{x}_{pp}) - P(Win | \vec{x}_{norm})
$$


## 2. Calculating the Gain
We simply subtract the two probabilities to find the marginal utility:
$$
\Delta P = P_{win}^{pp} - P_{win}^{norm}
$$

$$
\Delta P = 0.45 - 0.35 = +0.10
$$

In this scenario, using the Power Play increases our chance of winning by **10%**. That is huge. That is worth doing.

## 2. Quantitative Findings

### The "Catch-Up" Principle ($S < 0$)
The heatmap reveals a strong positive WPA when trailing, particularly in Ends 5-7.
*   **Mechanism:** The Power Play increases scoring variance ($\sigma^2_{score}$). When the expected outcome of a standard end is a loss ($P(Win) < 0.5$), introducing high variance (the opportunity for a large score) improves the probability of a comeback.

### The "Risk Assessment" Principle ($S > 0$)
Conversely, when leading, the Power Play yields a negative WPA.
*   **Mechanism:** When $P(Win) > 0.5$, risk minimization is optimal. The "Open Board" state introduces unnecessary volatility that jeopardizes the lead.

## 3. Opportunity Cost Optimization
Since the Power Play is a finite resource (one use per game), optimal usage requires comparing the *current* gain ($g_t$) against the *expected future* gain ($E[G_{future}]$).

$$
\text{Optimal Decision: } \text{Activate if } g_t > E[\max(g_{t+1}, \dots, g_8)]
$$

Our analysis indicates that reserving the Power Play for high-leverage late-game deficits (e.g., End 6, down by 2) is significantly more valuable than expending it for marginal gains in early ends.
