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
* 10 epochs on full training
* Cosine Annealing Warmup sheduler
* BiTem
