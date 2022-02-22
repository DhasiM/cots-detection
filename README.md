# [Help Protect the Great Barrier Reef Kaggle Competition.](https://www.kaggle.com/c/tensorflow-great-barrier-reef/overview)
## COTS Detection Model 

This repo contains code, datasets, and other resources for a model that detects crown-of-thorns starfish in deep seas videos.
It is the collective work of members of the [DSI-Marls Team](#Team). The team was formed for Module 1 of the [Africa Data Science Intensive Program, 2022](http://dsi-program.com/)

![Reef](https://blogger.googleusercontent.com/img/a/AVvXsEj6-rQw5r22Bt47BUTtW5bn_dcWT7zMeADwtvsAHS3kBt6w8eWTmCM649ZcJcvosIMup6flKFIaI8p4M9ZzH1yXpEaMRjvwwfVZ_hMqgXCxtwNzEK25vTa-J2ly20by3M1zx7rTymo-tBI6Fq-mj1SJfCOXsOz0Ou1Esi4h2omvQSW98AjsONsVS-EA)

### About the project 

The goal of the competition was to accurately identify starfish in real-time by building an object detection model trained on underwater videos of coral reefs. 

The crown-of-thorns starfish are a particular coral eating starfish that are threatening Australia's Great Barrier Reef. To find and control overpopulation of this species,a traditional reef survey method, called "Manta Tow", is performed by a snorkel diver. While towed by a boat, the divers visually assess the reef, stopping to record variables observed every 200m. This method has obvious limitations. 

The Great Barrier Reef Foundation established an innovation program to develop new survey and control methods. Teaming up with Google, Australia’s national science agency, CSIRO, aims to develop innovative machine learning technology that can analyse large image datasets accurately, efficiently, and in near real-time.

This repo is DSI-2022 Team 3's attempt to create an object detection model for this purpose.

### Contents
* [Overview](#overview)
* [Technologies](#technologies)
* [Setup](#setup)
* [Notebook](#notebook)
* [Resources](#resources)
* [Team](#team)

### Overview
Why [YOLO](https://www.analyticsvidhya.com/blog/2018/12/practical-guide-object-detection-yolo-framewor-python)? 

The project required a model that was; 
* fast (<9hours to execute on the hidden test data), 
* lightweight (able to run on Kaggle's public API with it's 1GPU limit) 
* and can detect objects in real-time.

And the team, being new to object detection, needed a model that was precise as well as easy to train and deploy. [Ultralytics](https://ultralytics.com/yolov5) claims their [YOLOv5](https://github.com/ultralytics/yolov5) models are exactly that. 
![Yolov5](https://cdn-images-1.medium.com/max/1024/0*XfVf5tdxHOnogHbU.png)
We used a [YOLOv5s](https://github.com/ultralytics/yolov5/releases) pre-trained checkpoint and included object traking with NoFair. The purpose of the tracking was to avoid detecting the same starfish in multiple frames of the video. 

We attempted to train our own model from scratch, but due to computational limitations we settled on using a publicly available [YOLOv5s](https://github.com/ultralytics/yolov5) checkpoint trained on the [greatbarrierreef](https://www.kaggle.com/c/tensorflow-great-barrier-reef/overview) dataset by [Sheep](https://www.kaggle.com/steamedsheep). 


### Technologies
* [Python >=3.8.0](https://www.python.org/)
* [YOLOv5](https://github.com/ultralytics/yolov5)
* [Pytorch >=1.7](https://pytorch.org/)
* [NoFair](https://github.com/tryolabs/norfair)


### Setup
To begin working with YOLO in PyTorch is as easy as:
* Clone the repo and install the requirements
  ```
  git clone https://github.com/ultralytics/yolov5  # clone
  cd yolov5
  pip install -r requirements.txt  # install
  ```

After which you can train the model on custom data or jump right into inference if using COCO type datasets.

### Notebook
Our code and report for training and inference on the [greatbarrierreef](https://www.kaggle.com/c/tensorflow-great-barrier-reef/overview) dataset is in this [notebook](https://github.com/DhasiM/cots-detection/blob/main/DSI_MasterNotebook.ipynb)

#### F2 Score of Pretrained Model Used
The competition was evaluated on the F2 metric.

![F2 Score of model used](https://github.com/DhasiM/cots-detection/blob/main/Report%20Images/F2_Score.PNG)
![True Positves](https://github.com/DhasiM/cots-detection/blob/main/Report%20Images/tp.PNG)
![False Positive distribution](https://github.com/DhasiM/cots-detection/blob/main/Report%20Images/Fp.PNG)


### Resources
![noob](https://c.tenor.com/XH9VpXFGzYYAAAAS/noob-loser.gif) We couldn't have done it by ourselves. 

This project was inspired by the work and tutorials of the following pythonistas, kaggle gurus and python resources:

#### Coding inspiration and datasets
* Training: [Awsaf](https://www.kaggle.com/awsaf49/great-barrier-reef-yolov5-train)
* Inference: [Awsaf](https://www.kaggle.com/awsaf49/great-barrier-reef-yolov5-infer)
* Tracking: [NatureZhang](https://www.kaggle.com/naturezhang/yolov5-detections-tracking-on-cot)
* COTS Pre-trained YOLOv5 model and datasets: [Sheep](https://www.kaggle.com/steamedsheep) and [Good Moon](https://www.kaggle.com/freshair1996)

#### Github:
* [Branchflow control](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)  
* [Gitflow](https://jeffkreeftmeijer.com/git-flow/)      
                                                                                      

#### Machine Learning 
* [Kaggle Intro To Machine Learning](https://www.kaggle.com/learn/intro-to-machine-learning)
* [Kaggle Intro To Deep Learning](https://www.kaggle.com/learn/intro-to-deep-learning)

#### Computer Vision
* [Kaggle Computer Vision ](https://www.kaggle.com/learn/computer-vision)

### YOLO
* [YOLOv5](https://docs.ultralytics.com/quick-start/)
* [AnalyticsVidhya](https://www.analyticsvidhya.com/blog/2018/12/practical-guide-object-detection-yolo-framewor-python)
* [YOLOv5 Tips for Best Results](https://docs.ultralytics.com/tutorials/training-tips-best-results/)

### EfficientDet0
* [Inference with EfficientDet0](https://www.kaggle.com/khanhlvg/inference-using-efficientdet-d0-model-tensorflow)
* [Tensorflow API](https://neptune.ai/blog/how-to-train-your-own-object-detector-using-tensorflow-object-detection-api)

### YoloX
[YOLOx training pipeline](https://www.kaggle.com/remekkinas/yolox-training-pipeline-cots-dataset-lb-0-507?scriptVersionId=81353936)

### Model Selection and Validation
[Model Evaluation, Model Selection, and Algorithm
Selection in Machine Learning](https://arxiv.org/pdf/1811.12808.pdf)


## Team
* [Sitwala](https://github.com/SitwalaM)
* [LaliAli](https://github.com/laliali20)
* [Antsa](https://github.com/AntsaHoneywinner)
* [Rhodasi](https://github.com/DhasiM)
* Tutor : [Martin Page](https://github.com/martinjpage)

![ML](https://miro.medium.com/max/2956/0*mF8oEQbABNtoZprD.gif)
