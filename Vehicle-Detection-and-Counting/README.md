# VEHICLE DETECTION,TRACKING AND COUNTING
This project focuses on "Vehicle Detection, Tracking and Counting" using [**TensorFlow Object Counting API**]

## Functionalities of this project

This project has more functionalities than just counting vehicles, they are : 

- Detection and classification of the vehicles (car, truck, bicycle, motorcycle, bus)
- Approximation of vehicle color
- Detection of vehicle direction of travel(up or down)
- Prediction of the speed of the vehicle
- **The images of detected vehicles are cropped from the video frames, and they are saved as new images in
 [captured_vehicles]folder 
- **The program gives a .csv file as an output ([traffic_measurement.csv]

 Recommendations
- Use a better detection model.
- Use a a python virtual environment to run the project 


## Theory

### System Architecture

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/103478400-80414280-4dd7-11eb-9874-3735359e2c20.png">
</p>

- Vehicle detection and classification have been developed using TensorFlow Object Detection API
- Vehicle speed prediction has been developed using OpenCV via image pixel manipulation and calculation
- Vehicle color prediction has been developed using OpenCV via K-Nearest Neighbors Machine Learning Classification Algorithm that uses Trained Color Histogram Features

[TensorFlow](https://www.tensorflow.org/) is an open source software library for numerical computation using data flow graphs. Nodes in the graph represent mathematical operations, while the graph edges represent the multidimensional data arrays (tensors) communicated between them.

[OpenCV (Open Source Computer Vision Library)](https://opencv.org/about.html) is an open source computer vision and machine learning software library. OpenCV was built to provide a common infrastructure for computer vision applications and to accelerate the use of machine perception in the commercial products.

### Tracker

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/41812993-a4b5a172-7735-11e8-89f6-083ec0625f21.png" | width=700>
</p>

The source video is read frame by frame using OpenCV. Each frame is processed by the ["SSD Mobilenet model](http://download.tensorflow.org/models/object_detection/) is developed on TensorFlow. There is a loop that continues working until it reaches the end of the video. The main pipeline of the tracker is given at the above Figure.

### Model

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/48481757-b1d5a900-e81f-11e8-824b-4317115fe5b4.png">
</p>

An ["SSD Mobilenet" model] is used (http://download.tensorflow.org/models/object_detection) in this project. 
Visit the [detection model zoo](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md) 
for a list of other models that can be used with varying speeds and accuracies.

*The minimum vehicle detection threshold can be set [in this file](utils/visualization_utils.py) in terms of percentage.

The default minimum vehicle detection threshold is 0.5!*

## Installation
If you have an Nvidia GPU you can do the following:
**Docker setup with Nvidia GPU:**
Run the demo in the GPU without installing anything, just nvidia-docker. The command to set up this docker:

    docker-compose up
    
Alternative for nvidia-docker, you can follow the installation steps are given below!

**1.) Python and pip**

Python is automatically installed on Kali Linux.
Confirm (by issuing a python -V command) that one of the following Python versions is already installed on your system:

- Python 3.3+

The pip or pip3 package manager is usually installed on Kali Linux. 
Take a moment to confirm (by issuing a *pip -V* or *pip3 -V* command) that pip or pip3 is installed. 
The recommended version is  8.1 or higher of pip or pip3.
If version 8.1 or later is not installed,run the following command, which will either install or upgrade to the latest pip version:

    $ sudo apt-get install python3-pip python3-dev # for Python 3.n
    
**2.) OpenCV**

See required commands to install OpenCV on Debian/Kali Linux in 
[here](https://www.geeksforgeeks.org/how-to-install-opencv-for-python-in-linux/).

**3.) TensorFlow**

Install TensorFlow using the following command:

    $ pip3 install tensorflow     # Python 3.n;
    

**4.) TensorFlow Object Detection API**

See required commands to install TensorFlow Object Detection API on Kali Linux in [here]
(https://github.com/rwightman/tensorflow-models/blob/master/research/object_detection/g3doc/installation.md).
  
If you are still getting problem about installation after the step given above, 
visit [link](https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/) 

---

**How to run the program**

After completing these 4 installation steps that are given at above, you can test the project by one of these commands.
Program takes an input argument 'imshow' or 'imwrite':

      python3 main.py imshow video-path
      python3 main.py imwrite video-path

- *imshow*  : shows the processed frames as an video on screen.
- *imwrite* : saves the processed frames as an output video in the 'videos' folder.

---
