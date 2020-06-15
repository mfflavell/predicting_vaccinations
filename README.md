# predicting_vaccinations
Predicting vaccinations to determine demand as well as specific ways to increase demand using survey data.

## Business Case

A pharmaceutical company that develops a vaccination for the H1N1 virus wants to gain a better understanding of the demand for the H1N1 vaccine compared to the seasonal flu vaccination and specific ways the company's marketing department could increase the demand for the vaccine.

Big Day has been tasked with conducting exploratory data analysis to identify the most important features for determining if a person will get the H1N1 vaccination and with developing a binary classification model to predict whether a person will get the vaccination or not.

## Dataset

The U.S. Department of Health & Human Services alomg with the National Center for Health Statistics launched a national telephone survey to gather data from a sample of the U.S. population to make predictions about H1N1 and Seasonal Flu vaccinations.

**Target:**
  * H1N1 Vaccination: Did the survey respondant receive the vaccine or not?
  * Seasonal Flue Vaccination: Did the survey respondant receive the vaccine or not?

In addition to these target features, there are additional survey questions regarding the respondent's health behavior, perception of virus risk and communication with their doctor.  These questions will help to reveal the most important factors that lead to vaccination.

The survey data can be found at this link: [National 2009 H1N1 Survey](https://www.drivendata.org/competitions/66/flu-shot-learning/page/210/)

## Target Review

This project contains two target variables: H1N1 Vaccination and Seasonal Flu Vaccination.  Below is a distribution of both variables.  There is a clear imbalance in the H1N1 Vaccination meaning there are far more people in the sample who did not receive this vaccine than people who did receive it.  Seasonal Flu vaccine has a higher percentage of usage and therefore the classes are fairly well balanced.

![](img/h1n1_imbalance_check.png) ![](img/seas_imbalance_check.png)

## EDA, Hypothesis Testing & Feature Importance

We used visualizations and Chi-Squared tests for cateogrical data to determine which features appeared to have a relationship with the target variables of H1N1 and seasonal vaccinations.

We dramatically decreased our p-value to run these Chi-Squared tests to avoid false positives, so any feature with a passing p-value is strongly correlated.

There are several features with a strong correlation with the target variable, including:
  * Doctor reccomendation for seasonal vaccine
  * Opinion seasonal vaccine effectiveness
  * Opinion seasonal flu risk
  
![](img/h1n1_feature_importance.png)
  
## Predictive Modeling H1N1

Based on Accuracy and Area Under the Curve (AUC), our best model appears to be Logistic Regression with an accuracy of .796, a harmonic F1-Score of .781 and an Area Under the Curve of .601.

![](img/logreg_confusion_matrix.png)

![](img/logreg_roc.png)

It is important to note that this model is very tolerant in terms of the number of false positives with a precision rate of .498 and a total of 826 false positives on the test set.  The model prioritizes false negatives with a recall of .756 and a total of 264 false negatives on the test set.  

**Fasle Positives** = predicted that people did vaccinate when they didn't.

**False Negatives** = predicted that people did not vaccinate when they actually did.

## Predictive Modeling Seasonal Flu Vaccine

Based on Accuracy and Area Under the Curve (AUC), our best model appears to be Logistic Regression again with an accuracy of .786, a harmonic F1-Score of .786 and an Area Under the Curve of .770.

![](img/confusion_seasonal.png)

![](img/roc_seasonal.png)

## Recommendations

If the pharmaceutical company could develop relationships with doctors and pharmacies that deliver vaccinations, then they could provide a two-pronged approach of providing marketing/ educational materials as well as increasing doctor recommendations during a patient's visit.

  * Educational materials in the waiting room to build awareness of the risks of H1N1 as well as the effectiveness of the vaccine 
  * Help doctors make recommendations for H1N1 vaccine.
  
The company can also create a targeted digital marketing campaign with a lead capture survey including the most relevant questions from the federal survey and then use that data to qualify leads using the predictive models which would trigger specific marketing actions.  For example, if someone is predicted not vaccinate, then the person could be routed to a webpage containing information about the risks of H1N1 and the effectiveness of the vaccine and also recieve marketing emails if they opted in.  

## Next Steps

  * Use other models, including a neural network, to see if this increases the accuracy, F1 score, and AUC of the predictive model.
  * Setup a pipeline that can be integrated into the company's marketing strategy and software to improve lead qualification.
  
