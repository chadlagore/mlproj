# Human Activity Recognition - Weightlifting Technique Optimization with Machine Learning
Authored by: Chad Lagore
Submitted as final project to Coursera's MOOC *Practical Machine Learning* through the John's Hopkins University School of Public Health Biostatistics Department.

View my full report [here](http://inversquare.github.io/har-ml/har-ml.html).

## Executive Summary

For the purpose of furthering Human Activity Recognition methodologies, data was gathered by Ugulino et al. on a group of six young weightlifters. The goal of the study was to predict, using wearable sensors, "how well an activity is performed by the weightlifter." Each subject performed 10 repetitions of the Unilateral Dumbbell Biceps Curl in five different fashions,

* Exactly according to the specification (Class A)
* Throwing the elbows to the front (Class B)
* Lifting the dumbbell only halfway (Class C)
* Lowering the dumbbell only halfway (Class D)
* Throwing the hips to the front (Class E)

More information on the data gathered is a available [here](http://groupware.les.inf.puc-rio.br/har).

A random forest machine learning model was applied to the data, and an accuracy rate of 99.0% percent was achieved on predicting which class of error the participant was making. Prior to modelling, the data was processed to remove highly correlative features, missing values, and features with near zero variance. Further improvements could be made by adding additional pre-processing elements, with more computing power.

## Preprocessing (Figure 1)

The model was built using a Random Forest algorithm from the `caret` package. Preprocessing of the entire data set prior to partitioning, took place as follows:

1. Removed user information including name, timestamps and window information - though window information may be valuable for k-fold analysis, the model still attained 99% out of sample accuracy *without* using it.

2. Removed features containing mostly NA values - features that contained NA values were more than 97% NA, it made sense to remove them entirely.

3. Using the `nearZeroVar` function in the `caret` package, I removed features that had sufficiently low variance - this offered some serious dimension reduction.

4. Using the `findCorrelation` function in the `caret` package, I removed features that had sufficiently high correlation with other features - more dimension reduction.

5. I did no scaling or centering of the data. Some variables appeared slightly skewed. If I had more computing power, I would ask the train function to do either `pca`, `scaling` or `centering` of the features.

## Partitioning (Figure 2)

For partitioning the dataset, I used `caret`'s `createDataPartition` to create three datasets, training, testing and validation. I did this with the goal of ensembling different models in the case that my out of sample accuracy was low. When a high accuracy was achieved with just one model, the validation set became redundant. The partitions were intentially applied following dimension reduction.

## Final Model (Figure 3)

I attempted 5 different models on the tidied dataset, they had varying levels of accuracy. Random foresting was the most accurate, see the next section for more information on out of sample error rates and cross validation.

## Cross Validation and Out of Sample Error (Figure 4 & 4a)

For cross validation, I used a `confusionMatrix` from the `caret` package. The `confusionMatrix` caters well to the the nature of the problem (classifier). The following out of sample error rates resulted.

* Generalized Boosted Regression Modelling`gbm` - 4.3%
* Random Forest `rf` - *1.0%*
* Recursive Partitioning and Regression Trees `rpart`- 50%
* Linear Discriminant Analysis `lda` - 32.8%
* Naive Bayes `nb` - 22%

## Submission (Figure 5)

The resulting features on the training set were selected from the `pml-testing` set. The same model was run, all 20 cases were accurately predicted.
