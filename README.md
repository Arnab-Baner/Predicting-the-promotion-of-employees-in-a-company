# Predicting the promotion of employees in a company

### Goal for the project:

#### The goal of the project is to understand the factors impacting the promotion of employees in an organization and to build a model that will predict the chances of promotion #### for new employees.

### About the dataset:

#### The dataset has been taken from Analytics Vidhya. It includes a training set having 54808 employee data points. It includes the following variables:

#### employee_id: unique id of the employee
#### department: department of the employee
#### region: region of the employee
#### education: education level of the employee
#### gender: gender of the employee
#### recruitment_channel: channel of recruitment of the employee
#### no_of_trainings: number of trainings taken by the employee
#### age: age of the employee
#### previous_year_rating: employee rating
#### length of service: length of service of the employee
#### KPIs_met > 80%: whether 80% of the KPIs were met by the employee
#### awards_won?: whether employee won any award the previous year
#### avg_training_score: average training score
#### is_promoted: whether the employee was promoted or not

#### The dataset had a total of 13 independent variables out of which 4 were continuous and 9 were categorical. The target variable was the is_promoted variable.

### Data Pre Processing:

#### Null value treatment: 

#### 1) The education column had a total of 2409 missing values. The missing values were imputed based on age of the employee, the education of the employee and the joining age of the employee. The joining age of the employee was calculated by subtracting the service length from the age of the employee. The age and joining age  variable of the variable were categorized. The assumption was people generally do a certain degree in a certain age. The counts were taken and when the values were very close judgement was used to decide the education.

#### 2) The previous year rating had a total of 1812 missing values. The missing values were imputed based on whether the KPI targets were met and whether the employee was promoted or not. The assumption was employees having similar work performances should have the same rating. Here also the counts were taken in a pivot table and based on the mode the values were imputed.

#### Treatment of values:

#### 1) In the gender column, the value of the gender was changed from m and f to male and female.
#### 2) The variables KPIs_met > 80%, previous_year_rating and awards_won? were changed to categorical.

### Exploratory Data Analysis:

#### Findings:
#### 1) 8.51% of the employees have been promoted the previous year
#### 2) 8.31% of the male employees were promoted and 9% of the female employees were promoted
#### 3) Out of the total people promoted males contributed 68.57% and females contributed 31.43%
#### 4) 8.06% of the Bachelors,8.32% of the below secondary degree holders and  9.66% of the masters degree holders were promoted
#### 5) Out of the total number promoted Bachelors, Below Secondary and Masters contributed 66.79%, 1.43% and 31.76%       respectively.
#### 6) Out of the total number of people promoted, 5 and 4 Point rating employees together contributed 65%
#### 7) 4 point rating employees has a lesser percentage of promotion compared to 3 point rating employees. This is because of the fact that the number of people with 3 point ratings is much higher than the number of people with 4 point rating.
#### 8) There is no difference between the median tenure of employees of promoted and non promoted employees
#### 9) Out of the total promotions Sales and Marketing, Operations, Legal, R&D, Finance, Analytics, Procurement and HR are 25.98%, 21.91%, 21.12%,  19.92%, 16.45% and 10.96%, 14.7% and 2.9% respectively
#### 10) Majority of the employees who got promoted had high training scores but there were very few employees who got promoted  and took more than 4 trainings.
#### 11) We can see some balance in gender diversity in departments like Operations and Procurment while high imbalance in R&D (where 96% are male), Analytics (90% are male).
#### 12) 50% of referrals and 34% of each of sourcing and others are reaching their targets.

### Model Building: 

#### 1) Logistic Regression
#### 2) Support Vector Machine
#### 3) K Nearest Neighbors
#### 4) Random Forest
#### 5) Artificial Neural Network

### Imbalance of Dataset:

#### After applying the logistic regression model for the first time, it was noticed that the accuracy was very good, 93%. But the number of correct predictions of employee promotion were very less, 26%. So if we use this model deserving people wont be promoted. One reason for this is that the dataset contains very few instances (8.5%) where employees were promoted. So, we will use SMOTE to duplicate the number of instances were people were promoted. After using SMOTE the correct predictions increased from 26% to 82%. This was an improvement and shows the importance of figuring out the imbalance in datasets.

### Metric Used and Accuracies of the model: 

#### Here I have considered precision and recall as the metrics to determine which model was good in prediction. Out of the two more importance was given to the recall because I feel here the deserving employees should get the promotion so our model should focus more on getting the correct promotion values correct. The accuracies of the models are as follows:

#### 1) Logistic Regression: % of correct promoted predictions: 82, % of correct not promoted predictions: 76, accuracy: 77
#### 2) Support Vector Machine: % of correct promoted predictions: 87, % of correct not promoted predictions: 72, accuracy: 74
#### 3) K Nearest Neighbors: % of correct promoted predictions: 51, % of correct not promoted predictions: 88, accuracy: 85
#### 4) Random Forest: % of correct promoted predictions: 40, % of correct not promoted predictions: 97, accuracy: 93
#### 5) Artificial Neural Network: % of correct promoted predictions: 92, % of correct not promoted predictions: 70, accuracy: 73

### Choice of model:

#### K Nearest Neighbor and Random Forest cannot be chosen because their coorect promoted predictions are very low, though their accuracies are high. Out of logistic regression, support vector machine and artificial neural network I would choose the Artificial Neural Network because it is predicting the promoted employees correctly.

### Limitations of the work:

#### 1) Due to the large size and hardware limitations hyperparameter tuning was not done.
#### 2) The accuracy of the model has to be improved. 
