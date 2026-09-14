# obesity-risk-classification-random-forest
Comparing behavioural-only vs. behavioural + physical predictors to classify obesity risk across seven WHO-aligned categories.
## Overview
This project investigates a core question in public health screening: **can lifestyle and behavioural data alone predict obesity risk as effectively as models that include physical measurements?** This matters because behavioural data can be collected without clinical infrastructure, making it far more scalable for early screening.

## Dataset
- Source: [Obesity Levels Dataset](https://doi.org/10.24432/C5H31Z), Mendoza Palechor & de la Hoz Manotas (2019)
- 2,111 records (SMOTE-augmented from 485 original survey responses), individuals aged 14–61 across Colombia, Peru, and Mexico
- Target variable: 7-category obesity classification (Insufficient Weight → Obesity Type III), derived from BMI

## Methods
- **Model A:** Random Forest using behavioural/lifestyle variables only
- **Model B:** Random Forest including height and weight
- Stratified 80/20 train-test split; evaluated via accuracy, balanced accuracy, F1 (per class), and confusion matrices
- Random Forest chosen over multinomial logistic regression due to violated linearity assumptions in EDA

## Key Findings
| Metric | Model A (Behavioural) | Model B (+ Physical)
| Accuracy | 81.8% | 93.6% |
| Balanced Accuracy | 89.2% | 96.0% |

- Behavioural data alone places most individuals within one severity band of their true category, a meaningful result for scalable screening
- Family history, vegetable consumption frequency, and age were the strongest behavioural predictors
- **Important honesty check:** Model B's high accuracy is partly circular, NObesity labels were derived directly from height/weight via BMI, so Model B partially "rediscovers" the labelling formula rather than demonstrating independent predictive power. This is addressed directly in the analysis rather than overstated.

## Tools Used
R, tidyverse, randomForest, caret, ggplot2, SMOTE

## Full Report
See the [full analysis](Obesity-Risk-Classification-Random-Forest-Analysis.html) for exploratory analysis, variable importance, confusion matrices, and design reflection.
