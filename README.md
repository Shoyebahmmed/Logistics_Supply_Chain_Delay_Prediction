# Supply Chain Risk Classification Using Machine Learning

## Project Overview

This project explores the use of machine learning techniques to analyze logistics and supply chain data in order to classify delivery risks. The goal is to identify whether a shipment falls into **High Risk**, **Moderate Risk**, or **Low Risk** categories based on operational, environmental, and logistical factors.

The project demonstrates a complete machine learning workflow including data exploration, correlation analysis, feature importance analysis, model training, and performance evaluation.

This work was developed as part of a data analytics assignment to understand how predictive models can support decision-making in logistics operations.

---

## Dataset

The project uses two logistics-related datasets:

1. **Smart Logistics Dataset**
2. **Dynamic Supply Chain Logistics Dataset**

These datasets contain operational metrics such as:

- GPS location of vehicles
- Fuel consumption
- Traffic congestion levels
- Warehouse inventory levels
- Shipping costs
- Lead time
- Supplier reliability
- Customs clearance time
- Delivery deviation
- Disruption likelihood

The target variable is:

**Risk Classification**
- High Risk
- Moderate Risk
- Low Risk

This classification represents the potential risk level associated with delivery operations.

---

## Project Workflow

### 1. Data Loading
The datasets are imported using **Pandas** and inspected to understand the structure and available features.

### 2. Exploratory Data Analysis
Initial data exploration includes:

- Inspecting dataset structure
- Reviewing feature distributions
- Checking correlations between variables

Three correlation techniques are used:

- Pearson Correlation
- Spearman Correlation
- Kendall Correlation

These correlation heatmaps help identify relationships between logistics variables.

---

### 3. Feature Importance Analysis

A **Random Forest model** is used to estimate feature importance and identify the most influential variables affecting risk classification.

Top features identified include:

- Disruption likelihood score
- Shipping costs
- Lead time days
- Delay probability
- Order fulfillment status
- GPS location coordinates
- Delivery time deviation
- Supplier reliability score
- Customs clearance time

This step helps reduce unnecessary features and focus on the most meaningful predictors.

---

### 4. Feature Engineering

Categorical variables are converted into numerical representations using **one-hot encoding** where necessary.

The selected top features are used to build predictive models.

---

## Machine Learning Models

Several classification models are trained and evaluated to compare performance.

### Logistic Regression

Logistic Regression is used as a baseline model after standardizing the features.

**Results**

Accuracy: ~0.999

The extremely high accuracy indicates that one of the variables (`disruption_likelihood_score`) directly reveals the target risk classification, which suggests possible **data leakage**.

---

### Logistic Regression Without Leakage Feature

After removing the leakage feature, the model performance drops significantly.

**Results**

Accuracy: ~0.74

This indicates the dataset contains class imbalance and that the removed feature had a dominant influence.

---

### Decision Tree Classifier

A Decision Tree model is trained with balanced class weights to address class imbalance.

**Results**

Accuracy: ~0.58

The model shows moderate performance but struggles with minority classes.

---

### Random Forest Classifier

Random Forest is used as an ensemble model to improve prediction stability.

Configuration:
- 200 trees
- Balanced class weights
- Parallel processing

**Results**

Accuracy: ~0.74

The model still struggles to predict minority classes effectively due to class imbalance in the dataset.

---

## Model Evaluation

Models are evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

Visualizations are created for:

- Feature importance
- Correlation heatmaps
- Classification metrics comparison
- Confusion matrix visualization

These help interpret model performance and understand prediction behavior.

---

## Technologies Used

Python was used for the entire analysis and modeling process.

Main libraries include:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

---

## Key Insights

- The disruption likelihood score is the most influential predictor of delivery risk.
- Class imbalance affects model performance significantly.
- Removing leakage features provides a more realistic view of model performance.
- Ensemble methods such as Random Forest improve stability but still require better handling of imbalanced data.

---

## Potential Improvements

Future improvements could include:

- Applying advanced imbalance handling techniques such as SMOTE
- Hyperparameter tuning
- Testing additional models such as Gradient Boosting or XGBoost
- Feature engineering using domain knowledge
- Building a real-time risk prediction system for logistics operations

---

## Author

Shoyeb Ahmmed

This project demonstrates practical application of machine learning techniques for logistics analytics and risk classification.

---

## License

This project is intended for educational and learning purposes.
