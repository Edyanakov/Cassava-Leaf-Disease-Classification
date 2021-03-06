# Cassava-Leaf-Disease-Classification

Here i will briefly describe my solution which i used for Cassava Leaf Disease Classification competition.</br>

All data(images) - https://www.kaggle.com/c/cassava-leaf-disease-classification/data. </br>
cassava-inference.ipynb - python notebook that i used for inference.</br>
cassava-train.ipynb - python notebook that i used for training.</br>
All training was done using kaggle enviroment and Colab.

## Data
* Only 2020 images
* Stratified 5-fold CV
* Removed duplicates from training folds based on DBSCAN on image embeddings

## Augmentations
- RandomResizedCrop
- HorizontalFlip, VerticalFlip, Transpose
- HueSaturationValue
- RandomBrightnessContrast
- CoarseDropout

Image size: 512 px </br>

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

## Ensembling
As for final submission ensemble of 8 models was used which got me a silver model on private leaderboard.

## What didnt work for me
* Using data from 2019 competition
* MixUp, CutMix augmentations
* Relabeling noisy images based on OOF predictions
* Removing noisy images based on OOF predictions
* Removing least performing folds while inference
* TTA for all models besides EfNet4 and ViT
