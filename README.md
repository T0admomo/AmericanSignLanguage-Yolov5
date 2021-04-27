# ![](/Assets/banner.png)
Project 5: American Sign Language Detection Project

## The team:
<ul>
 <li>Timothy L Carter - tcarter.era@gmail.com</li>
 <li>Lavanya Bandari </li>
 <li>Matthew Hemsley - mhemsley91@gmail.com </li>
 <li>Carlos Wilwayco <li>
 </ul>

## Table of Contents

1. Problem Statement
2. Tools
3. Proof of Concept
4. Image Dataset Creation 
5. Data Augmentation
6. Executive Summary 
7. Next Steps


## 1. Problem Statement

Their are approximately 500,000 individuals in the United States who's primary language is American Sign Language(ASL). These individuals are left out of many of the advances popularized by Natural Language Processing technologies such as voice commands, and worse, existing technologies have yet to be applied in a way meant to address the already existing gap between the speech impaired and their communities. This project will seek to build a computer vision model to classify 24 of the 26 letters of the American Sign Language Alphabet which do not require movement (j,z). Incorporating gestures was decided to be outside the current scope of the project, and would be for future stages of development. 

## 2. Tools

### Yolov5
A powerful single stage object oriented detection pipeline created by Glenn Jocher. Rather than begin training with the weights and anchors popularized by the COCO training set or others like it, Yolov5 uses a Kmeans algorithm to create custom anchors and weights to begin from for each model training! Yolov5 uses Feature Pyramids to generalize well on object scaling. It helps to identify the same object with different sizes and scales.

Activation Functions: Leaky, Relu, Sigmoid
Optimization Functions: SGD

### Roboflow
Augmentation of Labeled Images Becomes a simple and code free process using Roboflow.com for image augmentation. Our team successfully hard coded augmentations to a dataset of (blank) original images but failed to implement code which maintained the integrity of bounding boxes throughout the augmentation process.

### CVAC Image Labeler 
Easy to use Image Labeler that is Compatible with GitHub and allows groups to share project loads. Exports file in yolo1.1 format.

### Google Collaboratory 
Our was trained using a google Collab TPU to account for hardware deficits.


## 3. Proof of Concept 

### MNIST ASL 
We used a Kaggle MNIST drop in replacement Dataset of over 27,000 28x28p training images and a Random Forest algorithm for proof of concept. The model was well overfit and gave us the optimism to begin creating a real world dataset of images of various pixel sizes ranging from 720p to 4k 

## 4. Image Data Set Creation 
our original dataset was created from 4 photos per letter from the 4 members of the team, and some of their family totaling 418 images in all. The images include examples of at least 4 different skin pigmentations, and include examples of children and adult hands. The four photos taken for each letter were front left right and back views. Some of the back view photos were removed during image labeling as they we more likely to confuse the model than to assist it. 

Labelling methodology was selected to reduce noise in the dataset. bounding boxes will be drawn across the wrist and have minimal extra space around the hand.

## 5. Data Augmentation
This aspect of the project proved to be the most challenging. While the final code for this project exhibits the methods used to augment images with keras and tensorflow libraries, we were unable to maintain the integrity of bounding box data during image augmentation. In order to produce a model in the time allowed, we elected to use Roboflow.com for image augmentation which put limitations on the total number of images in our final augmented dataset. As such the size of our final dataset is 1000 images.

### Train Test Split 
| train | test |
|---|---|
|418|127|

## 6. Executive Summary

### The data
Creating an augmented dataset from scratch proved to be the biggest challenge for our team. With a total of 517 original images, proper augmentation would have left the dataset at around 10,000 images. As it is our final model is trained on 1000 images augmented from an original batch of 517. Labeling our original images was made easy by CVAC image labelling software for bounding boxes. This task was divided amongst the team, with the idea of reconvening at the end of week 1 with a labeled dataset to merge.

Research shows minimizing noise with consistent and quality labeling methodology can have the same effect as doubling the size of a dataset in certain conditions. With this in mind we attempted to pay special attention to our labeling methodology.

If we were to repeat the project, labeling would be assigned to one individual or group of individuals whenever possible to reduce noise in the dataset from varying labeling practices, and to streamline the flow of large image files through our processing pipeline.

### Issues in augmentation
Our augmented image dataset was made using Roboflow.com. Our team managed to perform image augmentation using tensorflow and keras libraries , but were unable to maintain the integrity of bounding boxes associate to each photo during augmentation. Beginning the project, each of us had assessed the augmentation process to be relatively straightforward. Our team now has a stronger appreciation and understanding of the industry importance that tools like Roboflow have to streamlining the computer vision workflow. 

### No greyscale
The decision was made not to reduce our images to grayscale. Although this trick is often used to reduce noise in images and cuts down on image processing time, we felt that the opportunity for grayscale to interfere in the models ability to predict or learn different skin tones was a major drawback best avoided. i.e.) a darkly myelinated hand against a dark background in greyscale may not pick up the hand or visa versa. the RGB scale data avoids this issue.

### Training Yolov5

Training of the Yolv5 model was executed in a Google Collab environment to account of hardware deficits , and to avoid complications with dependencies during model training. This put limitations on our ability to train the model for our desired number of epochs ( 2,000). because of Google's active user requirements, and complications being disconnected from the back end GPU, we were limited to training our model for 200 epochs with a batch size of 50. Due to the small dataset , and our inability to continue model training without further resources, our final performance metrics were as follows.

| recall | precision |
|---|---|
|42.5% |20.1%|
 

## 7. Next Steps & Conclusions

By adjusting the confidence required to make predictions, we were able to get our model to make some accurate predictions, though we then got false positives where two bounding boxes and classifications would be predicted for 1 letter image. 

Next steps are to increase the size of our dataset both with more orginal images, and with augmented images. Maintaining bounding box integrity throughout image augmentation proved to be a major challenge that we would address at the start were to do things differently. Future iterations of this project would involve the comparison of Yolov5 model performance to that of a tailored 2d Convolutional neural network. 

All in all, given the small size of our training set, the first iteration of this project leaves us optimistic about future model performance once the dataset is cleaned and properly augmented. 

Conclusion: A model can be built to interpret the and transcribe the 24 letters of American sign language. Future projects will seek to capture and transcribe a limited set of gestures.



# ![](/Assets/results.png) 






