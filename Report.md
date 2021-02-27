# **Traffic Sign Recognition** 

## Writeup

### You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./images/graph.png "Visualization"
[image4]: ./test_images/check/11_Right_of_way.jpg "Traffic Sign 1"
[image5]: ./test_images/check/12_Priority_road.jpg "Traffic Sign 2"
[image6]: ./test_images/check/13_Yield.jpg "Traffic Sign 3"
[image7]: ./test_images/check/31_Wild_animals_crossing.jpg "Traffic Sign 4"
[image8]: ./test_images/check/34_Turn_left_ahead.jpg "Traffic Sign 5"

### Detailed Writeup 

### Data Set Summary & Exploration

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is 34799
* The size of the validation set is 12630
* The size of test set is 4410
* The shape of a traffic sign image is (32, 32, 3)
* The number of unique classes/labels in the data set is 43

#### 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data is distributed within the three sets

![alt text][image1]

### Design and Test a Model Architecture

Initially the data was shuffled to make sure that the order of the data donot affect the convelutional neural network. Normalising technique like `(pixel-128)/128` was performed. But the network worked well with shuffling itself. 

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x3 RGB image   							| 
| Convolution 3x3     	| 1x1 stride, valid padding, outputs 28x28x6 	|
| RELU					|												|
|Convolution 3x3     	| 2x2 stride, valid padding, outputs 14x14x10 	|
| RELU					|												|
|Convolution 3x3     	| 1x1 stride, valid padding, outputs 8x8x6 		|
| RELU					|												|
|Max pooling	      	| 2x2 stride,  outputs 4x4x16	 				|
| flatten			    | output 256   									|
| Fully connected		| Input = 256. Output = 120.					|
| RELU					|												|
|drop out				|												|
| Fully connected		| Input = 120. Output = 100.					|
| RELU					|												|
| Fully connected		| Input = 100. Output = 84.						|
| RELU					|												|
|Fully connected		| Input = 84. Output = 43.						|

 


#### Training the model
To train the model, I used an Adam Optimiser, epoch 50, batch size of 128, mean 0, std deviation 1, learning rate of 0.0009 and keep probability of 0.5.

#### 4. Approach

My final model results were:
* training set accuracy of 0.997
* validation set accuracy of 0.957
* test set accuracy of 0.943

Initially the LeNet architecture from the tutorial was used. As mentioned in the notebook, the accuracy was not as per requirement. I then played with some hyper parameters and i tried to change it to get a better result. But then realised the architecture was not good enough.

Immediate thought was to add a convolutional layer and fully connected layer. Still the architecture was overfitting. A high accuracy on the training set but low accuracy on the validation set indicates over fitting. Then i introduced the drop out. The model was improved. Took a number of trials to finalise the epoch and learning rate. Intial epoch was 20 and learning rate was 0.005, but the model was still over fitting. Epoch was increased to 60 and then resuced to 50. Learning rate was reduced to 0.0009. The validation accuracy was increased to 95%


### Test a Model on New Images

Here are five German traffic signs that I found on the web:

![alt text][image4] ![alt text][image5] ![alt text][image6] 
![alt text][image7] ![alt text][image8]

The 'right-of-way' image might be difficult to classify because there are many other traffic sign board with the same shape and colour. Similarly 'turn left ahead' can be confused with 'go ahead or left'.

#### 2. Predictions on the new images

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Turn left ahead      	| Turn left ahead								| 
| Right-of-way     		| Right-of-way									|
| Yield					| Yield											|
| Wild animals crossing	| Wild animals crossing			 				|
| Priority road			| Priority road     							|


The model was able to correctly guess 5 of the 5 traffic signs, which gives an accuracy of 100%. 

#### 3. Softmax probabilities of each image
The code for making predictions on my final model is located in the 11th cell of the Ipython notebook.

For the first image, the model is relatively sure that this is a stop sign (probability of 0.6), and the image does contain a stop sign. The top five soft max probabilities were

| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .99         			| 34_Turn left ahead							| 
| 1.26157465e-04		| 38 Keep right									|
| 1.63594200e-06		| 11 Right-of-way at the next intersection		|
| 3.96604777e-10		| 32 Bumpy Road					 				|
| 1.43324644e-10	    | 28 Slippery Road      						|


For the second image 
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00        			| 11_ Right-of-way at the next intersection		| 
| 9.51591410e-12		| 30 Beware of ice/snow							|
|  2.09817671e-17		| 34 Turn left ahead							|
| 3.57186120e-22		| 18 General caution			 				|
| 7.26914372e-23	    | 28 Children crossing    						|

for third image
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00        			| 13  Yield 									| 
| 1.50264826e-25		| 35 Ahead only									|
| 1.20199299e-26		| 9 No passing									|
| 6.97395257e-27		| 38 Keep right					 				|
| 5.15983711e-27	    | 0 Speed limit (20km/h)   						|

For fourth image:
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00        			| 31  Wild animals crossing						| 
| 1.33014399e-20		| 29 Bicycles crossing							|
| 4.01040930e-22		| 21 Double curve								|
| 2.10564419e-22		| 23 Slippery road				 				|
| 1.30737113e-27	    | 25 Road work 									|

fifth image
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .99         			| 12 Priority road 								| 
| 3.72670934e-06		| 41 End of no passing							|
| 3.33458900e-07		| 40 Roundabout mandatory						|
| 7.74057085e-09		| 16 Vehicles over 3.5 metric tons prohibited	|
| 1.55302338e-09	    | 9 No passing									|

