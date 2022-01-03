# Credit Risk Analysis with Machine Learning

## Overview of the Analysis
The purpose of this analysis is to compare different machine learning approaches to the problem of identifying high risk loan applications. It is an inherently imbalanced classification problem, and several techniques to mitigiate that issue are tried here. 

The first three analyses used over or undersampling to create balance between the two classes. The fourth (SMOTEENN) combines the two, first using oversampling to create balance, and then undersampling to prune away the observations that are most likely to contribute to classification errors. Then logisitic regression classifiers were built using each set of resampled data.

Ensemble learning techniques were then explored. Balance is created in both ensemble learner techniques using undersampling. The first technique is random forest, the second is adaptive boosting.

Results for each classifier include accuracy, and precision and recall, focused on the minority class.


## Results
- Naive Random Oversampling - Accuracy: 65.5%, Precision: 0.01, Recall: 0.72

![accuracy](Results/NaiveOver_accuracy.png)
![report](Results/NaiveOver_report.png)

- SMOTE - Accuracy: 66.2%, Precision: 0.01, Recall: 0.63

![accuracy](Results/SMOTE_accuracy.png)
![report](Results/SMOTE_report.png)

- Cluster Centroid (Undersampling) - Accuracy: 58.2%, Precision: 0.01, Recall: 0.61

![accuracy](Results/Under_accuracy.png)
![report](Results/Under_report.png)

- SMOTEENN - Accuracy: 66.7%, Precision: 0.01, Recall: 0.72

![accuracy](Results/SMOTEENN_accuracy.png)
![report](Results/SMOTEENN_report.png)

- Random Forest (Balanced) - Accuracy: 78.9%, Precision: 0.03, Recall: 0.70

![accuracy](Results/RandomForest_accuracy.png)
![report](Results/RandomForest_report.png)

- Easy Ensemble (AdaBoost) - Accuracy:93.2%, Precision: 0.09, Recall: 0.92

![accuracy](Results/EasyEnsemble_accuracy.png)
![report](Results/EasyEnsemble_report.png)


## Summary
There are marked differences in the performance of different techniques applied to this dataset. 
The four single logistic regression classifier all had precision of 0.01, and recall of 0.6-0.72 for the high-risk class. Accuracy was lowest for the undersampling alone technique (58.2%) and ranged from 65.5 to 66.7 for the three which included oversampling. The combination technique, SMOTEENN did not differ from the random oversampling alone.
Both ensemble learners performed much better than the single classifiers. The random forest classifier had a precision of 0.03, 3x greater than that of any of the single learners, resulting in an accuract of 78.9% even though recall was the same as the better performing single learners. Low risk loans were much less likely to be classified as high risk by the random forest classifier compared the the 4 previous methods. 
The final method, a balanced adaptive boosting classifier performed the best on all three metrics. Accuracy in the test set is 93%. Recall for the high-risk class is 0.92. Both of these metrics are very high. Precision is much improved at 0.09, though this still means that 90% of the loans classified as high-risk by the classifier will be false positives. 

My recommendation is to use the Easy Ensemble Classifier method. While further improvements in precision would be ideal, the nature of this classification problem means that the classifier can still be useful. Bad loans are very rare in this dataset but are of very high importance to the company. Identifying bad loans as such provides information the company can act on to save money. As long as the number of loans falsely identified as bad is not so high as to make it impractical for the company to make a decision based on the result of the classifier, it does not hurt the company substantially to have low precision for the rare class. 
