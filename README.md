# Google Advanced Data Analytics

### A hands-on portfolio of data analysis, statistical modeling, and machine learning

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://www.tableau.com/)

This repository brings together practical projects and course labs from the **Google Advanced Data Analytics Professional Certificate**. It demonstrates an end-to-end analytical workflow: framing business questions, preparing and exploring data, applying statistical methods, building predictive models, and communicating results through visualizations.

The projects use a TikTok video dataset to investigate video claims and opinions, alongside practice datasets for data cleaning, statistics, regression, and machine learning. The work is organized around the **PACE framework**—Plan, Analyze, Construct, Execute—and is intended as a portfolio for data analyst and junior data scientist opportunities.

## Portfolio highlights

| Area | Work demonstrated | Example materials |
| --- | --- | --- |
| **Data exploration** | Inspect datasets, assess data quality, summarize variables, and investigate patterns in TikTok video data. | [Course 1 TikTok project](%231_foundations_of_data_science/Activity_Course%202%20TikTok%20project%20lab.ipynb) |
| **Data preparation & visualization** | Structure and clean data, address missing values, perform exploratory analysis, and communicate insights with Python and Tableau. | [Course 2 project folder](%232_go_beyond_the_numbers_translate_data_into_insights/Project_end_of_course_2/) · Tableau workbooks are included in the same course folder. |
| **Statistical analysis** | Apply descriptive statistics, probability, sampling, confidence intervals, and hypothesis testing to support evidence-based conclusions. | [Course 3 TikTok project](%233_the_power_of_statistics/End_of_course_project/Activity_Course%204%20TikTok%20project%20lab.ipynb) |
| **Regression** | Explore linear and multiple linear regression, evaluate model assumptions, use ANOVA, and build logistic regression models. | [Course 4 project archive](%234_regression_analysis_simplify_complex_data_relationships/End_of_course_4_project.zip) |
| **Machine learning** | Practice feature engineering, Naive Bayes, K-means clustering, decision trees, random forests, and XGBoost. | [Course 5 project archive](%235_the_nuts_and_bolts_of_machine_learning/End_of_course_5_project.zip) |

## Skills demonstrated

- **Python analytics:** working with tabular data, exploratory analysis, and visualizations in Jupyter notebooks.
- **Data quality:** inspecting data, validating values, organizing datasets, and addressing missing data.
- **Statistics:** descriptive analysis, probability, sampling, confidence intervals, and hypothesis testing.
- **Predictive modeling:** regression and classification workflows, feature engineering, model evaluation, and clustering.
- **Data communication:** translating analytical questions and results into visual and stakeholder-oriented outputs, including Tableau workbooks.
- **Analytical process:** structuring work through the PACE framework, from defining the problem to communicating recommendations.

## Repository structure

```text
.
├── #1_foundations_of_data_science/
│   ├── Activity_Course 2 TikTok project lab.ipynb
│   ├── tiktok_dataset.csv
│   └── images/
├── #2_go_beyond_the_numbers_translate_data_into_insights/
│   ├── Project_end_of_course_2/
│   ├── course labs and datasets/
│   ├── Tableau workbooks (.twbx)
│   └── tiktok_dataset.csv
├── #3_the_power_of_statistics/
│   ├── End_of_course_project/
│   └── statistics labs and datasets/
├── #4_regression_analysis_simplify_complex_data_relationships/
│   ├── End_of_course_4_project.zip
│   └── regression labs (.zip)
└── #5_the_nuts_and_bolts_of_machine_learning/
    ├── End_of_course_5_project.zip
    └── machine learning labs (.zip)
```

Course 1–3 materials include notebooks and datasets in folders. Course 4–5 projects and labs are supplied as ZIP archives; extract an archive to access its notebooks and associated data. Some datasets are repeated across course folders or archives so each exercise can be opened with its accompanying files.

## Tools

| Tool | How it is used |
| --- | --- |
| **Python** | Data exploration, statistical analysis, and model development |
| **Jupyter Notebook** | Interactive, step-by-step analytical work |
| **pandas / NumPy** | Data manipulation and numerical analysis |
| **Matplotlib / Seaborn** | Exploratory and explanatory visualizations |
| **SciPy / statsmodels** | Statistical analysis and inference |
| **scikit-learn** | Regression, classification, clustering, and model evaluation |
| **Tableau** | Interactive data visualization and presentation |

## Getting started

1. Clone or download this repository.
2. Install Python and JupyterLab. A general-purpose environment for the Python notebooks can be prepared with:

   ```bash
   python -m pip install jupyterlab pandas numpy scipy matplotlib seaborn scikit-learn statsmodels
   ```

3. Start JupyterLab from the repository directory:

   ```bash
   jupyter lab
   ```

4. Open a notebook and run its cells in order. Keep the corresponding CSV dataset in the location expected by the notebook. Extract Course 4 or Course 5 ZIP archives before opening those notebooks.
5. Open the `.twbx` packaged workbooks in Tableau Desktop or Tableau Public.

Individual exercises may use additional packages. If a notebook reports a missing dependency, install that package in the active Python environment before rerunning it.

## Notes for reviewers

This is a collection of certificate coursework, project activities, datasets, and packaged Tableau workbooks—not a single production application or one consolidated business engagement. The project notebooks provide the best starting point for reviewing the analytical workflow; the labs show the supporting methods and practice. Findings should be interpreted in the context of each exercise and its data, rather than as production-ready models or causal conclusions.
