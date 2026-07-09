# Hospital Readmission Analysis

Exploratory Data Analysis (EDA) and predictive modeling of hospital readmissions using Python.

---

## Project Overview

Hospital readmissions are an important quality metric in healthcare, impacting patient outcomes, hospital resources, and healthcare costs. The objective of this project is to explore patient characteristics associated with hospital readmissions and develop machine learning models capable of predicting readmission risk.

This project is being completed as part of the **DSCI-521: Foundations of Data Science** course in the **Master of Science in Data Science** program at **Drexel University**.

---

## Objectives

* Perform exploratory data analysis (EDA) on a healthcare dataset.
* Identify factors associated with patient readmission.
* Visualize relationships between patient characteristics and readmission outcomes.
* Engineer features for predictive modeling.
* Build and evaluate machine learning classification models.
* Communicate findings through data visualizations and written analysis.

---

## Dataset

https://www.kaggle.com/datasets/mohamedasak/hospital-patient-readmission-dataset

The dataset contains patient demographic, clinical, and hospitalization information, including:

* Age
* Gender
* Primary diagnosis
* Length of stay
* Number of comorbidities
* Previous readmissions
* Medications
* Follow-up visits
* Insurance type
* Discharge disposition
* Readmission risk score
* Readmission outcome

---

## Repository Structure

```
hospital-readmission-analysis
│
├── data/
│   ├── raw
│   └── processed
│
├── notebooks/
│
├── images/
│
├── reports/
│
├── src/
│
├── README.md
└── .gitignore
```

---

## Getting Started

1. Clone this repository.

2. Install the required Python libraries:

```bash
pip install pandas numpy matplotlib pathlib seaborn 
From Bokeh package: output_notebook, show 
```

3. Launch Jupyter Notebook.

4. Open the `notebooks` directory.

5. Run `01_exploratory_data_analysis.ipynb`.

> **Note:** This repository currently contains the Project Scoping (Phase 1) deliverable. Predictive modeling and model evaluation will be added during Phase 2.

---

## Technologies

* Python
* Jupyter Notebook
* Pandas
* NumPy
* Matplotlib
* Scikit-learn

Additional libraries may be incorporated throughout the project as needed.

---

## Research Questions

This project seeks to answer the following research questions:

* Which patient characteristics are most strongly associated with 30-day hospital readmissions?
* Does the length of a patient's hospital stay influence the likelihood of readmission?
* How do previous hospital readmissions relate to future readmission outcomes?
* Are certain primary diagnoses or clinical conditions associated with higher readmission rates?
* Which patient variables appear to be the most informative for predicting hospital readmission risk?

---

## Project Status

* In Progress

Current phase: (Phase 1 – Project Scoping)

* Repository initialization
* Project organization
* Dataset selection
* Exploratory Data Analysis (EDA)
* Data quality assessment
* Preliminary feature selection analysis

Future phases: (Phase 2)

* Data preprocessing
* Feature engineering
* Predictive modeling
* Model evaluation and comparison
* Final report and presentation

---

## Authors

* Roy Phelps
* Michael Ryan
* Shelby Frisbie
* Saad Majid


Drexel University

---

## Disclaimer

This project uses a synthetic dataset created for educational purposes. It does not contain real patient information and should not be used for clinical decision-making.
