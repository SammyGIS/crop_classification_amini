# Forest and Tree Crop Classification Using Sentinel-2 Imagery

## Project Overview

Deforestation is a critical global and African challenge. Between 1990 and 2010, Africa lost approximately 10% of its forest cover, leading to food insecurity, biodiversity loss, and accelerated climate change. A major issue in forest monitoring is the difficulty in distinguishing between natural forest cover and tree crops such as cocoa and palm plantations, which often appear similar in satellite imagery.

This project aims to build a machine learning model to classify land cover pixels as one of the following:

* **0**: Forest cover
* **1**: Cocoa plantation
* **2**: Palm plantation

Improving the accuracy of this classification task is essential for environmental monitoring, sustainable agriculture, regulatory compliance, and supporting global efforts to combat deforestation and forest degradation.

## Dataset Description

The dataset is derived from Sentinel-2 satellite imagery and includes:

* **13 spectral bands** per pixel
* **Three years of data**, capturing temporal dynamics related to crop and forest growth cycles
* **Unique Areas of Interest (AOIs)** for training and testing to ensure generalization

Each sample corresponds to a pixel with associated spectral data over time, labeled according to the dominant land cover type.

## Objective

The goal is to accurately classify each pixel into one of the three land cover categories using multi-year, multi-band satellite data.

## Methodology

The following steps were implemented:

1. **Data Cleaning**

   * Removal of duplicate records
   * Handling of missing values
   * Normalization and scaling of features where necessary

2. **Feature Engineering**

   * Exploration of correlations and class distributions
   * Consideration of potential vegetation indices and band combinations

3. **Model Development**

   * **Random Forest Classifier** and **LightGBM Classifier** were implemented
   * Hyperparameter tuning was applied using GridSearchCV with GroupKFold cross-validation
   * F1 Score was used as the primary evaluation metric due to class imbalance

4. **Model Evaluation**

   * Both models were evaluated on validation data
   * The **LightGBM model outperformed the Random Forest model**, achieving the highest macro F1 Score

5. **Feature Importance and Model Interpretation**

   * LightGBM feature importance was analyzed to interpret which spectral bands and temporal patterns contributed most to model performance

6. **Prediction and Submission**

   * Predictions were generated for the test set and formatted according to submission requirements

## Evaluation Metric

The primary evaluation metric is the **macro F1 Score**, which balances precision and recall across all three classes. It is defined as:

$$
F1 = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}
$$

This metric ensures fair performance across all classes, even if they are imbalanced.

## Submission Format

The final submission file is a CSV with the following structure:

| ID             | Target |
| -------------- | ------ |
| ID\_C7AV4GEJP9 | 1      |
| ID\_AFVZYGLXXY | 2      |
| ID\_567GHBKOPY | 0      |

* `ID`: Unique identifier for each test sample
* `Target`: Predicted class label (0 for forest, 1 for cocoa, 2 for palm)

## Tools and Technologies

* Python (pandas, numpy, matplotlib, seaborn)
* scikit-learn
* LightGBM
* GridSearchCV
* GroupKFold
* Imbalanced-learn (SMOTE)

## Conclusion

This project demonstrates an effective approach to classifying land cover types using multi-temporal satellite data. The LightGBM model, optimized with hyperparameter tuning and informed by feature analysis, delivered the best performance and will be useful for real-world environmental monitoring and forest management efforts.