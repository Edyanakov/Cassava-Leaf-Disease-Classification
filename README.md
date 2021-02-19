# Cassava-Leaf-Disease-Classification

Here i will briefly describe my solution which i used for Cassava Leaf Disease Classification competition.</br>

All data(images) - https://www.kaggle.com/c/cassava-leaf-disease-classification/data. </br>
cassava-inference.ipynb - python notebook that i used for training.</br>
cassava-train.ipynb - python notebook that i used for inference.</br>
All training was done using kaggle enviroment and Colab.

## Data
* Only 2020 images
* Stratified 5-fold CV
* Removed duplicates from training folds based DBSCAN on image embeddings

## Augmentations
- RandomResizedCrop
- HorizontalFlip, VerticalFlip, Transpose
- HueSaturationValue
- RandomBrightnessContrast
- CoarseDropout

Image size: 512 px </br>
No heavy augmentations like mixup, etc

## Training
* 12 epochs on full training
* Cosine Annealing Warmup sheduler
* BiTemperedLoss with label smoothing, t1 = 0.8, t2 = 1.4, smoothing = 0.1
* timm package to download pretrained models

## Architectures
Used several architectures for ensemble:
* tf_efficientnet_b4_ns
* tf_efficientnet_b5_ns
* vit_base_patch32_384
* resnext50_32x4d
* seresnext50_32x4d
* regnety_080
* ecaresnet50d

SeResNext and EfficientNet performed best, but transformer ended up being very important to improve the ensemble.
