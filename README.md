# Sitting_posture_detection
## Description
This work is a LAB project.  
The purpose of this project is to predict 12 types of sitting posture performed by users.  

![Figure1](https://user-images.githubusercontent.com/55873158/156693515-00cae530-f6ac-43c4-bf6c-aac0ad9a8c28.PNG)

## Experiment setting
8 pressure sensors are placed on the backrest and seat pad of the chair respectively, which means 16 sensors in total.  
10 participants are invited to this experiment. They performed the 10 sitting postures under instruction.  

## Analysis process 
Machine Learning models **SVC, KNN, Random Forest**, and **NN** are applied for prediction.  
For evluation, **Leave One Person Out** validation method is applied.  
First, **the raw data** is directly exploited after normalization and arrangement according to the need of each models. The result is:  

|Model|Recall|Precision|f1-score|Acc.|
|---|---|---|---|---|
|KNN|0.7542| 0.6974| 0.7043| 0.7543|
|SVM|0.8166| 0.7707| 0.7742| 0.8166|
|RF|0.7658| 0.6905| 0.7086| 0.7659|
|NN|0.5249| 0.6508| 0.5628| 0.65|

Second, **the difference between each values** of sensors are added to data. By combination, we get **128 new features** from 16 sensors.  
The result is:

|Model|Recall|Precision|f1-score|Acc.|
|---|---|---|---|---|
|KNN|0.755| 0.7004| 0.706| 0.7551|
|SVM|0.8317 |0.7872| 0.7909| 0.8319|
|RF|0.8083| 0.748| 0.7598| 0.8085|
|NN|0.6849| 0.7608| 0.7051| 0.76|

Finally, inorder to further increase the accuracy, we decide to **create feature with the difference between each values of sensors placed at the same component of chair.** (i.e. the difference is calculated between seatpad sensor and seatpad sensor value, and between backrest sensors and backrest sensors.)  
By combination, we get **56 new features**. The result is:  

|Model|Recall|Precision|f1-score|Acc.|
|---|---|---|---|---|
|KNN|0.7583| 0.6967| 0.7112| 0.7585|
|SVM|0.8342| 0.8014| 0.7996| 0.8342|
|RF|0.805| 0.7527| 0.7588| 0.8051|
|NN|0.8146| 0.85| 0.8143| 0.851|

Eventually, we have our best accuracy 0.851 performed by NN model.
