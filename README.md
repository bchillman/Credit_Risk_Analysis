# Credit_Risk_Analysis
## Overview
In this analysis we analyze credit card data using multiple supervised machine learning models, with the goal of finding a model that best determines whether a loan is a high-risk for fraud or low-risk. These models can be classified into two categories, resampling and ensemble. The resampling models utilize either oversampling or undersampling to better represent both low-risk and high-risk loans, which is necessary because there are many more low-risk loans than high-risk loans. The ensemble models use ensemble algorithms to categorize this same data. These 6 models (4 resampling and 2 ensemble) were then compared using both an accuracy score and a classification report.

## Results
With each of the 6 models being run, the following results were found:
### Resampling Models
#### Naive Random Oversampling
The first model was a simple naive random oversampling model, which randomly copies data points from the minority dataset (in this case the high-risk loans) until there are the same number as the majority dataset. The results are shown below:
<p align="center">
<img src="https://github.com/bchillman/Credit_Risk_Analysis/blob/main/Images/Random_Oversampling.png" width="400" height="291">
</p>
In this image, we first see that the accuracy is around 67%, meaning that 67% of the loans are correctly identified as high-risk or low-risk by the model. Additionally, we can see that while the recall of both high-risk and low-risk loans is decent, the precision for high-risk loans is very low (.01) meaning that the model is incorrectly identifying many low-risk loans as high-risk. This is not unexpected with imbalanced data, but we may want to have a higher recall for high-risk loans.

#### SMOTE Oversampling
The second model used SMOTE (Synthetic Minority Oversampling Technique), which creates new instances of the minority dataset that are interpolated from the original minority dataset. The results are shown below:
<p align="center">
<img src="https://github.com/bchillman/Credit_Risk_Analysis/blob/main/Images/SMOTE_Oversampling.png" width="400" height="291">
</p>
In this image, we see that the accuracy and the recall for both categories are all lower than the random oversampling. This could likely be due to the fact that there are data points from each class that are close to each other. When we create nearest neighbors for the low-risk dataset, then, it adds more noise to the system and the model performs worse.

#### Undersampling
The third model used cluster centroids to undersample the majority dataset. This technique creates clusters to represent the dataset and then takes the center of the cluster as a singular datapoint The results are shown below:
<p align="center">
<img src="https://github.com/bchillman/Credit_Risk_Analysis/blob/main/Images/Undersampling.png" width="400" height="291">
</p>
Once again, we see that the accuracy and the recall for both categories are all lower than the random oversampling, indicating that this undersampling model is performing worse. If our data is particularly noisy, it can be difficult to find clusters that correctly represent the majority dataset and undersampling reduces the amount of data that we have, adding more variance.

#### SMOTEEN
Finally, we used SMOTEEN to model this dataset. This technique combines oversampling and undersampling techniques, and its results can be seen below:
<p align="center">
<img src="https://github.com/bchillman/Credit_Risk_Analysis/blob/main/Images/SMOTEEN.png" width="400" height="291">
</p>
The total accuracy with this model is once again slightly lower than that of the random oversampling model, however, the recall for high-risk loans is higher than that of the random oversampling model. Depending on what we value, this may indicate that this model is preferred to the random oversampling model. If we place a lot of value on making sure that every high-risk loan is classified as high-risk, potentially at the expense of classifying some low-risk loans as high-risk, then this model would be considered better than the random oversampling model.

### Ensemble Models
#### Random Forest Model
In this model, many decision tree models are combined to create an ensemble model. The results of this ensemble model are shown below:
<p align="center">
<img src="https://github.com/bchillman/Credit_Risk_Analysis/blob/main/Images/Random_Forest.png" width="400" height="291">
</p>
Here we can see that this ensemble model performs significantly better than the resampling models. The accuracy is about 75% and almost all the classification report values are higher than those of each of the resampling methods. The only exception is the recall for high-risk loans. This is value is lower than that of the SMOTEEN model, so in the case outlined in that model's section, we may prefer that model.

#### AdaBoost Model
The final model uses the AdaBoost, which is similar to the random forest model, but each decision tree learns from the previous to make it better. The results of this model are shown below:
<p align="center">
<img src="https://github.com/bchillman/Credit_Risk_Analysis/blob/main/Images/AdaBoost.png" width="400" height="291">
</p>
This model clearly performs the best of all models across each metric, in particular, it has an accuracy of .912, meaning that 91.2% of the data is correctly categorized.

## Summary
In summary, the ensemble models clearly do a better job of categorizing this data than the resampling models. In particular, the boosted technique does much better than any other model and would be the suggestion for model to use to categorize these loans. It has the highest accuracy, as well as the highest high-risk recall, making it the clear choice.
