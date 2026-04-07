# Zero-Coverage-Prediction-for-Immunization-Sessions
This project develops a machine learning model to predict **zero coverage immunization sessions** — sessions where no beneficiaries are vaccinated despite being conducted. The goal is to support health authorities in identifying risky sessions early, improving resource allocation, and enhancing vaccination program efficiency.

 Objectives
- Predict zero coverage sessions (classification problem).
- Handle imbalanced datasets effectively.
- Avoid data leakage during model development.
- Evaluate models using **F1-score** as the primary metric.
- Identify key factors influencing zero coverage.


 **Business Context**
Immunization programs often face challenges where planned sessions result in **zero coverage**. A predictive system can:
- Flag underperforming sessions in advance.
- Reduce wastage of logistics and effort.
- Enable data-driven decision-making for better planning.

**Dataset**
- **Target Variable:** `Zero_Coverage`  
  - '1' → Zero vaccination (no beneficiaries vaccinated)  
  - '0' → Normal session
 
    **Final Feature Set:**
  - District  
  - Sub District  
  - Health Facility Name  
  - Session Site Name  
  - Session Planned  
  - Session Efficiency  

- **Data Cleaning:**
  - Removed leakage-prone columns (e.g., vaccination counts).
  - Removed invalid rows (e.g., “Delivery Point” sessions).
  - Handled duplicates (484 rows removed).
  - No missing values.

## Feature Engineering
- **Session Efficiency** = (Session Held / Session Planned) × 100  
- **Avg Vaccinated** = Total Vaccinated / Session Held  
- **Zero Coverage Definition:** Session held but no vaccination → `1`

## Model Development
- **Models Implemented:**
  - Random Forest Classifier (selected model)
  - Decision Tree Classifier (baseline)

- **Dataset Split:** Train (60%) / Test (40%)  
- **Evaluation Metrics:** Accuracy, Precision, Recall, F1-score  

### 📈 Results
- **Best Model:** Random Forest  
- **Confusion Matrix Insights:**
  - Correct Predictions:  
    - Normal sessions → 8049  
    - Zero coverage sessions → 5521  
  - Misclassifications:  
    - False Positives → 3720  
    - False Negatives → 4516  

**The model misses some zero-coverage sessions, which is critical in real-world scenarios.**

## Key Insights
- Zero coverage cases are minority but highly important.
- **Session efficiency** is the strongest predictor.
- Location-based features (district, facility) influence performance.
- Most sessions have low vaccination averages.

## Recommendations
- Monitor districts with frequent zero coverage.
- Improve planning for low-performing session sites.
- Use model predictions for **early intervention**.

## Usage
- **Input:** Session planning details  
- **Output:** Prediction (`Zero Coverage` / `Normal Coverage`)  

## Conclusion
The Random Forest model provides a practical solution for predicting zero coverage immunization sessions. While improvements are needed to reduce missed cases, this system can significantly enhance vaccination program efficiency by enabling proactive interventions.



