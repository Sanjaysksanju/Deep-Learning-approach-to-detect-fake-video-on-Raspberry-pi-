# Deep-Learning approach to detect fake video on Raspberry Pi (Deep Learning (ResNext and LSTM))

## Give a Star⭐ to repo and Don't forget to <a href="https://www.buymeacoffee.com/abhijitjadhav" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 35px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a> 

</a>

## Latest Update
#### We have dockerised the [Django Application](https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning/tree/master/Django%20Application) now you can spin up a container within seconds without worring about dependencies


## 1. Introduction
This projects aims in detection of video deepfakes using deep learning techniques like ResNext and LSTM. We have achived deepfake detection by using transfer learning where the pretrained ResNext CNN is used to obtain a feature vector, further the LSTM layer is trained using the features. For more details follow the [documentaion](https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning/tree/master/Documentation).

You can also watch [this Youtube video](https://www.youtube.com/watch?v=_q16aJTXVRE) to get a better intuition about the project.
You can watch [this playList](https://www.youtube.com/watch?v=quJ8Rv84oA0&list=PLNIj0dkfMA1FsD5xR4IEc8vdwr66_WExl) for step by step installation.

You can read more about the project on <a href="https://abhijithjadhav.medium.com/deepfake-video-detection-using-long-short-term-memory-df3674f83ecc" target="_blank"><img src="https://img.shields.io/badge/Medium-12100E?style=for-the-badge&logo=medium&logoColor=white" alt="Medium" /></a>&nbsp;


## 2. Directory Structure
For ease of understanding the project is structured in below format
```
Deepfake_detection_using_deep_learning
    |
    |--- Django Application
    |--- Model Creation
    |--- Documentaion
```
1. Django Application 
   - This directory consists of the django made application of our work. Where a user can upload the video and submit it to the model for prediction. The trained model performs the prediction and the result is displayed on the screen.
2. Model Creation
   - This directory consists of the step by step process of creating and training a deepfake detection model using our approach.
3. Documentation
   - This directory consists of all the documentation done during the project
   
## 3. System Architecture
<p align="center">
![image](https://github.com/Sanjaysksanju/Deep-Learning-approach-to-detect-fake-video-on-Raspberry-pi-/assets/133668271/1a246816-d6ba-4a99-b1de-b8f315fa6eec)

</p>

## 4. Demo 
### You can watch the [youtube video](https://www.youtube.com/watch?v=_q16aJTXVRE&t=823s) for demo

<p align="center">
  <img src="https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning/blob/master/github_assets/fakegif.gif" />
</p>

## 5. Our Results

| Model Name | No of videos | No of Frames | Accuracy |
|------------|--------------|--------------|----------|
|model_84_acc_10_frames_final_data.pt |6000 |10 |84.21461|
|model_87_acc_20_frames_final_data.pt | 6000 |20 |87.79160|
|model_89_acc_40_frames_final_data.pt | 6000| 40 |89.34681|
|model_90_acc_60_frames_final_data.pt | 6000| 60 |90.59097 |
|model_91_acc_80_frames_final_data.pt | 6000 | 80 | 91.49818 |
|model_93_acc_100_frames_final_data.pt| 6000 | 100 | 93.58794|

## 6. Contributors
   1. Sanjay S K
   2. Supriya G K
   3. Sachidanand M
   4. Harshitha G
   
## 7. License

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

## 8. We welcome Open Source Contribution. 
### Below are the some changes that can be applied to the project. New Ideas will be appreciated.
- [ ] Deploying the applications in free cloud 
- [ ] Creating open source API for detection
- [ ] Batch processing of entire video instead of processing first 'x' frames.
- [ ] Optimizing the code for faster execution.
#### Completed 
- [X] Dockerizing the app
- [X] ~~Enabling working of project on Non Cuda Computers. i.e on normal or AMD GPUs~~ : not possible as dlib uses CUDA internally

## 9. Dont forget to Star⭐ this repo 😉 and  <a href="https://www.buymeacoffee.com/abhijitjadhav" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 35px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a> 


###############################################################################################################################################################################
# Deep fake detection Django Application
## Requirements:

**Note :** Nvidia GPU is mandatory to run the application.
- CUDA version >= 10.0 for GPU
- GPU Compute Capability > 3.0 


You can find the list of requirements in [requirements.txt](https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning/blob/master/Django%20Application/requirements.txt). Main requirements are listed below:

```
Python >= v3.6
Django >= v3.0
```

## Directory Structure

- ml_app -> Directory containing code in views.py file
- project_settings -> Contains Django settings and files to run in production
- static -> Contains all css, js and json files (for face-api)
- templates -> Template files for HTML

<b>Note:</b> Before running the project make sure you have created directories namely <strong>models, uploaded_images, uploaded_videos</strong> in the project root and that you have proper permissions to access them.
# Running application on Docker
#### Step 1: Install docker desktop and start the Docker daemon

#### Step 2: Run the deepfake detection docker docker image
```
docker run --rm --gpus all -v static_volume:/home/app/staticfiles/ -v media_volume:/app/uploaded_videos/ --name=deepfakeapplication abhijitjadhav1998/deefake-detection-20framemodel
```
#### Step 3: Run the Ngnix reverse proxy server docker image
```
docker run -p 80:80 --volumes-from deepfakeapplication -v static_volume:/home/app/staticfiles/ -v media_volume:/app/uploaded_videos/ abhijitjadhav1998/deepfake-nginx-proxyserver
```
#### Step 4: All set now launch up your application at [http://localhost:80](http://localhost:80)

### Step 5: Star⭐ this repo 😉 on <a href="https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning" >  <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" /> </a> and   Star⭐ this image on <a href="https://hub.docker.com/r/abhijitjadhav1998/deefake-detection-20framemodel">  <img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white" /> </a>

## We deserve a Coffee ☕ <a href="https://www.buymeacoffee.com/abhijitjadhav" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 35px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a> <a href="https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning" target="_blank"><img src="https://img.shields.io/badge/UPI-abhijit.jadhav1%40ybl-brightgreen" alt="Medium" style="height: 35px !important;width: 250px !important;"/></a>&nbsp;


Please note that currently we have only pushed the image of 20 Frames model, If you can to create your own image of other frames model follow the steps given in the [blog](https://abhijithjadhav.medium.com/dockerise-deepfake-detection-django-application-using-nvidia-cuda-40cdda3b6d38).

# Running application locally on your machine

### Prerequisite
1. Copy your trained model to the models folder.
   - You can download our trained models from the [Google Drive](https://drive.google.com/drive/folders/1UX8jXUXyEjhLLZ38tcgOwGsZ6XFSLDJ-?usp=sharing) or you can train your models using the steps mentioned in Model Creation directory.

#### Step 1 : Clone the repo and Navigate to Django Application

`git clone https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning.git`

#### Step 2: Create virtualenv (optional)

`python -m venv venv`

#### Step 3: Activate virtualenv (optional)

`venv\Scripts\activate`

#### Step 4: Install requirements

`pip install -r requirements.txt`

#### Step 5: Copy Models

`Copy your trained model to the models folder i.e Django Application/models/`

- You can download our trained models from [Google Drive](https://drive.google.com/drive/folders/1UX8jXUXyEjhLLZ38tcgOwGsZ6XFSLDJ-?usp=sharing)

**Note :** The model name must be in specified format only i.e *model_84_acc_10_frames_final_data.pt*. Make sure that no of frames must be mentioned after certain 3 underscores `_` , in the above example the model is for 10 frames.


### Step 6: Run project

`python manage.py runserver`

## Demo 
### You can watch the [youtube video](https://www.youtube.com/watch?v=_q16aJTXVRE&t=823s) for demo
<p align="center">
  <img src="https://github.com/abhijitjadhav1998/Deepfake_detection_using_deep_learning/blob/master/github_assets/fakegif.gif" />
</p>  

