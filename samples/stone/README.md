# Stone Detection example



This is an example of specifically detecting stone in an off-road terrain with the help of Mask RCNN. This has been referenced from the original blogpost of Mask RCNN  by Matterport (https://github.com/matterport/Mas
k_RCNN). You can read in detail about the procedure of applying splash of colour in the detected object and keeping it throughout at this blogpost by Waleed Abdulla (https://engineering.matterport.com/splash-of-color-instance-segmentation-with-mask-r-cnn-and-tensorflow-7c761e238b46)  

<img src= "Validation result/Random_Images/download (4).png">
--------

**Installation**:
1. You have the choice to use the weights originally trained for balloon (mask_rcnn_balloon.h5) or you can download the coco weights. Additionally, i have trained the model for detecting stone (only 1 epoch due to training limitations) and is present in
    ```bash
    ~/Mask_RCNN/logs/
    ```
    If you wish to save it in the main repository, it should also be fine.

2. The dataset for training the model was created with the help of VIA (VGG Image Annotator) (http://www.robots.ox.ac.uk/~vgg/software/via/via-1.0.6.html). You can also use other annotators, but make sure that the format should be correct. Try to take images as many as you have but try to keep them in the following folder format:

```bash
    ~/Mask_RCNN/datasets/stone_datasets/stone/train
``` 
 
```bash
    ~/Mask_RCNN/datasets/stone_dataset/stone/val.
```
-----
**Applying color splash with the help of stone weights**:

For applying the splash effect on an image use the following command:
```bash
    python3 stone.py splash --weights=/path/to/mask_rcnn/mask_rcnn_stone_0001.h5 --image=< filename or URL >
```

For applying the splashing effect on a video (requiring OpenCV 3.2+) use the following command:
```bash
    python3 stone.py splash --weights=/path/to/mask_rcnn/mask_rcnn_stone_0001.h5 --video=< filename or URL >
```
------

[Training the stone model](https://pandao.github.io/editor.md/en.html)

We can train the model with 3 different weights:

1. Training a new model starting from pre-trained COCO weights :
```bash
    python3 stone.py train --dataset=/path/to/stone/dataset --weights=coco
```

2. You can also resume training a model that you had trained earlier:
```bash
    python3 stone.py train --dataset=/path/to/stone/dataset --weights=last
```
3. Train the new model starting from ImageNet weights:
```bash
    python3 stone.py train --dataset=/path/to/stone/dataset --weights=imagenet  
```
The code in stone.py is set to train for 500 Steps (5 epochs of 100 steps each), while using a batch size of 2. You can update the schedule to fit your needs.

------

**Running the demo version of the model**

With the help of pretrained stone weights (only 1 epoch) you can see the demo version of the model. With this we can test our images (not annotated) and check the accuracy. It takes a random image from the images folder and displays the prediction accuracy.

For this notebook, the test images are present in the folder
```bash
 ~/Mask_RCNN/images/
```

To run the demo version of the model, open the foloowing file in jupyter notebook:
```bash
~/Mask_RCNN/samples/demo_stone_detection.ipynb
```

----

**Tests Results**:

1. When running on similar images as during training:
<img src = "Validation result/Dataset_Images/download.png">
<img src = "Validation result/Dataset_Images/download (2).png">
<img src = "Validation result/Dataset_Images/download (6).png">
<img src = "Validation result/Dataset_Images/download (13).png">
<img src = "Validation result/Dataset_Images/download (22).png">

2. When running on random images (from internet)
<img src = "Validation result/Random_Images/download (25).png">
<img src = "Validation result/Random_Images/download.png">
<img src = "Validation result/Random_Images/download (5).png">
<img src = "Validation result/Random_Images/download (4).png">


----------