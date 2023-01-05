# Breast-Cancer-Detection
A deep learning project of breast cancer detection using tensorflow


Given a dataset of breast cancer images, I created this project to classify them in classes of benign, malignant and normal together with their masked images respectively.
Here a keras model is trained for classification then a prediction is made on new data.

The dataset was downloaded from kaggle then loaded from my local storage.

Below is a benign image

![sample_benign_tumor](https://user-images.githubusercontent.com/78556152/210738678-258b9e33-9091-47df-8415-230c45734417.png)

## Defining Some Parameter

batch_size set to 32, 
image height set to 180 and 
image width set to 180 

## Splitting the Dataset for Training and Validation

The data is split into training and validation sets. 80% of the data is assigned to training and the remaining 20% assigned to validation

Here are some images from my training set

![sample_training_images](https://user-images.githubusercontent.com/78556152/210739786-b4122950-a5c4-4f60-a7c2-913df343a9df.png)


The dataset is configured for performance and a keras model is created.

Below is the model's summary

![Screenshot 2023-01-05 115732](https://user-images.githubusercontent.com/78556152/210740926-f963cf36-184d-401b-b5d7-10018d634221.png)

Below are part of the results from training the model for 10 epochs

![Screenshot 2023-01-05 120201](https://user-images.githubusercontent.com/78556152/210741663-b52a4b43-021d-4d6c-9952-677ee5bd4bee.png)

## Visualize training results

Plots of accuracy and loss on training and validation sets indicate evidence of overfitting. This is shown by a wide margin between training and validation accuracy and loss as shown in the image below. 

The same is also evident in the training results above, where by the training accuracy is 0.9873 and the validation accuracy is 0.8063. Clearly the margin between the two is huge and the same is true for losses. 

![training_and_validation_accuracy_and_loss_1](https://user-images.githubusercontent.com/78556152/210742587-adeaa7c1-0576-4d07-891d-638565370e9d.png)


## Solving the Problem of Overfitting

Two techniques are used to solve the overfitting problem:

1. Data Augmentation - generating more training examples from the existing data. Below is an example of an augmented image

![sample_augmented_images](https://user-images.githubusercontent.com/78556152/210743280-92a1b024-ad29-4bac-bc07-55125e243a92.png)

2. Adding a dropout layer to the model.

![Screenshot 2023-01-05 121254](https://user-images.githubusercontent.com/78556152/210743834-9234c2c0-8252-46b8-a519-9ded165aa05f.png)


A new keras model is trained with 15 epochs and the results are remarkable. The training accuracy is 80% and the validation accuracy is 78%. The closeness of the training results indicate that the model fit well. This is also shown in the training results below.

## Visualizing the Training Results of the New Model

![training_and_validation_accuracy_and_loss_2](https://user-images.githubusercontent.com/78556152/210744936-68980afa-25ea-45d8-a584-67d49918c45c.png)


## Prediction on new data

The model's prediction results on new data are great. It gives good results with a high percentage accuracy and confidence as shown in the code snippet below.

![Screenshot 2023-01-05 122417](https://user-images.githubusercontent.com/78556152/210746068-4cfff8b7-954b-4827-9c3f-66867ff40895.png)


## Save the model
I finally saved the model then served it with tensorflow serving in docker during deployment

![Screenshot 2022-12-19 163305](https://user-images.githubusercontent.com/78556152/208437768-30dcdcae-5299-4bd3-a1e4-254350f384f6.png)
