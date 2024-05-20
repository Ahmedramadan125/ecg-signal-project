# ecg-signal-classification-project

ECG signal binary classification to normal and abnormal using deep learning

## Table of contents 
- [Introduction](https://github.com/Ahmedramadan125/ecg-signal-project/edit/main/README.md#introduction)
- [Preprocessing](https://github.com/Ahmedramadan125/ecg-signal-project/edit/main/README.md#preprocessing)
- [CNN Model](https://github.com/Ahmedramadan125/ecg-signal-project/edit/main/README.md#cnn-model)
- [Results](https://github.com/Ahmedramadan125/ecg-signal-project/edit/main/README.md#results)

 ## Introduction
 in this project we'll use deep learning to apply classification to the data we got, the Georgia 12-Lead ECG database . This training set contains 10,344 12-lead ECGs (male: 5,551, female: 4,793) of 10-second length with a sampling frequency of 500 Hz.

 this dataset has 122 different disease or heartbeat disorders
 
 you can download the dataset from [here](https://www.kaggle.com/datasets/bjoernjostein/georgia-12lead-ecg-challenge-database)
 ## Preprocessing

- since we have too many diseases , so we should concentrate on some of this diseases so first of all we looked through the .mat files which have the actual data and we found that almost all the data have a length of 5000 and only few records have length of 2500 so we've neglected the 2500 records 
 
- then we explored the.hea files and found that every disease has a special code or number so we've sorted the diseases and saw which are the most repeated disease so we choose the normal(sinus rhythm) and other five abnormal conditions

- then we've labled all the normal with [0] and any other index or disease with [1] and then sheffled the list

- finally , we apllied normalization to the data [fit transform] so we can deal with it

- then the data was ready to be splitted into training and testing data and aplly the model 

## CNN Model

The convolutional Neural Network (CNN) model is designed for binary classification task between normal and abnormal 
#### which consists of some layers which are :
- *Input Layer* : The model starts with a 1D convolutional layer (Conv1D) consisting of 128 filters, each with a kernel size of 55 and ReLU activation. This layer is tailored to process input signals of length 5000 with a single feature.
-  *Pooling layer* : Following the convolutional layer, a max-pooling layer (MaxPooling1D) is applied with a pool size of 10.
-  *Dropout* : is then introduced with a rate of 0.5 to mitigate overfitting
-  *Global Average Pooling*: is employed to condense the feature maps into a single vector, facilitating the transition to the fully connected layers.
-  *Dense layer* : with ReLU activation, gradually reducing the dimensionality while extracting high-level features, Each dense layer is followed by dropout regularization to further prevent overfitting the final layer  with a sigmoid activation function is utilized to produce the binary classification output.

  
#### this figure shows the model
   ![popopop](https://github.com/Ahmedramadan125/ecg-signal-project/assets/170275437/de2501ab-5dc6-47d5-a8c8-6f1b94b1120c)


## results 

after we applied the model and saw the accuracy and validation accuracy we had to express the roc curve and the confusion matrix

#### this is the confusion matrix with (TP=349) , (TN=153) , (FP=7) , (FN=94)
![image 2](https://github.com/Ahmedramadan125/ecg-signal-project/assets/170275437/632a0b22-5345-4ee2-84e9-62414089f4c8)

#### and here comes the ROC curve
![image 3](https://github.com/Ahmedramadan125/ecg-signal-project/assets/170275437/4f5d9272-fe71-4f91-ab28-a2481e4cb4dc)


#### So from the results we can see that the model is nearly good and acceptable but has alot of improvements to be done maybe we can add some layers or apply more epochs 
 



