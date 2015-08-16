# Human Activity Recognition - Weightlifting Technique Optimization with Machine Learning
Authored by: Chad Lagore
Submitted as final project to Coursera's MOOC *Practical Machine Learning* through the John's Hopkins University School of Public Health Biostatistics Department.

View full report [here](http://inversquare.github.io/har-ml/har-ml.html)

## Executive Summary

For the purpose of furthering Human Activity Recognition methodologies, data was gathered by Ugulino et al. on a group of six young weightlifters. The goal of the study was to predict, using wearable sensors, "how well an activity is performed by the weightlifter." Each subject performed 10 repetitions of the Unilateral Dumbbell Biceps Curl in five different fashions,

* Exactly according to the specification (Class A)
* Throwing the elbows to the front (Class B)
* Lifting the dumbbell only halfway (Class C)
* Lowering the dumbbell only halfway (Class D)
* Throwing the hips to the front (Class E)

More information on the data gathered is a available [here](http://groupware.les.inf.puc-rio.br/har).

A random forest machine learning model was applied to the data, and an accuracy rate of 99.0% percent was achieved on predicting which class of error the participant was making. Prior to modelling, the data was processed to remove highly correlative features, missing values, and features with near zero variance. Further improvements could be made by adding additional pre-processing elements, with more computing power.

