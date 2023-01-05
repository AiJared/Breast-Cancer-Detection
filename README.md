# Breast-Cancer-Detection
A deep learning project of breast cancer detection using tensorflow


Given a dataset of breast cancer images, I created this project to classify them in classes of benign, malignant and normal together with their masked images respectively.
Here a keras model is trained for classification then a prediction is made on new data.

The dataset was downloaded from kaggle then loaded from my local storage.

Below is a benign image

![sample_benign_tumor](https://user-images.githubusercontent.com/78556152/210738678-258b9e33-9091-47df-8415-230c45734417.png)

I defined the parameters for the loader, that is; batch_size of 32, image height of 180 and image width of 180 

I then split my dataset into training and validation sets. Assigned 80% of my data to training set and the remaining 20% to validation set

Here are some images from my training set

![Screenshot 2022-12-19 152549](https://user-images.githubusercontent.com/78556152/208425910-57ef17fa-f4b8-43d2-81ca-662fa2a75c20.png)

I configured the dataset for perfomance with data.cache and data.prefetch methods. I then standardized the RGB channel values in [0,1] range using tf.keras.Rescalling.

I created a keras Sequential model and compiled it. Below is the model's summary
![Screenshot 2022-12-19 153421](https://user-images.githubusercontent.com/78556152/208427325-4c9ddca0-0170-43d4-8b62-5b9c6941f828.png)

I trained the model for 10 epochs as show below.

![Screenshot 2022-12-19 153741](https://user-images.githubusercontent.com/78556152/208427966-1bf87568-27e9-4f9d-a4ec-1e352e26b4ef.png)


## Visualize training results

plots of accuracy and loss on training and validation sets
![Screenshot 2022-12-19 154430](https://user-images.githubusercontent.com/78556152/208429189-3e6cbb71-3a7b-410a-9fa3-3fc9de670466.png)

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
