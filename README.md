# Employee Attrition Analysis

### A data-driven HR retention capstone for Salifort Motors

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![pandas](https://img.shields.io/badge/pandas-data%20analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-machine%20learning-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)

> **Portfolio project:** Exploratory analysis and employee-attrition classification, organized around the PACE workflow.

## Contents

- [Executive summary](#executive-summary)
- [Project at a glance](#project-at-a-glance)
- [PACE workflow](#pace-workflow)
- [Dataset](#dataset)
- [Analysis and modeling](#analysis-and-modeling)
- [Recommendations](#recommendations)
- [Repository contents](#repository-contents)
- [Getting started](#getting-started)
- [Next steps](#next-steps-for-a-stronger-evaluation)
- [Responsible use and limitations](#responsible-use-and-limitations)

## Executive summary

Salifort Motors' HR team wants to better understand which workplace and employee-experience patterns are associated with employees leaving. This project explores a dataset of **14,999 employee records** and develops a tuned Random Forest classifier to help inform supportive retention investigations.

After removing **3,008 duplicate rows**, the analysis explores satisfaction, performance evaluations, workload, tenure, workplace accidents, promotions, department, and salary. On a held-out test set of **2,399 records**, the Random Forest achieved **0.99 accuracy** (rounded) and **0.93 recall** for employees recorded as having left.

The results are an initial evaluation on one random holdout, not a guarantee of performance on future employees or individual teams. The data is observational: the relationships identified do not establish causes. Predictions should support confidential, human-led employee support—not automated or punitive employment decisions.

## Project at a glance

| | |
| --- | --- |
| **Business question** | Which employee and workplace patterns are associated with attrition, and where can HR investigate supportive retention actions? |
| **Analysis type** | Exploratory data analysis and binary classification |
| **Primary model** | Tuned Random Forest classifier |
| **Model selection** | 5-fold cross-validation, refit to prioritize recall |
| **Test split** | 80% training / 20% test, `random_state=0` |
| **Best mean cross-validation recall** | 0.910 |
| **Primary audience** | HR stakeholders, people managers, and portfolio reviewers |

### Skills demonstrated

- Translating an HR business question into a measurable classification task.
- Auditing, cleaning, and exploring structured employee data.
- Preparing numerical and categorical features for machine learning.
- Tuning and evaluating a classifier with cross-validation and class-specific metrics.
- Communicating findings, limitations, ethical considerations, and actionable recommendations to non-technical stakeholders.

## PACE workflow

The notebook follows **PACE: Plan, Analyze, Construct, Execute**—from clarifying the business question through communicating practical next steps.

<p align="center">
  <img src="images/pace/pace-overview.png" alt="PACE workflow overview: Plan, Analyze, Construct, and Execute" width="420">
</p>

| Stage | What was done |
| --- | --- |
| **Plan** | Defined the HR attrition question, project stakeholders, analysis goals, and privacy, fairness, and explainability considerations. |
| **Analyze** | Checked the dataset, standardized column names, removed duplicate records, reviewed tenure outliers, and explored distributions and relationships. |
| **Construct** | Prepared the target and categorical features, trained a Random Forest, and tuned its hyperparameters using cross-validation with recall as the refit metric. |
| **Execute** | Evaluated class-level test metrics, interpreted model limitations, and proposed supportive, measurable retention follow-up. |

<details>
<summary>View the PACE stage illustrations</summary>

| Plan | Analyze |
| --- | --- |
| <img src="images/pace/plan.png" alt="Plan stage illustration" width="240"> | <img src="images/pace/analyze.png" alt="Analyze stage illustration" width="240"> |

| Construct | Execute |
| --- | --- |
| <img src="images/pace/construct.png" alt="Construct stage illustration" width="240"> | <img src="images/pace/execute.png" alt="Execute stage illustration" width="240"> |

</details>

## Dataset

The included `HR_capstone_dataset.csv` contains **14,999 rows and 10 columns**. The target field is `left` (`1` = left; `0` = stayed). The supplied file contains 3,571 records labeled as left and 11,428 labeled as stayed.

| Column | Description |
| --- | --- |
| `satisfaction_level` | Employee-reported job satisfaction |
| `last_evaluation` | Score from the employee's last evaluation |
| `number_project` | Number of projects assigned |
| `average_montly_hours` | Monthly hours as named in the original CSV; renamed to `average_monthly_hours` in the notebook |
| `time_spend_company` | Years at the company; renamed to `years_at_company` |
| `Work_accident` | Whether the employee had a workplace accident; renamed to `work_accident` |
| `left` | Target label: `1` if the employee left, otherwise `0` |
| `promotion_last_5years` | Whether the employee was promoted in the last five years |
| `Department` | Employee department; renamed to `department` |
| `salary` | Salary category |

The dataset is also available from [HR Analytics and Job Prediction on Kaggle](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv).

## Analysis and modeling

### Data preparation

- Checked the dataset for missing values; the notebook reports none.
- Found and removed **3,008 duplicate rows** before analysis and modeling.
- Renamed inconsistent columns to make their meaning clearer and to standardize the naming style.
- Reviewed tenure outliers using the interquartile range. They were not automatically discarded because longer tenure can be valid and tree-based models can accommodate nonlinear splits.
- Encoded department and salary categories for use as model features.

### Exploratory findings

- Project count and average monthly hours tend to move together.
- Lower satisfaction is associated with leaving.
- Some employees with high evaluation scores also leave when workload is high.

These are descriptive patterns in the supplied historical data—not causal findings or an explanation for an individual employee's decision.

### Model and evaluation

The Random Forest was tuned using `GridSearchCV` with five folds. Recall was selected as the refit metric so cross-validation favored detecting more of the employees labeled as having left. The held-out test report is:

| Test-set class | Precision | Recall | F1-score | Support |
| --- | ---: | ---: | ---: | ---: |
| Stayed | 0.99 | 1.00 | 0.99 | 2,024 |
| Left | 0.98 | 0.93 | 0.95 | 375 |
| **Overall accuracy** |  |  | **0.99** | **2,399** |

*Values are rounded as displayed in the notebook's classification report.*

Recall for the `left` class is especially relevant to a retention-support use case, but it is not the only consideration: false positives can lead to unnecessary follow-up, while false negatives may miss people who could benefit from support. The notebook does **not** report held-out test ROC-AUC. An XGBoost comparison is included as an optional workflow, but no XGBoost result is claimed here.

## Recommendations

1. **Review workload:** Discuss sustained monthly hours, project allocation, and recurring overtime with teams and managers.
2. **Listen and support:** Offer confidential check-ins and manager support, especially where employees report low satisfaction.
3. **Review people practices:** Make overtime, recognition, and promotion policies clear and consistently applied. Investigate tenure-related patterns before proposing tenure-based promotion rules.
4. **Pilot and measure:** Test an intervention on a small scale; track satisfaction, workload, and attrition over time; and expand only when evidence supports doing so.
5. **Keep decisions human-led:** Use model signals only to prioritize supportive conversations—not to label employees or determine hiring, promotion, compensation, or termination.

## Repository contents

```text
.
├── README.md
├── Activity_ Course 7 Salifort Motors project lab.ipynb
├── HR_capstone_dataset.csv
└── images/
    └── pace/
        ├── pace-overview.png
        ├── plan.png
        ├── analyze.png
        ├── construct.png
        └── execute.png
```

## Getting started

### Requirements

- Python **3.10 or newer**
- JupyterLab or Jupyter Notebook
- The packages listed below

### 1. Download the project

Clone the repository and move into its folder:

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

Alternatively, download the repository as a ZIP file from GitHub and extract it.

### 2. Create and activate a virtual environment (recommended)

**Windows PowerShell**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install jupyterlab pandas numpy scipy matplotlib seaborn scikit-learn xgboost
```

The notebook imports scikit-learn, XGBoost, pandas, NumPy, SciPy, Matplotlib, and Seaborn. XGBoost is included because its optional comparison cells import the package, even if you only plan to reproduce the Random Forest analysis.

### 4. Launch and run the notebook

Start JupyterLab from the repository root:

```bash
jupyter lab
```

Open [`Activity_ Course 7 Salifort Motors project lab.ipynb`](Activity_%20Course%207%20Salifort%20Motors%20project%20lab.ipynb) and run the cells **from top to bottom**. Keep `HR_capstone_dataset.csv` beside the notebook: it loads the data with the relative path `HR_capstone_dataset.csv`.

The notebook runs a hyperparameter search and may take several minutes, depending on your computer. To reproduce the reported figures, use the same dataset and train/test split (`test_size=0.2`, `random_state=0`). Exact results can vary with package versions and execution environment.

### Optional: run the XGBoost comparison

XGBoost cells are an additional model-comparison workflow. Run those cells only after the shared preprocessing and train/test split have completed. Review the resulting test-set classification report before drawing conclusions; the results are intentionally not summarized here because they have not been verified for this project snapshot.

## Next steps for a stronger evaluation

- Evaluate the model on a later, time-based holdout to test generalization beyond a random split.
- Compare performance with a simple baseline and report held-out ROC-AUC, precision-recall, and probability calibration.
- Review false positives and false negatives and assess relevant subgroup performance and fairness.
- Check for potential target leakage and assess whether the model remains useful without evaluation or satisfaction features.
- Validate proposed interventions with employee feedback and measured retention outcomes before scaling.

## Responsible use and limitations

This is an educational analysis of historical employee data, not a production HR decision system. Historical patterns can encode organizational bias, and features such as department and salary may reflect structural differences. A random holdout does not prove future performance, fairness, or causality.

Protect employee privacy, restrict access to individual-level data, communicate uncertainty, and keep any follow-up fair and human-led. Model predictions must **never** be used as the sole basis for adverse employment decisions.

## Tools and references

- [Python](https://www.python.org/)
- [JupyterLab](https://jupyter.org/)
- [pandas documentation](https://pandas.pydata.org/docs/)
- [NumPy documentation](https://numpy.org/doc/)
- [Seaborn documentation](https://seaborn.pydata.org/)
- [scikit-learn model evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html)
- [scikit-learn GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)
- [XGBoost documentation](https://xgboost.readthedocs.io/)
- [Kaggle dataset source](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv)

---

*Google Advanced Data Analytics Capstone · Salifort Motors employee attrition analysis*
