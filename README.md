# Breast-Cancer-Detection
A deep learning project of breast cancer detection using tensorflow


Given a dataset of breast cancer images, I created this project to classify them in classes of beningn and malignant.
Here a keras model is trained for classification then a prediction is made on new data.

The dataset was downloaded then loaded from my local storage, i.e, saved in the same directory as my project's jupyter file

Below is a benign image

![Screenshot 2022-12-19 151652](https://user-images.githubusercontent.com/78556152/208424435-4009f7eb-fde5-4da3-b83b-770cf737c97e.png)

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

plots of accuracy and loss and training and validation sets
![Screenshot 2022-12-19 154430](https://user-images.githubusercontent.com/78556152/208429189-3e6cbb71-3a7b-410a-9fa3-3fc9de670466.png)

From the above plot, it is clear that there was overfitting, evident by training and validation accuracies being off by large margin
