# Cassava-Leaf-Disease-Classification

Here i will briefly describe my solution which i used for Cassava Leaf Disease Classification competition.</br>
All data(images) - https://www.kaggle.com/c/cassava-leaf-disease-classification/data

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

Image size: 512 px
No heavy augmentations like mixup, etc
