# Regularization: Buying Bias to Sell Variance

## Objective

In this lab, I wanted to understand how LASSO and Ridge regression reduce overfitting by introducing bias, and how regularization affects prediction accuracy and variable selection.

## Methodology

- Created a simulated dataset with 200 predictors, only 5 of which actually affected the outcome, and 105 training observations.
- Trained Ordinary Least Squares (OLS), LASSO, and Ridge regression models to compare their training and test errors.
- Examined the LASSO regularization path to see when true predictors and noise variables entered the model.
- Used 5-fold cross-validation to choose the best penalty, fitting StandardScaler separately within each training fold.
- Compared LASSO's selected predictors against the known true predictors to evaluate its ability to identify important variables.
- Tested how LASSO and Ridge handled two predictors that were almost identical.
- Explored how scaling affects LASSO and OLS by multiplying one predictor by 1,000.
- Wrote my own AI prompt to generate a cross-validation function and tested its results against my original model.

## Key Findings

- **Model performance:** OLS had a test MSE of 12.9587, Ridge had 10.1128, and LASSO had 1.4219. LASSO reduced test error by 89% compared to OLS, while Ridge reduced it by 22%.
- **Bias and variance:** LASSO increased training error but performed much better on new data. This showed me how accepting some bias can help reduce variance and prevent overfitting.
- **Variable selection:** LASSO kept 16 of the original 200 predictors, while Ridge kept all 200. This showed how LASSO can simplify a model by removing unnecessary variables.
- **Cross-validation:** The best penalty was λ = 0.1995, with a CV MSE of 1.5502.
- **Correlated predictors:** When two predictors had a correlation of 0.9985, LASSO assigned 4.462 to one and 0 to the other. Ridge split the weight between them, assigning 1.618 and 1.609.
- **Standardization:** Without scaling, LASSO kept 40 predictors and had a test MSE of 1.5757. With scaling, it kept 41 predictors and reduced its test MSE to 1.4772.
- **OLS and scaling:** Rescaling one predictor changed OLS test MSE from 8.8210 to 8.0196, showing that scaling can affect its predictions when there are more predictors than observations.
- **AI-assisted cross-validation:** I used two rounds of prompting to create and revise a manual cross-validation function. I compared its results against the original cross-validation procedure, although the final agreement still needs to be confirmed.

## Conclusion

This lab helped me understand why adding more predictors doesn't always make a model better. OLS fit the training data perfectly but performed poorly on new observations. LASSO performed much better because it reduced the influence of unnecessary predictors, while Ridge improved predictions by shrinking coefficients without removing them.

I also learned that regularization depends on how predictors are scaled and that LASSO doesn't always identify the correct variables, especially when predictors are highly correlated. Overall, I would use cross-validation to choose the penalty and compare performance on new data rather than relying on training error alone.
