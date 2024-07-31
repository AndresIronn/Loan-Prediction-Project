<h1 style="background: linear-gradient(to right, red, orange, yellow); -webkit-background-clip: text; color: transparent; font-weight: bold; font-size: 48px;">Loan Prediction</h1>

![Images](Images/caratulaa.png)

## Buisines Statement

Automating the loan approval processes represents a critical advancement for this bank, and banks in general, looking to optimize operations. By implementing automation, we can achive significant efficiencies, reduce operational costs, and accelerate customer service delivery, leading to enhanced overall satisfaction. A key component of this initiative involves deploying machine learning predictive models capable of accurately assessing loan applications. These models are essential for distinguishing between low-risk and high-risk applicants, thereby minimizing the occurrence of defaults and enhancing financial stability.


## Data Collection

The data used for this project was taken from Kaggle

## Goals

1) Analyze and clean the Loan Approval dataset
2) Use Machine Learning models to both predict the loan status variable and the maximum loan amount that can be lend
3) Use Tableau for data visualization

## EDA

The dataset was quite clean, it had no nulls or duplicates. However, there were some negative values in the residential assets value column, which is incorrect (and can also lead to some issues while doing square root transformations to that variable) so I imputed those values.

I did some plots/graphs to get some insights and understanding of the dataset. 

## Preprocessing

I did the preprocessing to both the numerical and categorical variables to get them ready to be used in the machine learning models. I dropped some features due to it's high VIF, did some log and sqrt transformations, scaled numerical data, encoded categorical, etc

## Machine Leraning Models

### Linear Regresion/PCA/Polinomical/RFE

To predict the maximun loan amount, I trained a Linear Regression model using RFE, PCA and also a Polinomial Regression, in a subset of the data were the status was approved. The Linear Regression with the RFE ended up being the best model, having:

- Independent variables: Income and Cibil Score
- R2=0.87
- All p-values were 0
- Prob(F-Statistic)=0

It is a great model that was later on used to make predictions on a rejected subset of the dataframe. The idea was to be able to predict the loan amount that could be lent to the clients in those cases of rejection and make some comparissons. Some cases did not make sense, because the loan amount was higher than what the client actually applied for and they were still rejected. What happened was that those were cases of clients with 'low' income, so they involved some risk to the bank

### Logistic Regression/KNN/Random Forest

To be able to predict the loan status variable, I used 3 different classification models. All of them have accuracys over 90%. I chose the Logistic model as my final model because of its accuracy and feature importance. The model worked well and was coherent. Its accuracy was 91%, and its first 3 top features were Cibil Score, Income and Loan Amount, which are probably the 3 most important for the worker at the bank attending the clients


## Visualization with Tableau

I did some comparissons between 2 of the most important variables: loan amount and income, approval percentages and portfolio assets analysis.

The link to the Tableau Story is this one: https://public.tableau.com/app/profile/andres.genta/viz/LoanApprovalVisualization_17202559517520/Story

