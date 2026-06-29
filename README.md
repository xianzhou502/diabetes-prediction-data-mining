# Diabetes Risk Prediction Using Data Mining

## Overview

This project applies data mining and statistical modelling techniques to predict diabetes risk using the Pima Indians Diabetes dataset. The goal is to explore whether clinical and health-related variables can be used to identify individuals at risk of diabetes and support early screening decisions.

The analysis compares logistic regression and decision tree models, with a focus on model performance, interpretability, and the trade-off between false positives and false negatives in a healthcare screening context.

## Research Question

How accurately can diabetes risk be predicted using genetic and health-related predictors such as glucose, BMI, pregnancies, blood pressure, age, and diabetes pedigree function?

## Dataset

The project uses the Pima Indians Diabetes dataset, which contains records of female Pima Indian patients aged over 21. The dataset includes eight numeric predictor variables and one binary outcome variable indicating whether diabetes was diagnosed.

### Predictor Variables

* Pregnancies
* Glucose
* Blood Pressure
* Skin Thickness
* Insulin
* BMI
* Diabetes Pedigree Function
* Age

### Target Variable

* `Outcome`

  * `1` = Diabetes
  * `0` = No diabetes

## Project Workflow

### 1. Data Cleaning and Preprocessing

Several variables contained physiologically impossible zero values. These values were treated as missing data rather than valid medical measurements.

The project handled these issues by:

* Identifying nonsensical zero values
* Recoding invalid zero values as missing values
* Applying median imputation
* Removing one impossible skin thickness outlier
* Creating a cleaned and imputed dataset for modelling

### 2. Exploratory Data Analysis

Exploratory analysis was used to understand the distribution of health variables and their relationship with diabetes outcomes.

The analysis included:

* Summary statistics
* Histograms
* Boxplots
* Violin plots
* Outcome-based variable comparisons
* Correlation matrix analysis

Key patterns showed that glucose and BMI had clearer separation between diabetic and non-diabetic groups compared with other variables.

### 3. Feature Assessment

Correlation and multicollinearity checks were conducted before modelling.

The project found that most predictors had low to moderate correlations. Variance Inflation Factor values were also low, suggesting that multicollinearity was not a major issue.

Skin thickness and insulin were excluded from the final binomial logistic regression and decision tree models because they required heavy imputation and contributed limited predictive value.

### 4. Predictive Modelling

The project compared multiple modelling approaches:

* Simple logistic regression
* Binomial logistic regression
* Forward selection
* Backward elimination
* Stepwise logistic regression
* Original decision tree
* Pruned decision tree

The final logistic regression model included:

* Glucose
* BMI
* Pregnancies
* Diabetes Pedigree Function
* Age
* Blood Pressure

## Model Results

| Model                        |   AUC | Accuracy | Sensitivity | Specificity | False Negatives |
| ---------------------------- | ----: | -------: | ----------: | ----------: | --------------: |
| Simple Logistic Regression   | 0.749 |    66.7% |       75.5% |       62.0% |              13 |
| Binomial Logistic Regression | 0.810 |    73.2% |       83.0% |       68.0% |               9 |
| Original Decision Tree       | 0.755 |    72.6% |       62.3% |       78.0% |              20 |
| Pruned Decision Tree         | 0.757 |    73.2% |       67.9% |       76.0% |              17 |

The binomial logistic regression model performed best overall, achieving the highest AUC, highest sensitivity, and the fewest false negatives.

## Key Findings

* Glucose was the strongest individual predictor of diabetes risk.
* BMI, pregnancies, and diabetes pedigree function also contributed meaningful predictive value.
* A broader health-risk profile performed better than glucose alone.
* Logistic regression performed better for screening prediction.
* Decision trees were easier to interpret and useful for explaining risk patterns.
* A lower classification threshold was more appropriate for healthcare screening because missing true diabetes cases is more harmful than sending additional patients for follow-up testing.

## Threshold Trade-off

The project compared classification thresholds of 0.30 and 0.50.

For healthcare screening, the 0.30 threshold was preferred because it reduced false negatives. Although this increased false positives, additional testing is safer than failing to identify patients who may have diabetes.

## Non-invasive Screening Analysis

The project also explored whether non-invasive measurements could be used to identify high-risk individuals before more invasive or expensive testing.

Non-invasive predictors included:

* BMI
* Age
* Diabetes Pedigree Function
* Pregnancies

These variables showed potential for identifying individuals who may require further diabetes testing, although they were not strong enough to replace clinical diagnostic testing.

## Tools and Technologies

* R
* R Markdown
* ggplot2
* tidyverse
* caret
* pROC
* rpart
* rpart.plot
* Logistic regression
* Decision trees
* ROC/AUC evaluation

## Project Files

| File                                 | Description                                                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------------- |
| `STAT462project_final.Rmd`           | Main R Markdown file containing data cleaning, exploratory analysis, modelling, and evaluation code |
| `Prediction of Diabetes Report.docx` | Written project report explaining methodology, findings, limitations, and next steps                |
| `Prediction of Diabetes Poster.pdf`  | Final project poster summarising the analysis and results                                           |
| `Prediction of Diabetes code.pdf`    | Exported version of the project code and outputs                                                    |

## Skills Demonstrated

* Data cleaning and preprocessing
* Exploratory data analysis
* Missing value treatment
* Statistical modelling
* Logistic regression
* Decision tree modelling
* Model comparison
* ROC/AUC evaluation
* Sensitivity and specificity analysis
* Healthcare data interpretation
* R programming
* Research communication
* Data storytelling

## Limitations

This project has several limitations:

* The dataset only includes female Pima Indian patients over 21 years old.
* The model may not generalise well to males, younger individuals, or other ethnic groups.
* Insulin and skin thickness required large amounts of imputation.
* The dataset reflects historical medical data rather than current population health conditions.
* External validation on a broader and more diverse dataset would be needed before practical use.

## Conclusion

This project shows how data mining and statistical modelling can support early diabetes risk screening. The binomial logistic regression model provided the strongest overall screening performance, while decision trees offered a more interpretable view of diabetes risk patterns.

The models should not be used as diagnostic tools, but they demonstrate how predictive analytics can help identify individuals who may benefit from further medical testing.

