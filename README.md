# Crop Health Classification Pipeline

## Overview
This project focuses on classifying crop health using numerical features derived from satellite imagery and field data. We decompose the multi-class classification problem into two steps:
1. **Healthy vs. Not Healthy (H vs. NH)**: A binary classification to determine if a crop is healthy or not.
2. **Type of Not Healthy Condition**: A multi-class classification to predict the type of unhealthy condition.

To handle class imbalance, we applied **SMOTE** (Synthetic Minority Over-sampling Technique) only to augment class 2 in the multi-class classification stage.

## Data Analysis & Feature Engineering
### Data Sources
- Numerical features extracted from **Google Earth** imagery and other agricultural datasets.
- Statistical transformations applied to enhance predictive power.

### Feature Engineering
- **Grow Time Calculation**: Derived from sowing and harvesting dates.
- **Statistical Feature Engineering**: Applied transformations such as skewness, kurtosis, and power transformations.
- **Handling Missing Values**: Imputation using the most frequent strategy.
- **Feature Selection**: Only numerical features were used for the classifiers after analyzing categorical features and determining their incompatibility with the models.

## Classification Approach
### Step 1: Healthy vs. Not Healthy (Binary Classification)
- **Model Used**: Logistic Regression
- **Oversampling**: Applied SMOTE only to class 2 to balance the dataset.
- **Evaluation**: Used cross-validation and F1-score for performance measurement.

### Step 2: Classification of Not Healthy Types (Multi-class Classification)
- **Ensemble Model with Soft Voting**:
  - Logistic Regression
  - Random Forest
  - Gradient Boosting Classifier
- **Cross-Validation Strategy**: 7-fold Stratified Cross-Validation.

## Categorical Features Analysis
After thorough analysis, categorical features were excluded from final classification models due to:
- **High cardinality**: Leading to sparsity and complexity in encoding.
- **Low predictive power**: Correlation tests showed weak relationships with the target variable.

## Results & Performance
- **Best Threshold for Classification**: 0.36 (F1-score: 0.3367)
- **Weighted F1-score after SMOTE and feature engineering improvements**: Achieved stable and improved classification results with ensemble learning.

## Conclusion
This pipeline successfully decomposed the classification task into two stages, leveraged soft voting for robust prediction, and applied statistical feature engineering techniques to enhance performance. Future work could explore deep learning techniques for feature extraction from raw imagery data.

