# failed_sleep_health_ml
### Final Project Report: Sleep Health & Lifestyle Classification

#### 🎯 Project Goal
Develop a machine learning model to automatically diagnose sleep disorders (Insomnia, Sleep Apnea) based on lifestyle indicators and health metrics.

#### 🛠 Tried Pipeline & Experiments
1. **Feature Importance Analysis:** Evaluated feature weights using a Random Forest model. Identified that features like stress level and systolic blood pressure introduced more noise than signal for this specific sample size, and subsequently removed them.
2. **Class Imbalance Handling (SMOTE):** Attempted to generate synthetic data to overcome a critical class bottleneck (only 4 Sleep Apnea patients in the test set vs. 59 healthy individuals).
3. **Feature Scaling (StandardScaler):** Normalized numerical features (Steps, Heart Rate, Age) to equalize their mathematical weight, ensuring SMOTE distance metrics operated correctly.
4. **Machine Learning Algorithms:** Benchmarked a baseline `RandomForestClassifier` against an industry-standard gradient boosting model (`XGBClassifier`).
5. **Product Pivot (Binary Triage):** Transformed the task from multi-class classification into a binary triage system ("None" vs. "Sleep_Disorder") to aggregate weak signals and simplify the decision boundaries.

#### Key Insights & Successes
* The models successfully captured valid biological patterns: the strongest predictors for sleep issues were physical activity levels, BMI categories, and age.
* Mathematically disproved a direct linear correlation between `Daily Steps` and `Physical Activity Level` (minutes/day), validating the decision to keep both features as independent sources of information.
* Shifting to a binary approach allowed the algorithm to break the zero-recall barrier for patients with sleep issues.

#### Limitations & Failure Analysis
* **Extreme Data Scarcity:** The sample size for active disorders was too small to allow complex gradient boosting trees to generalize properly without overfitting.
* **Class Overlap (Lack of Signal):** In this dataset, healthy individuals and those with disorders share nearly identical physiological boundaries. The signal is heavily drowned out by noise.
* **Conclusion:** The maximum F1-score achieved for the disorder class was 0.21. This model is not production-ready due to a dangerously high risk of missing real patients (False Negatives). A broader data collection phase with more distinct physiological biomarkers is highly recommended.
