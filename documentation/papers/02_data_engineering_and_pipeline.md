# Part 2: Data Engineering

## 1. Data Cleaning & Integration
The dataset consisted of two primary files: `Ends.csv` (score data) and `Games.csv` (match metadata). A critical initial step involved resolving identifier ambiguities.

### Identifier Resolution (Composite Keys)
The `GameID` field is not globally unique; it is only unique within a specific `CompetitionID`. Merging solely on `GameID` would result in severe data leakage (mixing ends from different tournaments).
*   **Solution:** We constructed a composite primary key using (`CompetitionID`, `GameID`) to ensure 1:1 mapping between match metadata and end-by-end scoring.


## 2. Feature Engineering
Reflecting the nuances of Curling in a machine-readable format required constructing state-based features.

*   **Hammer (Last Rock Advantage):** 
    *   Determined by tracking scoring history. The team that scores > 0 points relinquishes the Hammer in the subsequent end. We implemented logic to propagate this state end-accordingly.
*   **Score Differential:**
    *   Calculated as `Own_Score - Opponent_Score` relative to the team holding the decision rights. This captures the urgency of the game state (e.g., trailing by 2 vs. leading by 1).

The processed dataset was serialized to `modeling_data.csv` for training.
