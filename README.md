🧠 Brain Tumor Detection using Machine Learning

A machine learning project for binary classification of brain tumor cases using a structured numerical dataset. The project covers data inspection, preprocessing, exploratory data analysis, feature selection, feature scaling, Logistic Regression model training, and performance evaluation.

The project was developed in Python using Google Colab, with the final results visualized through a Power BI dashboard.


📌 Project Overview

The objective of this project is to build a machine learning classification model that distinguishes between two classes:

* Normal
* Tumor

The dataset contains a relatively small number of samples but a very large number of numerical features. To handle this high-dimensional structure, the workflow applies feature selection and scaling before training the classification model.

The complete machine learning workflow is:

Dataset → Data Inspection → Data Cleaning → Exploratory Data Analysis → Train-Test Split → Feature Selection → Feature Scaling → Logistic Regression → Prediction → Model Evaluation


🎯 Objectives

* Inspect and understand the dataset structure.
* Clean and prepare the target variable.
* Remove duplicate records and constant columns.
* Check for missing values.
* Explore the dataset using visualizations.
* Separate features and target.
* Split the dataset into training and testing sets.
* Reduce the feature space using `SelectKBest`.
* Scale the selected features using `StandardScaler`.
* Train a Logistic Regression classifier.
* Evaluate the model using multiple performance metrics.
* Present the project results through an interactive Power BI dashboard.


📊 Dataset

The project uses `data.csv` as the input dataset.

### Dataset Characteristics

| Property          | Value |
| ----------------- | ----: |
| Total Samples     |    36 |
| Original Columns  | 7,466 |
| Feature Columns   | 7,465 |
| Target Column     |   `y` |
| Classes           |     2 |
| Normal Cases      |    18 |
| Tumor Cases       |    18 |
| Selected Features |    50 |

The initial dataset inspection shows **36 rows and 7,466 columns**, consisting of **7,465 integer columns and one object column (`y`)**.

After separating the target variable, the feature matrix contains **7,465 features**, while the target contains 36 values.


🧹 Data Preprocessing

The notebook performs basic data cleaning before model development.

1. Target Cleaning

The target column `y` is:

* stripped of unnecessary whitespace,
* converted to lowercase,
* mapped into numerical binary labels.

The mapping used is:

* `tumor → 1`
* `normal → 0`

2. Duplicate Removal

Duplicate rows are removed using `drop_duplicates()`.

3. Constant Feature Removal

Columns containing only a single unique value are removed using a uniqueness check.

4. Missing Value Check

The notebook checks the dataset for missing values before proceeding with machine learning.


🔍 Exploratory Data Analysis

Exploratory analysis was performed to understand the dataset and relationships between numerical features.

The notebook includes visualizations such as:

* Line Plot
* Bar Chart
* Pie Chart
* Scatter Plot
* Correlation Heatmap
* Histogram
* Boxplot

For example, the scatter plot examines the relationship between two selected features while using the target variable to distinguish the classes.

A correlation heatmap is also created for the first 10 numerical features.

The boxplot similarly examines the first 10 features and their value distributions.


✂️ Feature Selection

Because the dataset contains 7,465 features, feature selection is applied before model training.

The notebook uses:

`SelectKBest` + `f_classif`

with:

python
k = 50


This reduces the feature space from:

**7,465 features → 50 selected features**

The notebook output confirms the original feature count as 7,465 and the selected feature count as 50.


 📏 Feature Scaling

After feature selection, the selected features are standardized using:

`StandardScaler`

The scaler is fitted on the training data and then applied to both training and testing data.

This produces:

* Training data: 28 × 50
* Testing data: 8 × 50

The scaling step uses `fit_transform()` on the training features and `transform()` on the test features.



🧪 Train-Test Split

The dataset is divided into training and testing sets using `train_test_split()`.

Configuration:

| Parameter        | Value |
| ---------------- | ----- |
| Test Size        | 20%   |
| Random State     | 42    |
| Stratification   | `y`   |
| Training Samples | 28    |
| Testing Samples  | 8     |

The notebook explicitly uses `test_size=0.20`, `random_state=42`, and `stratify=y`.


🤖 Machine Learning Model

Logistic Regression

The selected and scaled features are used to train a Logistic Regression classification model.

Model configuration:

python
LogisticRegression
(
    max_iter=1000,
    random_state=42
)


The model is trained using the scaled training data.


📈 Model Evaluation

The trained model generates predictions for the test dataset.

The following evaluation metrics are calculated:

* Accuracy
* Precision
* Recall
* F1 Score
* Mean Squared Error (MSE)

Results

| Metric    |       Score |
| --------- | ----------: |
| Accuracy  | 1.00 (100%) |
| Precision | 1.00 (100%) |
| Recall    | 1.00 (100%) |
| F1 Score  | 1.00 (100%) |
| MSE       |        0.00 |

## These are the reported notebook results.

## 📋 Classification Report

The notebook also generates a detailed classification report for the two classes.

| Class        | Precision |   Recall | F1-Score | Support |
| ------------ | --------: | -------: | -------: | ------: |
| Normal       |      1.00 |     1.00 |     1.00 |       4 |
| Tumor        |      1.00 |     1.00 |     1.00 |       4 |
| Accuracy     |      1.00 |     1.00 |     1.00 |       8 |

The test set contains 8 samples, with 4 Normal and 4 Tumor cases.


🎯 Confusion Matrix

A confusion matrix is generated using the actual test labels and model predictions.

The matrix uses:

* Actual: Normal / Tumor
* Predicted: Normal / Tumor

and is visualized as a heatmap using Seaborn.

The test-set classification results show that all 8 test samples were classified correctly.



📊 Project Summary

| Category          | Result              |
| ----------------- | ------------------- |
| Dataset           | `data.csv`          |
| Total Samples     | 36                  |
| Original Features | 7,465               |
| Selected Features | 50                  |
| Training Samples  | 28                  |
| Testing Samples   | 8                   |
| Classes           | Normal, Tumor       |
| Model             | Logistic Regression |
| Accuracy          | 100%                |
| Precision         | 100%                |
| Recall            | 100%                |
| F1 Score          | 100%                |
| MSE               | 0.0                 |

These values correspond to the final summary produced inside the notebook.



📊 Power BI Dashboard

The machine learning results were further presented through an interactive Power BI dashboard.

Power BI is used as a visualization and reporting layer for the project rather than as part of the Python machine learning pipeline.

The dashboard presents information such as:

* Dataset overview
* Normal vs Tumor distribution
* Data and preprocessing information
* Model information
* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix
* Key insights
* Final project summary

The dashboard is organized into four main pages:

1. Overview
2. Data & Preprocessing
3. Model Performance
4. Insights & Summary



🛠️ Technologies Used

Programming & Analysis

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn

Machine Learning

* Scikit-learn

  * `train_test_split`
  * `SelectKBest`
  * `f_classif`
  * `StandardScaler`
  * `LogisticRegression`
  * `accuracy_score`
  * `precision_score`
  * `recall_score`
  * `f1_score`
  * `classification_report`
  * `confusion_matrix`
  * `mean_squared_error`

 Development Environment

* Google Colab

Visualization & Reporting

* Microsoft Power BI


📁 Project Structure

text
Brain-Tumor-Detection/
│
├── brain_tumor_updated(4).ipynb
├── data.csv
├── cleaned_data.csv
├── README.md
│
└── Power BI Dashboard/
    └── Dashboard screenshots / report files


> `cleaned_data.csv` is generated from the cleaned dataframe in the notebook and downloaded from the Colab environment.


🔄 Project Workflow

text
                 ┌──────────────────┐
                 │    data.csv      │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ Data Inspection  │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ Data Cleaning    │
                 │ • Target Mapping │
                 │ • Duplicates     │
                 │ • Constant Cols  │
                 │ • Missing Check  │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │      EDA         │
                 │   Visualizations │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ Train-Test Split │
                 │    28 / 8        │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ Feature Selection│
                 │ 7465 → 50        │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ StandardScaler   │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ Logistic         │
                 │ Regression       │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ Model Prediction │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │ Model Evaluation │
                 │ Accuracy         │
                 │ Precision        │
                 │ Recall           │
                 │ F1 Score         │
                 │ MSE              │
                 └────────┬─────────┘
                          ↓
                 ┌──────────────────┐
                 │  Power BI        │
                 │  Dashboard       │
                 └──────────────────┘


 Key Takeaways

* The dataset contains 36 samples and 7,465 feature columns after separating the target.
* The target contains two classes: Normal and Tumor.
* The classes are balanced with 18 Normal and 18 Tumor cases.
* Feature selection reduces the dimensionality from 7,465 to 50 features.
* StandardScaler is applied before Logistic Regression.
* The dataset is split into 28 training samples and 8 testing samples.
* Logistic Regression achieved 1.00 accuracy, precision, recall, and F1 score on the reported test set.
* The reported **MSE is 0.0.
* The results are presented in a dedicated Power BI dashboard for interactive analysis.



⚠️ Note

This project demonstrates a machine learning workflow on the available dataset and its reported test-set results. The dataset contains only 36 samples, so the reported 100% test performance should not be interpreted as evidence of clinical-grade diagnostic performance or generalization to unseen real-world medical populations.

This project is intended for **educational and machine learning demonstration purposes.


👩‍💻 Author

Riya Sharma

BCA Student | Data Science & AI/ML Enthusiast

GitHub: riya-sharma04

LinkedIn: riya-sharma-218834379
