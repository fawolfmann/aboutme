#  Image classification of wheat plant disease
This was my final project to achieve the title of compute engineer. 
In this blog i'll explain how i did it and which tools i used.

In this project i created my own image dataset to work with.
Some of the code used is on [github](https://github.com/fawolfmann/Tesis)

This project was created with the help of [INTA](https://www.argentina.gob.ar/inta) Argentinian agriculture institute and received a scholarship of [SECyT](https://www.unc.edu.ar/ciencia-y-tecnolog%c3%ada/) Argentinian University Technology and Science secretary.

## The problem
The problem we pose is the lose of grain on wheat harvest caused by leaf disease. 

In the next images we see the kind of leaf disease that are more common in the wheat. 

| Healthy        | Mildew           | Leaf Spot  | Rust |
| :-------------: |:-------------:| :-----:| :-----: |
| ![]({{site.url}}/aboutme/images/tesis/problem1.png) | ![]({{site.url}}/aboutme/images/tesis/problem2.png) | ![]({{site.url}}/aboutme/images/tesis/problem3.png) | ![]({{site.url}}/aboutme/images/tesis/problem4.png)|

As you can see in the images they are slightly different, with the idea is to classify this images and define if a leaf have a disease. 

So now we have defined our problem next we will see wich technic we used
## Convolutions neural networks
For the image classification we will use CNN or Convolutions neural networks. 
This is not a CNN course but will make a little intro.

#### CNN Architecture
![]({{site.url}}/aboutme/images/tesis/cnn_architecture.png)
Image from [Google](https://developers.google.com/machine-learning/practica/image-classification/convolutional-neural-networks)


A CNN basically is made of 2 modules, the first is the convolutional module that is used to create a feature map of an image. It made convolution with the patterns it was trained, in the firsts layers it look for basics patters ass lines or circles but in the deep convolutions it look for more complex patterns as a leg or a face in the case of a CNN trained to classify people. 


The second module is the classification module, its a dense layer or fully connected layer that use the feature map as input and give a classification as an output, it trains the connection weights to classify.

This is a very short intro if you want to get a deeper knowleadge of computer vision i recomnend this [Standford Course](http://cs231n.stanford.edu/) contains the slides and syllabus and the YouTube [videos](https://www.youtube.com/watch?v=vT1JzLTH4G4).

## Creation of dataset
We create an image dataset crawling image from the web and taking photos in the field. After the images where validated and labeled we got:


| Label        	| Amount     	|
| :----------:	|:----------:	| 
| Healthy		| 113 			| 
| Mildew		| 102		    |   
| Leaf Spot		| 122   		|   
| Rust			| 159			|

This is a small amount of pictures to work with but we handle to generate a good solution

## Installation
To the training part i install everything on a server with a Titan X GPU 

I used docker with a Tensorflow 2.0 image and run everything on Jupyters notebooks. All the code was build with Keras. 

## Training of models
In the training steps i made 3 iteration to get the final results. 

### Iteration 1
Transfer learning of models trained with IMAGENET. 
Data augmentation

### Iteration 2
Re-train the models with PlantVillage dataset and after transfer learning with my own data set. 

### Iteration 3 
Cut my dataset with UEA labeling tool and again transfer learning the network trained with PlantVillage.


## Android app implementation
After we trained successfully a model we convert it with TensorflowLite and created an Android app to use this trained model and make predictions on the device.

## Conclusions