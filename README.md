# Gesture-recognition #

## Goal of the project ##
The goal is to develop a cool feature in the smart-TV that can recognise five different gestures performed by the user which will help users control the TV without using a remote. The gestures are continuously monitored by the webcam mounted on the TV. Each gesture corresponds to a specific command:

Thumbs up:  Increase the volume
Thumbs down: Decrease the volume
Left swipe: 'Jump' backwards 10 seconds
Right swipe: 'Jump' forward 10 seconds  
Stop: Pause the movie
 

Each video is a sequence of 30 frames (or images)

## Understanding the Dataset ##
The training data consists of a few hundred videos categorised into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames(images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use. 

 The data is in a zip file. The zip file contains a 'train' and a 'val' folder with two CSV files for the two folders. These folders are in turn divided into subfolders where each subfolder represents a video of a particular gesture. Each subfolder, i.e. a video, contains 30 frames (or images). Note that all images in a particular video subfolder have the same dimensions but different videos may have different dimensions. Specifically, videos have two types of dimensions - either 360x360 or 120x160 (depending on the webcam used to record the videos). Hence, we  will need to do some pre-processing to standardise the videos. 


Each row of the CSV file represents one video and contains three main pieces of information - the name of the subfolder containing the 30 images of the video, the name of the gesture and the numeric label (between 0-4) of the video.


The task is to train a model on the 'train' folder which performs well on the 'val' folder as well (as usually done in ML projects).


## Approach Taken ##
### 1) Data Pre-Processing : ###
 The proprocessing of data is performed in a Generator Function . As we have 2 different dimensions of images ,
 all of them are cropped to same size .Also batches of video frames are created to be fed to the training model.
 Data was split as train and test data and an epoch and batch size variable was created to vary their values to inspect performance of model.
### 2) Model Building : ###
 Started with a simple 7 layer 3D convolution network and Adam optimiser. 
 Evaluated model based on categorical accuracy by plotting training epochs vs model accuracy . 
 val_categorical_accuracy turned out to be 0.2222 which is very low. Tried creating 2 more variations of the conv 3d model by adding more layers . 
 The validation accuracy did not improve much and stood at 56%.
 Hence , tried a conv 2d model with time distributed layers the validation categorical accuracy improved significantly from 56% to 76%. 
 Further tweaking the model by adding LSTM layers did not make any further improvements.

## Further Work ##
I am looking forward to solve this porblem starting with a pre- trained model using transfer learning and to fine tune it to get better accuracy.

