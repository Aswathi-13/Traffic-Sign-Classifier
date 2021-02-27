# Traffic-Sign-Classifier
Convolutional Neural Networks for Traffic Sign Classifier
=======
![alt text]('./readMe image')

Overview
---
In this code, deep neural networks and convolutional neural networks were used to classify traffic signs. A model was trained and validated so it can classify traffic sign images using the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). After the model was trained, random traffic signs from the web, which are German traffic signs were tested.

The Project
---
The goals / steps of this work are the following:
* Load the data set
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images

### Dataset and Repository

1. Download the data set. The dataset was resized and the images to 32x32. It contains a training, validation and test set.
2. Clone the project, which contains the Ipython notebook and the writeup template.
```sh
git clone https://github.com/udacity/CarND-Traffic-Sign-Classifier-Project
cd CarND-Traffic-Sign-Classifier-Project
jupyter notebook Traffic_Sign_Classifier.ipynb
```
3. I followed Udacity classroom instructions

The Architecture
----
The network model was inspired from LeNet Architecture and few modifications and tuning was done to avoid overfitting of the data. The model worked with a training accuracy of * and testing accuracy of *. 
