# CREDIT-RISK-
https://www.kaggle.com/datasets/adilshamim8/credit-risk-benchmark-dataset
16714 pbservaciones de 11 variables, 10 numericas y una binaria. El objetivo es predecir si en los proximos dos años se va a producir default o no.

Variables: 
rev_util: Ratio of revolving credit utilization (balance/credit limit)
age: Age of the borrower
late_30_59: Number of times 30-59 days past due (worse than current)
debt_ratio: Debt to income (or assets) ratio
monthly_inc: Monthly income of the borrower
open_credit: Number of open credit lines and loans
late_90: Number of times 90 days or more late on a payment
real_estate: Number of real estate loans or credit lines
late_60_89: Number of times 60-89 days past due (worse than current)
dependents: Number of dependents
dlq_2yrs: Target variable indicating if a serious delinquency occurred in the next 2 years (0 = No, 1 = Yes)


- Los morosos tienden a ser más jóvenes.
- Mayor frecuencia de pagos atrasados tanto de 30–59, 60-90 y +90 días en morosos 
- Los morosos usan menor proporción de su crédito disponible, o bien tienen líneas más pequeñas. Los morosos tienen un menor ratio de deuda actual (posiblemente porque ya fueron restringidos).
- Los morosos tienen menores ingresos mensuales promedio.
- Los morosos tienen más hijos, lo cual podría aumentar la presión financiera.
XGBOOST
Accuracy:  0.7886 ,Precision: 0.7988 ,Recall:    0.7713 , F1 Score:  0.7848 , PR AUC:    0.8618
Random Forest
Accuracy : 0.7854, Precision: 0.8098 ,Recall   : 0.7458 , F1       : 0.7765 ,AUC-PR   : 0.8527 
LGBM
Accuracy:  0.787 Precision: 0.7988 Recall:    0.767  F1 Score:  0.7826  PR AUC:    0.8628 

EL Mejor modelo es XGBOOST con 77,15% de casos malos descubiertos con 80% de precision





