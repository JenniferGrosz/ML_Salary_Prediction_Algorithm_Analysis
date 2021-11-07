# Salary Prediction System: A Comparative Analysis to Determine the Best ML Model for Predicting Job Salary
##### Seattle University - Machine Learning 5066 - Data Translation Challenge March 2021
##### Author: Jennifer Grosz


**Abstract:** _A prediction is statement about what will happen or might happen in the future. Future events
are unknown and, in many cases, confirmed, exact data about the future is impossible to obtain. This
makes predictions useful tools for the determination of and preparation for probable future outcomes. In
this paper, observations containing historical person-level data and salary information will be used as
the basis for a comparative analysis between six machine learning models’ salary prediction capabilities.
Machine Learning models discussed in this paper include Multiple Linear Regression, Polynomial
Regression, K-Nearest Regressor, Random Forest Regressor, Ridge Regression and Lasso Regression
algorithms._

## Introduction
**Problem Statement:** 
The purpose of this analysis is to determine the best Machine Learning algorithm
for producing the most accurate prediction of a person’s prospective salary based on existing data. Use
cases for these models include predicting the salary for a business’ newly hired employee or predicting
the salary for a business professional job posting online where the anticipated salary information is not
provided; it can also be used as an algorithm to predict your own salary. This paper achieves the goal of
identifying the best salary prediction algorithm by using person-level data between 2016 and 2020
extracted from the Integrated Public Use Microdata Series - Current Population Survey (IPUMS CPA).
The prediction algorithms used for this analysis take certain key features as inputs and produce the most
accurate salary predictions based on the previous data each model was trained with.
**Motivations:** 
The inspiration behind this paper stems from personal frustrations experienced stemming
from the lack of information about expected salary figures provided to prospective applicants during the
online job search and application process. Additionally, this analysis is being utilized as an opportunity to
further explore and apply machine learning algorithms to develop a deeper personal understanding of
learned algorithms and the process for evaluating their performance results.
**Literature Review:** 
The methods implemented in this analysis were drawn from several sources where
similar works of such projection systems have been studied. U. Bansal et all published an article
describing their process of implementing Simple Linear and Multiple Linear Regression models for
housing and salary predictions. Das, Barik, Mukherjee published an article in January of 2020 discussing
their techniques for the implementation of a salary prediction system using Polynomial Regression
models. Achrekar, Pawade, Mathias, and Tekwani published an article in March of 2020 discussing a
system that was implemented to help people to analyze current job trends and assist applicants with the
identification of required job skills depending on prospective employment location and company in the
job market. Similarly, Xin & Khalid published an article in 2018 detailing their implementation of
methods using Lasso and Ridge regression techniques to predict housing prices. Each of these published
works provided insights and inspiration for the implementation and analysis of algorithms discussed in
this paper.
Additionally, the inspiration behind the idea of trying different categorical-coding methods used
for handling categorical data in this analysis was drawn Brownlee’s article about Ordinal and One-Hot
Encoding. In this article, the author claims the best method for handling categorical data “...is
unknowable.” (Brownlee) and a recommendation was provided to test each technique to discover what
works best. This suggestion was the foundation for the dummy vs ordinal coding analysis conducted
alongside identifying the best ML model for salary prediction performance. 


## Implementation
**Summary of work:** 
The ML models used for this analysis include Multiple Linear Regression,
Polynomial Regression, K-Neighbors Regressor, Random Forest Regressor, Ridge Regression, and Lasso
Regression algorithms. The metrics used to measure and evaluate performance of the models include 
Rsquared Score, Mean Squared Error, Mean Average Error, Root Mean Squared Error, and Explained 
Variance Score. Two separate versions of each model have been implemented to determine the best
method for handling categorical features (ordinal coding and dummy coding) for each model.
This analysis identifies the best machine learning algorithm for producing the most accurate salary
predictions by tuning the models with different parameter input settings to determine the optimal input
parameters as well as evaluating each individual model’s performance between two different encoding
methods used for handling categorical features.
To implement this process, the entire data set will be split (80/20) into 80% training and 20% test
data sets. The 80% training data from this initial split is used for tuning and training of the models. Once
optimal model parameters and categorical data encoding methods have been identified, a final
comparative test will be ran using the 20% test data and the best-performing version of each machine
learning algorithm. The resulting test data from the initial split will not be used during the tuning or
training process, it is separated and only used only in a final test. 

## Experiment Setup
**Feature Selection:** 
Based on the results generated from a correlation matrix, the decision was made to
exclude the feature years_experience from the data set because of its high correlation coefficient (0.97)
with age. Eliminating highly correlated features can help reduce overfitting because less redundant data
means there is less opportunity for the models to make decisions based on noise. The features used from
the data set are region_name, age, sex, education, and Position. The target variable for the models to
predict is earnings. (See Appendix A)
**Tuning:**
For each model, a performance evaluation has been conducted to determine the optimal input
parameters for each algorithm. Tuning of the models included running the Polynomial regression
algorithm with ordinal encoding of categorical features with the degree parameter equal to 2, 3, 4, 5, 6,
and 7. K-Neighbor Regressor algorithms were ran with the n_neighbors parameter equal to 1, 2, 3, 4, 5, 6,
7, 8, 9, 10, 20, 30, 50, 100, 200, and 300. Finally, Random Forest Regressor algorithms were ran with the
n_estimator parameter equal to 10, 50, 100, 150, 200, 250, and 300.
**Training:** 
Once the optimal input parameters for each model were identified the resulting optimal
algorithms were trained using a 10-fold cross validation. After reviewing the results of the cross
validation training the resulting 5 best performing versions of each model are selected for the final test.
**Testing:** 
The final test is conducted using the 20% test data that was originally separated from the
complete data set. This test identifies which machine learning algorithm provides the most accurate salary
prediction by using test data for which they have not been trained with.

## Results Presentation
**Tuning Results:** 
Respective to ordinal and dummy encoding of categorical features, the Polynomial
Regression models performed best with the parameter degrees = 7 and degrees = 2, the K-Neighbor
Regressor models performed best when n_neighbors = 8 and n_neighbors = 10, and the Random Forest
Regressor models performed best when n_estimators = 250 both methods of encoding categorical
features. These input parameter settings resulted in the best performance from each machine learning
model. (See Appendix B)
**Training Results:** The table below shows the training results for each model.
<img width="706" alt="1" src="https://user-images.githubusercontent.com/62961139/140666239-91a9b312-9d4e-4ab7-89a4-6fe94c64982c.png">
All models, except for the Random Forest Regressor, perform best when the dummy encoded categorical
features data set is used. (See Appendix C)

## Results Discussion
**Final Test Results:** 
The table below shows the results for each top-performing version of the models,
using test data which they have not been trained on. (See Appendix D)
<img width="842" alt="2" src="https://user-images.githubusercontent.com/62961139/140666278-08c22694-da8a-4db1-a37d-5d6f30416b71.png">
Plotted below is the density distribution of Actual (blue) and Random Forest predicted (pink) earnings
values from the final test.
<img width="847" alt="3" src="https://user-images.githubusercontent.com/62961139/140666314-fb8633bc-d383-4994-a123-3d44222fc9d9.png">

**Conclusion:** 
A Random Forest Regressor algorithm using the ordinal encoding of categorical features
performed the best across all models and all performance metrics. Since the earnings variable is
represented in thousands of USD, the performance results from the Random Forest Regression are to be
interpreted as follows:
• The Mean Squared Error of this model is $1,357,110
• The Mean Absolute Error of this model is $18,610
• The Root Mean Squared Error of this model is $36,840
• 51% of the variation in outcome can be explained by the variation in the independent variables

## Resources:
Brownlee, Jason. “Ordinal and One-Hot Encodings for Categorical Data”. June 12, 2020.
https://machinelearningmastery.com/one-hot-encoding-for-categorical-data/

U Bansal et al. “Empirical analysis of regression techniques by house price and salary prediction” 2021
IOP Conf. Ser.: Mater. Sci. Eng. 1022 012110. https://iopscience.iop.org/article/10.1088/1757-
899X/1022/1/012110/pdf

Das, Sayan & Barik, Rupashri & Mukherjee, Ayush. “Salary Prediction Using Regression Techniques”.
January 2020. SSRN Electronic Journal. 10.2139/ssrn.3526707.
https://www.researchgate.net/publication/339055809_Salary_Prediction_Using_Regression_Techniques

Achrekar D., Pawade M., Mathias G, Tekwani B. “Job Portal Analysis and Salary Prediction System”.
March 2020. International Research Journal of Engineering and Technology (IRJET). Volume: 07 Issue:
03. https://www.irjet.net/archives/V7/i3/IRJET-V7I31054.pdf

XIN, Seng Jia & Khalid, Kamil. “Modelling House Price Using Ridge Regression and Lasso Regression”
2018. International Journal of Engineering & Technology, 7 (4.30) 498-501.
https://www.sciencepubco.com/index.php/ijet/article/view/22378





### PDF Submittal 
![Salary_prediction_system_WriteUp_JG.pdf](https://github.com/JenniferGrosz/SalaryPrediction/blob/a8c0886a5c6f32bffa868ec0aa345f82d2f73840/Salary_prediction_system_WriteUp_JG.pdf)
