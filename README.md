# Churn_prediction_model_for_a_bank
## Supervised Machine Learning Project from Practicum by Yandex

### Goal

Develop a binary classification model for Beta Bank that would analyze data on clients’ past behavior and termination of contracts with the bank and predict whether a customer will leave the bank soon.

### This project's repo includes the following files:

- The project's jupyter notebook (Churn_prediction_model_for_a_bank.ipynb);
- A pdf format of the notebook (Churn_prediction_model_for_a_bank.pdf);
- Input data (Churn.csv);
- Project description from Practicum (SML project description.pdf).

### This project includes the following steps:

1. Descriptive statistics;
2. Data Preprocessing: missing values, categorical features encoding and duplicates check;
3. EDA: outliers and target variable analysis;
4. Splitting data into train, validation and test sets;
5. Features standard scaling;
6. Class Imbalance correction and models' hyperparameters tuning;
7. Model selection;
8. Retrain the best tuned model on the whole training set and test it on the test set;
9. Sanity check;
10. AUC-ROC calculation.

### Based on the analysis we have come to the following conclusions:

- There are no visible outliers in our data. We decided to keep the data as is and if necessary revisit this section after modeling;
- Most clients are located in France and they are the most loyal to the bank among all countries, on average. The highest churn rate is in Germany. This features might be quite a good predictor for our model;
- Most customers are in their 30s, the distribution is positively skewed as less elder than younger people have bank accounts. Interestingly that the distribution of "exited" customers (in orange) is closer to normal than that of loyal clients;
- Most clients are male. Female clients leave the bank more often.
- We noticed that our target classes are imbalanced: there are more than twice as many observations when a client stayed with the bank than of those who left. As one way to correct it, we used the stratify parameter while splittig data into train and test sets. It makes a split so that the proportion of values in the sample produced will be the same as the proportion of values in the target variable.

In the next step we have tried to correct imbalanced classes using 3 methods:

- class weight adjustment;
- upsampling;
- downsampling.

We have also tuned each of the 3 chosen algorithms (Decision Tree, Random Forest and Logistic Regression) and searched for the best hyperparameters in order to select the best model.

**Random Forest model using Class Weight Adjustment method** showed the highest score (62.33). Then we have retrained this model on the whole training set (including validation set) and tested it with the test set that our model didn't see before. We have reached **63.19% F1 score on the test set**.

Next, we have checked our model for sanity by comparing the final score to the baseline F1 score. The final F1 score of our model is much higher (28.82%) than the baseline F1 score that we would get if instead of classifying we simply predicted minority class target value for each new observation.

Finally, we have calculated the **AUC-ROC value and it turned out to be 86.66%**, which means that our model's predictions are correct in more than 80% of cases. We have also plotted the ROC curve. It visualized well the fact that our final model is performing quite well - its ROC curve is much higher than the diagonal.

### The logbook of this project can be found [here](https://docs.google.com/spreadsheets/d/1SrGdReexaSEomJGS6yR6cRwJtHA_XqpprnLaE7B6Ayg/edit#gid=1392390286) (SML tab).
Total time spent on the project: 11.3 hours with a daily average of 1.94 hours working for 8 days.
