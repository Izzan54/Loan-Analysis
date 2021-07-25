# Loan Analysis (K-mean,  K-Nearest Neighbor, Decision Tree)
Loan Analysis was my task during the internship. I had to give insight and built classification and clustering models. For the loan analysis task, I was given three different datasets which were loan_csv, clarity_underwriting_variables.csv, and payment_csv.

# 1) Import the data
* I import loan_csv, clarity_underwriting_variables.csv, and payment_csv.

# 2) Checking and cleaning missing values
* Checking the percentage of missing values in each column of underwriting data, loan data and payment data and dropped the columns that have more than 50% missing values and unimportant columns.
* clarity_underwriting_variables.csv had many variables (53 variables) for the underwriting process. Then, I created a new data frame from the underwriting dataset to keep only important columns. The new data frame only had clarity time and days, match code, fraud indicator and clear fraud score.

# 3) Exploring the data
## Loan data
* Exploring categorical variables of loan data set:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/loan_categorical.png)

* Made the "bin" for loan amount:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/loan_amount_bin.png)

* From the loan approval in categorical plot, I found out that almost 90% of applicants did not get loan approval. Then, I wanted to find out more about a not approved group.
* So, I plotted loan origination and loan status of not approved group:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/not_approved_categorical.png)

* From the plot, we know that more than 90% of applicantions did not originate from a not approved group and about 80% of applicants from a not approved group were withdrawn their applications.
* Then,  I wanted to know how many loans from not approved group has paid off in the past:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/not_approved_npaidoff.png)

* I knew that 99.9% of applicants' from not approved group had paid off 10 loans in the past.

## Underwriting process
* I merged two datasets, loan and underwriting dataset, into one data to look at details of applicants in underwriting process.
* From merged dataset, I knew that only 8.97% applications underwent underwriting process.

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/underwriting_categorical.png)

* From the plot, almost 90% applications had been originate and 90% applicants got loan approval in underwriting process.
* Then, I plotted the histogram of clear fraud scores, total fraud indicators and overall match code:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/clear_fraud_score.png)
![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/fraud_indicator.png)
![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/overall_match_code.png)

## Payment
* I also wanted to know about payment amount and installment index:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/paymentamount_installment.png)

* From plot above, we can see that applicants that did payment amount in the range 3000-4000 had installment lower than 10.
* Then, I looked at principal amount and fees:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/Principa_fees.png)

* Applicants that have higher principal amount (3000 - 4000) paid lower fees (~ 200).
* I plotted bar graph of payment status and payment collection

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/payment_categorical.png)

# 4) Correlation Between Variables using Heat Map
* I created heat map to know correlation of variables in the merged loan data and payment data.

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/heatmap_loan.png)

 ![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/heatmap_payment.png)

# 4) K-Mean Clustering
* For K-mean clustering, I used three features from merged loan data which were apr, loan amount and clear fraud score. Then, scaling these features using the standard scaling method.
* Uisng 'elbow' method to determine K clusters:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/elbow_method.png)

* From 'elbow' method, I set K = 4.
* Then, I visualized the clusters for loan, apr and clear fraud score:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/cluster_loan_apr.png)
![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/cluster_loan_clearfraudscore.png)

From summary within each cluster, i found out that:
- Cluster 1 have the highest number of applicants with the highest average annual interest rate, the lowest loan amount and the lowest fraud score.
- Cluster 3 had the lowest average annual per rate and the highest average loan amount.
- We may say that applicants that had high loan amounts will have a low annual interest rate.
- The applicants with a low clear fraud scores will get a lower loan amount and high interest rate.

# 5) K-Nearest Neighbor to Classify Loan Status
* I used KNN model to predict loan status of applicants
* I changed categorical variables into dummy variables and scaled the continuous variables using a standard scaler.
* Splitting the data into the train and test data, 70% train data and 30% test data
* I created confusion metric for KNN model:

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/KNN_model.png)

Accuracy of the model:
* Training data R-squared: 0.5434509381452554
* Test data R-squared: 0.44182636925332497

# 6) Decision Tree for Loan Approval
* I would like to predict loan approval of applicants using decision tree model.
* I changed categorical variables into dummy variables and splitted the data into the train and test data, 70% train data and 30% test data.
* I selected entropy as the criteria for calculating information gain.

![Image of loan](https://github.com/Izzan54/Loan-Analysis/blob/main/decision_tree.png)

Accuracy scores of decision tree model. Accuracy score meant the set of labels predicted in prediction must exactly match the corresponding set of labels in true label.
* DecisionTrees's Accuracy:  0.9020839878521311
