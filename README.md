# Digital Insomnia: How Screen Habits Shape Your Sleep

## Project Overview

This project explores the relationship between screen habits, lifestyle choices, and sleep patterns using machine learning.

The main objective is to build machine learning models that predict sleep debt categories based on different features, including screen time before bed, caffeine consumption, bedtime, and sleep-related measurements.

I also compare different machine learning algorithms to evaluate their performance and investigate which features contribute most to their predictions.

## Dataset

The dataset used in this project is the **Digital Insomnia: Screen Habits and Sleep** dataset, obtained from Kaggle.

It contains 8,500 simulated records with 34 features describing individuals' screen habits, lifestyle choices, and sleep patterns.

Some of the important features include:

- `screen_time_before_bed_min`: Screen time before going to sleep.
- `screen_brightness_pct`: Screen brightness percentage.
- `caffeine_intake_mg`: Daily caffeine consumption.
- `bedtime_hour`: Bedtime.
- `total_sleep_hours`: Total sleep duration.
- `physical_activity_min`: Daily physical activity.
- `chronotype`: An individual's sleep-wake preference.

**Target Variable:** `sleep_debt_category`

The target variable classifies individuals into sleep debt categories: Mild, Moderate, No Debt, and Severe.

## Research Question

Can machine learning predict an individual's sleep debt category based on their screen habits, lifestyle choices, and sleep-related features?

## Project Objectives

The main objectives of this project are:

- Explore and understand the dataset.
- Analyze the relationship between screen habits, lifestyle choices, and sleep patterns.
- Clean and preprocess the data for machine learning.
- Build and compare different machine learning models.
- Evaluate model performance using appropriate classification metrics.
- Identify the most important features contributing to the models' predictions.

## Data Preprocessing

Before training the machine learning models, several preprocessing steps were performed:

- Removed unnecessary columns, including `user_id`.
- Removed `next_day_fatigue_score` to focus the prediction task on `sleep_debt_category`.
- Converted categorical features into numerical representations using encoding techniques.
- Separated the input features (X) from the target variable (y).
- Split the dataset into training and testing sets using a 70/30 split.
- Applied feature scaling using StandardScaler.
- Used stratified sampling to preserve class proportions in the training and testing sets.

Additionally, SMOTE was explored in a separate experiment to investigate whether oversampling could improve performance on underrepresented classes.

## Machine Learning Models

Two machine learning algorithms were implemented and compared in this project:

### 1. Support Vector Machine (SVM)

A Support Vector Machine with an RBF (Radial Basis Function) kernel was used for classification.

GridSearchCV was used in the initial experiment to find suitable hyperparameters. The final three-class SVM model used balanced class weights to account for class imbalance.

### 2. Random Forest Classifier

A Random Forest Classifier was trained using 200 decision trees.

The model used balanced class weights to help address class imbalance.

### Additional Experiment: SMOTE

SMOTE (Synthetic Minority Over-sampling Technique) was tested separately to investigate whether generating synthetic samples for minority classes could improve classification performance.

## Results and Evaluation

### Experiment 1: Four-Class Classification

The initial experiment included all four sleep debt categories: Mild, Moderate, No Debt, and Severe.

However, the Severe category contained only 25 observations (approximately 0.29% of the dataset), creating a significant class imbalance.

Additional experiments using SMOTE were conducted, but they did not sufficiently improve the model's ability to identify Severe cases.

### Experiment 2: Three-Class Classification

To investigate model performance without the extremely underrepresented Severe category, a second experiment was conducted using three classes:

- Mild
- Moderate
- No Debt

The dataset was divided into training and testing sets using a stratified 70/30 split.

The two models were evaluated using accuracy and macro F1-score.

| Model | Accuracy | Macro F1-score |
|---|---:|---:|
| Support Vector Machine (SVM) | 79.0% | 79.0% |
| Random Forest | 98.4% | 98.4% |

### Evaluation

Random Forest achieved the best performance on the three-class test set, outperforming SVM in both accuracy and macro F1-score.

These results indicate that Random Forest learned the patterns in this dataset more effectively. However, its high performance should be interpreted carefully because further investigation into the target-generation process is needed.
## Key Findings

The analysis produced several important findings:

- **Total sleep hours was the most influential feature.** It had the highest feature importance in the Random Forest model, accounting for approximately 42.35% of the model's total impurity-based feature importance.
- **Other sleep-related measurements also contributed to predictions.** Age, bedtime, sleep onset latency, caffeine intake, and sleep efficiency were among the other influential features.
- **Removing total sleep hours significantly reduced model performance.** The Random Forest model's accuracy dropped from approximately 98.4% to 53%, suggesting that the model relied heavily on this feature.
- **Behavioral features alone were not sufficient for strong predictions.** When sleep-related measurements were removed, the model achieved approximately 53% accuracy and a macro F1-score of 0.37.

Overall, the results suggest that physiological sleep measurements played a much larger role in predicting sleep debt categories than screen habits and lifestyle features alone.

However, further investigation into how the dataset's target variable was generated is needed to determine whether some sleep-related features are directly involved in defining the sleep debt categories.

## Technologies & Libraries

The following tools and libraries were used in this project:

- **Python:** Main programming language.
- **Pandas:** Data manipulation and analysis.
- **NumPy:** Numerical operations.
- **Matplotlib:** Data visualization.
- **Seaborn:** Statistical data visualization.
- **Scikit-learn:** Machine learning models, preprocessing, and model evaluation.
- **Imbalanced-learn:** SMOTE for handling class imbalance.
- **Jupyter Notebook:** Development and experimentation environment.
## Limitations

Although the models achieved promising results, this project has several limitations:

- **Simulated dataset:** The dataset contains 8,500 simulated records rather than data collected from real individuals. Therefore, the results may not represent real-world sleep behavior.
- **Class imbalance:** The Severe category contained only 25 observations, making it difficult for the models to learn and identify this class reliably.
- **Dependence on sleep-related features:** The Random Forest model relied heavily on `total_sleep_hours`. Removing this feature caused a significant drop in performance.
- **Potential target leakage or circular prediction:** The exact process used to generate `sleep_debt_category` is not fully known. Further investigation is needed to determine whether some input features are directly involved in defining the target variable.
- **Limited generalization:** The models were evaluated on a test set from the same simulated dataset. Their performance on real-world data remains unknown.

These limitations should be considered when interpreting the results. The project demonstrates a machine learning workflow and explores patterns in the dataset, but it does not establish that the models can reliably predict sleep debt in real individuals.

## Future Improvements

There are several ways this project could be improved in the future:

- **Use real-world data:** Test the models on real sleep and screen-time data to evaluate their ability to generalize.
- **Investigate target generation:** Examine how `sleep_debt_category` was created to better understand the relationship between the target and the input features.
- **Improve preprocessing:** Use Scikit-learn pipelines and `ColumnTransformer` to organize preprocessing and reduce the risk of data leakage.
- **Experiment with additional models:** Explore algorithms such as Logistic Regression, XGBoost, and Gradient Boosting.
- **Improve minority-class prediction:** Investigate alternative techniques for handling class imbalance and improving performance on underrepresented categories.
- **Perform further feature analysis:** Explore how screen habits and lifestyle choices relate to sleep patterns using additional statistical analysis and feature-selection techniques.

These improvements could help make the project more reliable, informative, and suitable for further experimentation.

## About Me

I am **Yahya Chourouki**, a Software Engineering student at the **University of South China**.

My academic interests include **Machine Learning Engineering, Data Science, and Artificial Intelligence**. I focus on developing my technical knowledge through continuous learning, practical projects, and hands-on experimentation.

My current goal is to strengthen my expertise in machine learning and develop the skills required to build effective, data-driven solutions.