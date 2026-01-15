# Part 1: Strategic Methodology

## 1. Introduction: Mixed Doubles Curling
Mixed Doubles Curling differs from the traditional game by having only two players per team and a faster pace of play. The game is characterized by high scoring and aggressive tactics.

### The Power Play
A key strategic element is the **Power Play**, which teams can exercise once per game.
*   **Mechanic:** Moving the stationary "pre-placed" stones from the center line to the side wings.
*   **Strategic Implication:** This creates an "Open Board" state, increasing variance and the potential for multi-point ends.

## 2. Research Objective
The primary objective of this analysis is to quantify the optimal usage of the Power Play. Specifically:
> *Under what Game State conditions (Score Differential, End Number) does maximizing the Power Play yield the highest increase in Win Probability?*

## 3. Methodology: Win Probability Added (WPA)
Traditional analysis often relies on **Expected Points ($E[P]$)**. However, in late-game scenarios, maximizing points does not always equate to maximizing victory.
*   *Example:* Leading by 8 points in the final end requires risk minimization, not point maximization.

### The "WPA" Metric
We define the **Win Probability Added (WPA)** as the comparative gain in win probability derived from a specific strategic decision (calling the Power Play).

We define the Game State vector $\vec{x}$ as:
$$
\vec{x} = \{ \text{ScoreDiff}, \text{EndNumber}, \text{Hammer} \}
$$

The Win Probability function $f(\vec{x})$ gives us the probability of winning given state $\vec{x}$.
$$
P(Win) = f(\vec{x})
$$

Therefore, the value of the Power Play is the **Comparative Gain**:
$$
WPA(\vec{x}) = P(Win | \vec{x}, PowerPlay=1) - P(Win | \vec{x}, PowerPlay=0)
$$

**Our Strategy:** We will build an AI model to estimate the function $f(\vec{x})$ for every possible game state.
