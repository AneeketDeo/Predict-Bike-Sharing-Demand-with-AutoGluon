# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### ANEEKET DEO

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I had to replace all the negative values to zero and I had to walktthrough the dataframe to check if it contains any NAN values and if it did I needed to replace it with mean values using fillna() method as kaggle did'nt accept any na or negative values. I also encountered an error while I was trying to just drop all the NA values as kaggle did'nt accept that either.

### What was the top ranked model that performed?
In my case WeightedEnsemble_L3 was my top ranked model as it gave me the score of 0.51411 when tuning with hyperparameters.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The datetime needed to be split into more features and I chose to split it into year, month, day and hour which is what improve my model the most. About the season I suppose that we see the four seasons in the distribution and it is the same for the weather which has three categories of input.

### How much better did your model preform after adding additional features and why do you think that is?
The best improvement was because of the split of the datetime field into year, month, day and hour.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
In my case, the model performed much better than before when I added additional features. The score jumped from 1.63468 to 0.51411.

### If you were given more time with this dataset, where do you think you would spend more time?
I would try more hyperparameter combinations as they affected the scores much more than anything else.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
| model        | hpo1                                                                                                               | hpo2                                                                              | hpo3         | score   |
|--------------|--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|--------------|---------|
| initial      | default vals                                                                                                       | default vals                                                                      | default vals | 1.86412 |
| add_features | default vals                                                                                                       | default vals                                                                      | default vals | 1.63468 |
| hpo          | nn = 'epochs': 10 'activation':('relu', 'softrelu', 'tanh') 'layers': ([100], [1000], [200, 100], [300, 200, 100]) | gbm_options 'num_boost_round': 100 'num_leaves': (lower=26, upper=66, default=36) | default vals | 0.51411 |



### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary
The most score improvement I observed was by working with the hyperparameters and also i learned that you can gain great insights from the EDA. Working forward my goal would be to improve the model by taking into consideration the working hours which impact the bike demand and the seasonal spikes and lows.
