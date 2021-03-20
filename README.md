# Mask R-CNN for Stone detection in Off-Road environment

This example, originally adapted from the Matterport repository (https://github.com/matterport/Mask_RCNN) showcases the implementation of Mask R-CNN (https://arxiv.org/abs/1703.06870) on Python (version 3), TensorFlow and Keras. The model has the capability to generate bounding boxes and segmentation masks in stones present in the images. It is based on Feature Pyramid Network (FPN) and a ResNet101 backbone.

<img src = "samples/stone/Validation result/Random_Images/download (1).png" > 

The repository further includes:

1. Source code of Mask R-CNN built on FPN and ResNet101.
2. Training code for stone detection.
3. Pre-Trained weights (only 1 epoch) for Stone detection.
-----------

# Updated (Full) project details under Inferences folder

# Training on your own stone dataset

As a basis of detecting stones and presenting them with a color splash, go through this incredible example (https://engineering.matterport.com/splash-of-color-instance-segmentation-with-mask-r-cnn-and-tensorflow-7c761e238b46) in which the same has been done with the help of Balloon. It covers the whole process starting from annotating images to training to using the results in your own application.

While making your own dataset, follow the following steps:

1. Make a folder named "datasets" inside the main repository.
2. Inside datasets, follow the sequence 
    > -> stone_dataset > stone 
3. Extend the stone folder by making 2 subfolders named "train" (for training) and "val" (Validation). With your images, separate them according to your needs and put them in both of these folders. With the help of VIA (VGG Image Annotator), annotate your images and make sure to have a correct format. (http://www.robots.ox.ac.uk/~vgg/software/via/via-1.0.6.html)   

# Training the model

To train a new model, you have options to train on different weights:

**Training a new model starting from pre-trained COCO weights**
```bash 
python3 samples/stone/stone.py train --dataset=/path/to/stone/ --model=coco
```
**Training  a new model starting from ImageNet weights**
```bash
python3 samples/stone/stone.py train --dataset=/path/to/stone/ --model=imagenet
```
**Continue training a model that you had trained earlier**
```bash
python3 samples/stone/stone.py train --dataset=/path/to/stone/ --model= /path/to/mask_rcnn_stone_0001.h5
```

------

# Requirements 
Python 3.4, TensorFlow 1.3, Keras 2.0.8 and other common packages listed in ```requirements.txt```

# Installation

1. Clone this repository
2. Install dependencies
    ```bash
      pip3 install -r requirements.txt
    ```
3. Run setup from the repository root directory 
    ```bash
      python3 setup.py install
    ```
4. The stone weights are already present in logs folder

# Results

<img src = "samples/stone/Validation result/Random_Images/download (27).png">
<img src = "samples/stone/Validation result/Dataset_Images/download (4).png">
<img src = "samples/stone/Validation result/Dataset_Images/download (12).png">
<img src = "samples/stone/Validation result/Dataset_Images/download (14).png">

------