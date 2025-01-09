# Sports Game Prediction Using XGBoost

## Project Overview
This project is a pipeline to predict sports game outcomes using the XGBoost algorithm. It involves two main stages: **data preprocessing** and **model training/prediction**. The goal is to leverage game statistics, custom features, and machine learning techniques to achieve higher prediction accuracy.

---

## Files in the Project
### 1. **`PreprocessData.ipynb`**
- **Purpose**: Gathers game statistics over a specified number of seasons (we used **7 seasons** in this project).
- **Key Steps**:
  - Preprocesses the raw data, cleaning and formatting it for machine learning.
  - Adds **custom features** to improve the model's prediction accuracy:
    - **`WL` Conversion**: Converts win/loss outcomes into binary values (`0` for loss, `1` for win).
    - **`DaysSinceLastGame`**: Calculates the number of days since the team's last game.
    - **`IS_HOME_GAME`**: Encodes whether the game was played at home (`1`) or away (`0`).
    - **Custom "Injury Penalty" Feature**:
      - Grades each player based on their in-season performance, assigning a rating out of 100.
      - Quantifies the impact of player injuries on team performance by summing the "importance" ratings of injured players.
  - Produces a **preprocessed dataset** (`output.csv`) for use in the next step.

### 2. **`output.csv`** (Generated Output File)
- Contains the preprocessed dataset with all added features.
- This file serves as the input for the XGBoost training and evaluation notebook.

### 3. **`XGBoost.ipynb`**
- **Purpose**: Implements the XGBoost algorithm to predict game outcomes using the preprocessed data.
- **Key Steps**:
  - Trains the model on the preprocessed dataset, leveraging the custom input variables created in the preprocessing step.
  - Evaluates the model's performance using key metrics:
    - **Log Loss**: Measures how well the model predicts probabilities.
    - **ROC-AUC Score**: Evaluates the model's ability to separate wins and losses.
    - **Accuracy**: Measures overall prediction correctness.
  - Fine-tunes hyperparameters and uses custom features (e.g., "Injury Penalty") to improve prediction accuracy.

---

## How to Use the Project
### Prerequisites
- Python 3.x
- Required libraries:
  - `pandas`
  - `numpy`
  - `scikit-learn`
  - `xgboost`
  - `matplotlib`
  - `jupyter` (to run `.ipynb` files)

### Steps to Run the Project
1. **Run Preprocessing**:
   - Open `PreprocessData.ipynb`.
   - Configure the seasons to gather stats for (default is 7 seasons).
   - Execute all cells to generate the preprocessed dataset (`output.csv`).

2. **Train the Model**:
   - Open `XGBoost.ipynb`.
   - Load the preprocessed dataset (`output.csv`).
   - Train the XGBoost model and evaluate its performance using the included metrics.

---

## Custom Features
### 1. `DaysSinceLastGame`
- Captures the time gap between games, which can affect team performance due to rest or fatigue.

### 2. `IS_HOME_GAME`
- Encodes whether a game is played at home (`1`) or away (`0`), accounting for home-court advantage.

### 3. "Injury Penalty"
- Quantifies the impact of injuries on game performance:
  - Each player is assigned a rating (out of 100) based on their seasonal stats.
  - The total penalty for a game is calculated as the sum of ratings for all injured players.

---

## Model Performance Metrics
- **Log Loss**: Evaluates the accuracy of the predicted probabilities.
- **ROC-AUC**: Measures the model's ability to rank games correctly (higher is better).
- **Accuracy**: Reflects the percentage of correctly predicted outcomes.

---

## Conclusion
This project demonstrates how careful feature engineering (e.g., custom injury penalties) combined with a powerful machine learning algorithm like XGBoost can yield improved predictions for sports game outcomes. The modular structure allows easy adaptation for different datasets, sports, or custom features.

Feel free to contribute or adapt this project to suit your needs. Happy coding! 🚀

