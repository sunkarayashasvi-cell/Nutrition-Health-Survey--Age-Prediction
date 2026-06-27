# Summer Analytics 2026 Hackathon - Rank 9 Solution 🏆

This repository contains my **Top 10 (Rank 9)** solution for the Summer Analytics 2026 Camp Machine Learning Hackathon. 

## 🎯 Project Objective
The task is a binary classification challenge aimed at predicting whether an individual belongs to the `Adult` (0) or `Senior` (1) age bracket based solely on clinical measurements, physical activity records, and laboratory blood biomarkers.

## 📊 Key Challenges & Solutions
* **Missing Targets:** Identified and removed rows in the training data with missing classification labels to prevent training errors.
* **Severe Class Imbalance:** The dataset was heavily skewed (83.91% Adult / 16.09% Senior). Addressed this structurally using cost-sensitive learning (`scale_pos_weight`) to force the trees to actively prioritize rare Senior flags.
* **Data Imputation:** Gaps in laboratory features (Insulin, Glucose) were cleanly handled using median imputation to remain robust against outliers without introducing data leakage.

## 🛠️ The Winning Machine Learning Pipeline
Instead of relying on standard architectures or overfitting to the public leaderboard, the solution uses a highly engineered **5-Seed XGBoost Ensemble**:
1. **Clinical Feature Engineering:** Synthesized explicit metabolic biomarkers, including the *Triglyceride-Glucose (TyG) interaction index* and *BMI-Glucose Stress metrics*, to make subtle boundary lines obvious to the model.
2. **Sequential Multi-Seed Boosting:** Evaluated an optimized gradient boosting layout across 5 distinct random initializations to smooth variance and eliminate random flukes.
3. **Targeted Probability Calibration:** Shuffled decision thresholds down to a fine-tuned **15% senior selection density**. This optimized the precision/recall trade-off, breaking a heavy leaderboard plateau and locking in **Rank 9**.

## 📦 File Layout
* `Summer_Analytics_Hackathon.ipynb`: End-to-end operational pipeline (EDA, engineering, and model cross-validation).
* `submission.csv`: Final optimized predictions.
