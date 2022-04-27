# FaceMaskDetection

## Features
- __Lightweight models:__  only `2,422,339` and `2,422,210` parameters for the MFN and RMFD models, respectively
- __Detection of multiple faces:__ able to detect multiple faces in one frame
- __Support for detection in webcam stream:__ our app supports detection in images and video streams 
- __Support for detection of improper mask wearing:__ our MFN model is able to detect improper mask wearing including
  (1) uncovered chin, (2) uncovered nose, and (3) uncovered nose and mouth.

## About
This app detects human faces and proper mask wearing in images and webcam streams. 

Under the COVID-19 pandemic, wearing
mask has shown to be an effective means to control the spread of virus. The demand for an effective mask detection on 
embedded systems of limited computing capabilities has surged, especially in highly populated areas such as public 
transportations, hospitals, etc. Trained on MobileNetV2, a state-of-the-art lightweight deep learning model on 
image classification, the app is computationally efficient to deploy to help control the spread of the disease.

## Frameworks and Libraries
- __[OpenCV](https://opencv.org/):__ computer vision library used to process images
- __[OpenCV DNN Face Detector](https://github.com/opencv/opencv/blob/3.4.0/samples/dnn/resnet_ssd_face_python.py):__ 
  Caffe-based Single Shot-Multibox Detector (SSD) model used to detect faces
- __[Tensorflow](https://www.tensorflow.org/) / [Keras](https://keras.io/):__ deep learning framework used to build and train our models
- __[MobileNet V2](https://arxiv.org/abs/1801.04381):__ lightweight pre-trained model available in Keras Applications; 
  used as a base model for our transfer learning
- __[Dash](https://plotly.com/dash/):__ framework built upon Plotly.js, React and Flask; used built the demo app

## Setup
1. Open your terminal, `cd` into where you'd like to clone this project, and clone the project:
```
$ git clone https://github.com/sidx255/FaceMaskDetection
```
2. Download and install Miniconda [here](https://docs.conda.io/en/latest/miniconda.html).
3. Create an environment with the packages on `requirements.txt` installed:
```
$ conda create --name env_name --file requirements.txt
```
4. Now you can `cd` into the clone repository to run or inspect the code.

## How to Run

### To detect masked faces in images
`cd` into `/src/` and enter the following command:
```
$ python detect_mask_images.py -i <image-path> [-m <model>] [-c <confidence>]
```

### To detect masked faces in webcam streams
`cd` into `/src/` and enter the following command:
```
$ python detect_mask_video.py [-m <model>] [-c <confidence>]
```

### To train the model again on the dataset
`cd` into `/src/` and enter the following command:
```
$ python train.py [-d <dataset>]
```
Make sure to modify the paths in `train.py` to avoid overwriting existing models.

Note: 
- `<image-path>` should be relative to the project root directory instead of `/src/`
- `<model>` should be of `str` type; accepted values are `MFN` and `RMFD` with default value `MFN`
- `<confidence>` should be `float`; accepting values between `0` and `1` with default value `0.5`
- `<dataset>` should be of `str` type; accepted values are `MFN` and `RMFD` with default value `MFN`

### Run the app yourself
1. Run the app:
```
$ python main.py
```
2. Enter `http://127.0.0.1:8050/` in your browser to open the app on the Dash app's default host and port. Feel free to modify
the host and port number if the default port is taken.

## Author
[sidx255](https://github.com/sidx255)
