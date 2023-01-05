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


From the above plot, it is clear that there was overfitting, evident by training and validation accuracies being off by large margin

I used two techniques to reduce overfitting.

1. Data Augmentation - generating more training examples from the existing data. Below is an example of an augmented dataset

![Screenshot 2022-12-19 161307](https://user-images.githubusercontent.com/78556152/208434451-c8d3f0a5-aa1b-4a39-8db7-1d9781d7a181.png)

2. Introduced dropout in the network to help reduce overfitting further
![Screenshot 2022-12-19 162117](https://user-images.githubusercontent.com/78556152/208435367-15b6f2ca-6d82-4652-a5c4-41163c87f852.png)


I created a new model, compiled and trained it for 15 epochs and the results were remarkable.
![Screenshot 2022-12-19 162451](https://user-images.githubusercontent.com/78556152/208435964-d0971c9b-af77-4640-bbed-a3f8edc57d4f.png)

## Visualizing the training results of my new model
![Screenshot 2022-12-19 162734](https://user-images.githubusercontent.com/78556152/208436482-aedc762f-2605-4c53-b3e5-2c71217c3033.png)

## Prediction on new data

It made an accurate prediction when an image was laoded and tested
![Screenshot 2022-12-19 162937](https://user-images.githubusercontent.com/78556152/208436999-21573bfc-f046-43ee-af30-5a27ca8dc851.png)


## Save the model
I finally saved the model then served it with tensorflow serving in docker during deployment

![Screenshot 2022-12-19 163305](https://user-images.githubusercontent.com/78556152/208437768-30dcdcae-5299-4bd3-a1e4-254350f384f6.png)
