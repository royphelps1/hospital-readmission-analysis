# Hospital Readmission Analysis

Exploratory data analysis and predictive modeling of hospital readmissions using Python and machine learning.

---

## Project Overview

Hospital readmissions are an important healthcare quality concern because they can affect patient outcomes, healthcare utilization, and costs. This project investigates patient demographic and clinical characteristics associated with 30-day hospital readmission and evaluates machine learning approaches for predicting readmission outcomes.

Using a synthetic healthcare dataset containing 8,000 patient records, the project combines exploratory data analysis, feature assessment, supervised classification, hyperparameter tuning, and model interpretation. Three classification approaches—Logistic Regression, Decision Tree, and Random Forest—were evaluated and compared.

A potentially problematic feature, `readmission_risk_score`, was separately investigated because its method of construction was undocumented and could introduce data leakage. The final modeling approach excludes this variable.

This project was completed as part of DSCI-521: Foundations of Data Science in the Master of Science in Data Science program at Drexel University.

---

## Key Findings

The analysis identified several important patterns associated with hospital readmission:

* **Previous hospital readmissions** emerged as one of the strongest predictors of future readmission.
* **Comorbidity burden** was strongly associated with increased readmission risk.
* Several primary diagnosis categories, including **Sepsis, COPD, Stroke, Kidney Disease, and Heart Failure**, were associated with higher predicted readmission odds in the Logistic Regression model.
* **Length of stay** provided predictive information but was comparatively less influential than previous utilization, comorbidity burden, and diagnosis.
* Removing `readmission_risk_score` produced only a minimal reduction in predictive performance, supporting its exclusion from the final model because of potential data-leakage concerns.
* Hyperparameter tuning substantially reduced overfitting in the Decision Tree and Random Forest models.
* **Logistic Regression was selected as the preferred final model** because it provided the strongest overall combination of predictive performance and interpretability.

### Final Model Performance

| Metric            | Logistic Regression |
| ----------------- | ------------------: |
| Accuracy          |           **0.814** |
| Precision         |           **0.832** |
| Recall            |           **0.951** |
| F1-Score          |           **0.888** |
| ROC-AUC           |           **0.839** |
| Average Precision |           **0.941** |

The final Logistic Regression model achieved approximately **95.1% recall** for the readmitted class while retaining greater interpretability than the tree-based alternatives.

Note: Because the dataset is synthetic, these findings demonstrate the analytical and machine learning methodology and should not be interpreted as clinically validated relationships.

---

## Objectives

The primary objectives of this project were to:

- Perform exploratory data analysis (EDA) on a healthcare dataset.
- Assess data quality and examine patient characteristics.
- Identify factors associated with hospital readmission.
- Visualize relationships between patient characteristics and readmission outcomes.
- Prepare and transform features for exploratory analysis and predictive modeling.
- Build multiple machine learning classification models.
- Tune model hyperparameters using cross-validation.
- Evaluate and compare model performance.
- Interpret important predictors of hospital readmission.
- Communicate findings through data visualizations and written analysis.

---

## Research Questions

This project investigates the following research questions:

- Which patient characteristics are most strongly associated with 30-day hospital readmissions?
- Does the length of a patient's hospital stay influence the likelihood of readmission?
- How do previous hospital readmissions relate to future readmission outcomes?
- Are certain primary diagnoses or clinical conditions associated with higher readmission rates?
- Which patient variables appear to be the most informative for predicting hospital readmission risk?

---

## Dataset

The project uses the **Hospital Patient Readmission Dataset** available from Kaggle.

**Dataset Source:**  
https://www.kaggle.com/datasets/mohamedasak/hospital-patient-readmission-dataset

The original Kaggle page became unavailable after the dataset was obtained for this project. A verified identical copy is currently available at:

https://github.com/Amal-kjn/hospital-readmission-sql-analysis/blob/main/hospital_readmission_dataset.csv

The dataset contains patient demographic, clinical, and hospitalization information, including:

- Age
- Gender
- Primary diagnosis
- Length of stay
- Number of comorbidities
- Previous readmissions
- Medications
- Follow-up visits
- Insurance type
- Discharge disposition
- Readmission risk score
- Readmission outcome

The original dataset is preserved in the `data/raw` directory.

A processed version containing engineered features is generated by the notebook and saved to the `data/processed` directory.

---

## Repository Structure

```text
hospital-readmission-analysis/
│
├── data/
│   ├── raw/
│   │   └── hospital_readmission_dataset.csv
│   │
│   └── processed/
│       └── hospital_readmission_processed.csv
│
├── notebooks/
│   └── Project_analysis_v3.ipynb
│
├── images/
│
├── README.md
└── .gitignore
```

---

## Project Workflow

The project follows a structured data science workflow:

1. Load the raw dataset.
2. Validate the dataset for missing values and duplicate records.
3. Examine dataset structure and descriptive statistics.
4. Perform exploratory data analysis.
5. Engineer additional features for analysis.
6. Save the processed dataset.
7. Prepare the feature matrix and target variable.
8. Split the data into training and testing datasets.
9. Preprocess numerical and categorical variables.
10. Train multiple classification models.
11. Tune model hyperparameters using cross-validation.
12. Evaluate and compare model performance.
13. Interpret important model features and coefficients.
14. Compare model performance using Precision-Recall analysis.

---

## Exploratory Data Analysis

Exploratory data analysis was performed to better understand the structure, distribution, and relationships within the dataset.

The EDA includes:

- Dataset validation and structural inspection
- Numerical summary statistics
- Categorical summary statistics
- Gender distribution
- Admissions by season
- Insurance type distribution
- Age-group analysis
- Primary diagnosis distribution
- Histograms of numerical variables
- Box plots for identifying distributions and potential outliers
- Correlation analysis
- Relationship between comorbidities and readmission
- Readmission class distribution

Both static and interactive visualizations were used throughout the analysis.

---

## Interactive Data Visualization

Interactive visualizations were created using **Bokeh** to provide additional ways to explore relationships in the dataset.

These include:

- Readmission counts by primary diagnosis and readmission status
- Interactive correlation heatmap of numerical variables

Interactive charts include features such as hover information, zooming, panning, and chart reset controls.

---

## Data Preparation and Feature Engineering

Data preparation was performed before predictive modeling.

The workflow includes:

- Identification of categorical and numerical variables
- Preparation and transformation of features for exploratory analysis and predictive modeling
- Preservation of the original raw dataset
- Export of the feature-enriched dataset to `data/processed`
- Removal of identifiers and variables not used for modeling
- Creation of the feature matrix (`X`)
- Creation of the target vector (`y`)
- Stratified training and testing split
- Standardization of numerical features where appropriate
- One-hot encoding of categorical features

Scikit-learn pipelines and `ColumnTransformer` were used to keep preprocessing and model training together in a reproducible workflow.

---

## Machine Learning Models

Several classification models were developed and evaluated.

### Logistic Regression

Logistic Regression was used as an interpretable baseline classification model.

Two versions were examined during the analysis, including an evaluation of model performance without the provided readmission risk score.

### Decision Tree

A Decision Tree classifier was trained and evaluated.

Training and testing performance were compared to examine potential model overfitting.

The model was subsequently tuned using cross-validation and hyperparameter optimization.

### Random Forest

A Random Forest classifier was trained to provide an ensemble-based approach capable of modeling more complex relationships.

Training and testing performance were compared, followed by hyperparameter tuning using cross-validation.

### Hyperparameter Tuning

`GridSearchCV` was used to evaluate combinations of model hyperparameters.

Cross-validation ROC-AUC was used as the scoring metric during model tuning.

### Feature Selection and Data Leakage Assessment

The provided `readmission_risk_score` variable was investigated separately because its method of construction was undocumented. If the score incorporated information unavailable at the time a readmission prediction would normally be made, including it could introduce data leakage.

Logistic Regression models were therefore compared with and without `readmission_risk_score`. Removing the variable produced only a minimal change in predictive performance while maintaining strong recall and discrimination. The variable was consequently excluded from the final feature set used for model comparison.

---

## Model Evaluation

Model performance was evaluated using multiple complementary classification metrics:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC
* Average Precision

Additional evaluation methods included confusion matrices, classification reports, ROC curves, Precision-Recall curves, training versus testing accuracy, and cross-validation performance.

### Final Model Comparison

| Model                   |  Accuracy | Precision |    Recall |  F1-Score |   ROC-AUC | Average Precision |
| ----------------------- | --------: | --------: | --------: | --------: | --------: | ----------------: |
| **Logistic Regression** | **0.814** |     0.832 | **0.951** | **0.888** | **0.839** |         **0.941** |
| Tuned Decision Tree     |     0.812 | **0.847** |     0.924 |     0.884 |     0.815 |             0.929 |
| Tuned Random Forest     |     0.799 |     0.819 |     0.949 |     0.879 |     0.828 |             0.938 |

Although the differences between the models were relatively modest, Logistic Regression achieved the highest accuracy, recall, F1-score, ROC-AUC, and Average Precision. The tuned Decision Tree achieved the highest precision.

Based on predictive performance, generalization, and interpretability, **Logistic Regression was selected as the preferred final model**.

### Precision-Recall Analysis

Precision-Recall analysis was performed to provide an additional comparison of classifier performance.

Precision-Recall curves were generated for the final models, along with Average Precision scores.

The positive-class prevalence was included as a baseline to provide additional context when interpreting model performance.

---

## Model Interpretation

Model interpretation techniques were used to better understand which variables contributed most strongly to predicted hospital readmission.

### Random Forest Feature Importance

Feature importance values were extracted from the tuned Random Forest model and ranked to identify the most influential predictors.

The ten most important features were visualized using a horizontal bar chart.

### Logistic Regression Feature Effects

Logistic Regression coefficients were examined to determine the direction and magnitude of relationships between features and predicted readmission.

The analysis includes:

- Logistic Regression coefficients
- Absolute coefficient magnitude
- Odds ratios
- Features associated with higher predicted readmission odds
- Features associated with lower predicted readmission odds
- Visualization of the strongest Logistic Regression feature effects

---

## Generated Visualizations

Static visualizations generated by the notebook are saved automatically to the `images` directory.

Examples include:

- Gender Distribution
- Admissions by Season
- Insurance Type Distribution
- Primary Diagnosis Distribution
- Histograms
- Box Plots
- Correlation Matrix
- Logistic Regression Confusion Matrix
- Logistic Regression ROC Curve
- Tuned Decision Tree Confusion Matrix
- Random Forest Confusion Matrix
- Tuned Random Forest Confusion Matrix
- Random Forest Feature Importances
- Logistic Regression Feature Effects
- Precision-Recall Curve Comparison

---

## How to Run the Project

### 1. Clone the Repository

Clone or download this repository to your local computer.

```bash
git clone <repository-url>
```

Navigate to the project directory:

```bash
cd hospital-readmission-analysis
```

### 2. Install the Required Python Libraries

Install the required dependencies:

```bash
pip install pandas numpy matplotlib seaborn bokeh scikit-learn jupyter
```

### 3. Launch Jupyter Notebook

From the project directory, launch Jupyter Notebook:

```bash
jupyter notebook
```

### 4. Open the Analysis Notebook

Navigate to:

```text
notebooks/Project_analysis_v3.ipynb
```

### 5. Run the Notebook

Run all notebook cells from top to bottom using **Run All**.

The notebook will automatically:

- Load the raw dataset from `data/raw`
- Validate the dataset
- Perform exploratory data analysis
- Generate visualizations
- Create engineered features
- Save the processed dataset to `data/processed`
- Prepare the data for machine learning
- Split the data into training and testing sets
- Preprocess categorical and numerical variables
- Train classification models
- Perform hyperparameter tuning
- Evaluate model performance
- Generate model interpretation results
- Save static visualizations to the `images` directory

The notebook uses relative project paths so that the project can be run using the repository structure without manually changing individual file paths.

---

## Technologies

This project uses:

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Bokeh
- Scikit-learn
- pathlib

---

## Reproducibility

Several practices were used to make the analysis reproducible:

- Relative project paths are used throughout the notebook.
- Raw and processed datasets are stored separately.
- Output directories are created automatically when needed.
- Random states are specified for machine learning models and data splitting.
- A stratified train/test split preserves the target-class distribution.
- Scikit-learn pipelines combine preprocessing and model training.
- Cross-validation is used during hyperparameter tuning.
- Generated static figures are automatically saved to the project `images` directory.
- The notebook is designed to run sequentially from top to bottom using **Run All**.

---

## Project Status

**Status: Complete**

### Phase 1 – Project Scoping and Exploratory Data Analysis

- Dataset selection and evaluation
- Data quality assessment
- Exploratory data analysis
- Data visualization
- Feature assessment
- Research question development

### Phase 2 – Predictive Modeling and Model Evaluation

- Data preprocessing and feature engineering
- Logistic Regression modeling
- Data-leakage assessment
- Decision Tree modeling and tuning
- Random Forest modeling and tuning
- Cross-validation and hyperparameter optimization
- Model comparison
- Precision-Recall and Average Precision analysis
- Random Forest feature importance
- Logistic Regression coefficient and odds-ratio interpretation
- Final model selection
- Research question findings
- Final conclusions and recommendations

**Preferred Final Model:** Logistic Regression

---

## Authors

- Roy Phelps
- Michael Ryan
- Shelby Frisbie
- Saad Majid

**Drexel University**

---

## Disclaimer

This project uses a synthetic dataset created for educational purposes. It does not contain real patient information and should not be used for clinical decision-making.