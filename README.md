# Final_Project_IANNWTF_Image_Colorization

##### Final Project of the course IANNWTF to colourize black and white images with a cGAN
[Link Colab](https://colab.research.google.com/drive/1d8h10E2cVMBiXZkAXDpFHEhPEprC_ERl?usp=sharing) <br />
[Link to Overleaf](https://sharelatex.gwdg.de/2932948648dmqptrcrvgpq) <br />
[Link to grading sheet](https://docs.google.com/spreadsheets/d/18C2XG1RoJYEbmnlO8zWXbXh_Tmm3O4V7jRp-9IP-l7M/edit?usp=sharing) <br />
[Link to requirenments](https://studip.uni-osnabrueck.de/sendfile.php?type=0&file_id=9d06087b66248e3c02957105cd037e4e&file_name=The_Path_towards_a_final_Project.pdf) <br />

1. Introduction
2. Requirements

## 1. Introduction
In this Project we implemented a convolutional generative adversial network to generate colorful images from greyscaled images. For this purpose we took the paper from Isola at al as a starting point for our model. With different techniques we tried to improve the generative performance of the model. You can find more informatmation in our[paper](Image Colorization - Methods and Applications).

The model can be trained on differnt datasets. It can also be used to generate a colorful image from a black and white image with the a model that is already trained with the coco2017 dataset. However, due to rescource constrains we cannot provide a sufficient trained model and the performance meassured with subjective observation of the results is not so good. 

## 2. Structure
Prerequisites
before you start, check if you have all poackages listed in requirenments.txt

if not, you can run:

    $ pip install -r requirements.txt

then you should clone the repository and open the folder in your terminal.
Alternatively you can use the notebook in colab.

### Get data
to load a dataset there are several differnt ways.


#### To Colab via URL
You candirectly load a dataset via URL to colab by the following code which is already includet in the our colab notebook.

***
```
# here you can insert yout path to the dataset or use  one of the cocodatasets
!wget http://images.cocodataset.org/zips/val2017.zip # 778MB, 5000 images
!wget http://images.cocodataset.org/zips/train2017.zip # 18G, 118287 images

import zipfile
import os

import zipfile
with zipfile.ZipFile('val2017.zip','r') as zip:     #ZipFile constructor; READ mode; ZipFile object named as zip, closes file automatically
    zip.extractall('/tmp')                          #Extract contents of the ZIP to tmp
    
path = '/tmp/val2017/'
data_rgb = []
IMG_SIZE = 256
#count = 0

for img in os.listdir(path):
  #...

```

#### To Colab via kaggle
Steps to-do:
1. Create or acces your kaggle account
2. go to your account
3. create new API Token and save it on your local machine (you have to do this every few days)
![grafik](https://user-images.githubusercontent.com/80921777/158060854-c4c96927-3a43-4472-b199-50cec56b29f8.png)
5. upload it to google drive with the following code snippet

***
```
from google.colab import drive
drive.mount('/content/drive')

!cp '/content/drive/MyDrive/YOUR_FOLDER/kaggle.json' '/content'

import zipfile
import os

os.environ['KAGGLE_CONFIG_DIR'] = "/content"

#!kaggle competitions download -c imagenet-object-localization-challenge # ImageNet

!kaggle datasets download -d awsaf49/coco-2017-dataset # coco2017
```
***
