# Machine Learning Documentation of Rice Quality Detection - Berasil App

## Table of contents
* [Introduction](#introduction)
* [About Dataset](#dataset)
* [Model Architecture](#model)
* [Machine Learning Project Cycle](#cycle)
* [Labeling and Split Dataset](#labeling)
* [Data Augmentation](#augmentation)
* [Training](#training)
* [Eval](#Eval)
* [Integrate Model with FastAPI](#fastapi)
* [Reference](#reference)

<a name="introduction"></a>
## Introduction
Transfer learning is a popular technique in machine learning (ML) in which knowledge learned from a task is re-used in order to boost performance on a related task. For example, In this case we use Transfer learning for object detection and the model we use Faster R-CNN ResNet152 V1 640x640.

<a name="dataset"></a>
## About Dataset
The dataset utilized by the original from [Berasil Team](https://www.kaggle.com/datasets/fadhelm/rice-dataset) directly from on-the-ground collection efforts, providing a robust foundation for the app's rice quality detection features. Collected through direct field sampling and We have 225 sample images.

We have total 10 classes :
1. batu
2. butir_gabah
3. butir_kapur
4. butir_kepala
5. butir_menir
6. butir_merah
7. butir_patah
8. butir_rusak
9. kutu
10. sekam

<a name="model"></a>
## Model Architecture
![image](https://github.com/zeroix07/ml-capstone/assets/120600614/6c7232fb-c6ad-4784-b748-6ac5033e17e9)

<a name="cycle"></a>
## Machine Learning Project Cycle
![ML-Flowchart](https://github.com/zeroix07/ml-capstone/assets/120600614/3a08fb44-6edf-4477-b755-cc3dbea08d23)

<a name="labeling"></a>
## Labeling and Split Dataset
The dataset consists of training data and test data, where the training data consists of 180 images and the test data consists of 45 images. We labeled the image using [labelImg](https://github.com/HumanSignal/labelImg).

<a name="augmentation"></a>
## Data Augmentation
Data augmentation is a technique used in machine learning and deep learning to artificially increase the diversity of a training dataset by applying various transformations to the existing data. The goal of data augmentation is to improve the performance and generalization of machine learning models, especially in scenarios where the amount of labeled training data is limited. And The result for data augmentation is 633 images. we divide for training data consists of 612 images and test data consists of 21 images. train set 97% and test set 3%.

<a name="training"></a>
## Training
![image](https://github.com/zeroix07/ml-capstone/assets/120600614/519289c3-4781-4139-949a-599bdc6d31ad)

![image](https://github.com/zeroix07/ml-capstone/assets/120600614/f2ccab31-ef64-4144-a261-c03e9837cefb)

> We train the model with 50000 epoch
>

| epoch | Loss/BoxClassifierLoss/classification_loss | Loss/BoxClassifierLoss/localization_loss | Loss/RPNLoss/localization_loss | Loss/RPNLoss/objectness_loss | Loss/regularization_loss | Loss/total_loss | learning_rate |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 50000| 0.00039563698 | 0.0038573607 | 0.0004368036 | 0.00014826868 | 0.006825394 | 0.011663465 | 0.0 |

<a name="eval"></a>
## Eval
> mAP Precision
> 

| DetectionBoxes_Precision/mAP | DetectionBoxes_Precision/mAP (large) | DetectionBoxes_Precision/mAP (medium) | DetectionBoxes_Precision/mAP (small) | DetectionBoxes_Precision/mAP@.50IOU | DetectionBoxes_Precision/mAP@.75IOU |
| --- | --- | --- | --- | --- | --- |
| 0.6513 | -1 | 0.6664 | 0.624 | 0.9271 | 0.7772 |
> mAP Recall
>

| DetectionBoxes_Recall/AR@1 | DetectionBoxes_Recall/AR@10 | DetectionBoxes_Recall/AR@100 | DetectionBoxes_Recall/AR@100 (large) | DetectionBoxes_Recall/AR@100 (medium) | DetectionBoxes_Recall/AR@100 (small) |
| --- | --- | --- | --- | --- | --- |
| 0.2645 | 0.7214 | 0.7258 | -1 | 0.7544 | 0.7061 |

<a name="fastapi"></a>
## Integrate Model with FastAPI
![WhatsApp Image 2023-12-10 at 5 22 49 PM](https://github.com/zeroix07/ml-capstone/assets/120600614/9af04000-20ea-4730-8bbf-3969c8445156)
Integrating a machine learning model with FastAPI involves creating an API endpoint that can receive input data, process it using the model, and return the predictions or results. Before that We upload model in Cloud Storage.

<a name="reference"></a>
## Reference
Model Architecture [Reference](https://arxiv.org/pdf/1512.03385)
