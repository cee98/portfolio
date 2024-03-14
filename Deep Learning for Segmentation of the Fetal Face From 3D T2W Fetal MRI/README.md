# Deep Learning for Segmentation of the Fetal Face From T2W Fetal MRI

## Problem description:
Assessing fetal craniomaxillofacial malformalities,affecting soft tissue and bone, through 3D Magnetic Resonance Imaging (MRI) provides anatomical details of such conditions that arise congenitally, due to good soft tissue contrast, and
the advantage of examining such features from multiple planes. Having detailed segmentations is essential for planning and implementing high-quality postnatal care since these abnormalities can greatly affect the newborn’s wellbeing. However, segmentations
are usually derived manually, posing challenges such as its time-consuming nature, and potential for interobserver variability. Therefore, using Deep Learning (DL) techniques provides
automated segmentations with an accurate degree, contributing to further comprehending anatomical characteristics of orofacial conditions. DL medical segmentation techniques have been widely applied to cardiology, neurology, and placental health
in fetal medicine, but still lacks research regarding craniofacial development. This study aims to implement and evaluate DL pipelines for the segmentation of the fetal face from 3D T2-weighted fetal MRI.

## Feature variables:
Fetal MRI Images: All of the maternal participants were scanned on the Philips Ingenia 1.5T system using a body coiland SSTSE acquisition (TE = 80ms, TR = 18000ms, flip angle,fa,=90°, acquisition resolution, a, = 1·25×1·25x2.5 mm, and
slice overlap, SO,=1·25 mm). 

## Target variables:
Segmentation of Ground Truth Labels: Manual segmentations were performed by a single operator using ITK snap (version 2.2.0) by implementing a semi-automated method based on image thresholding and manual editing. 82
fetal MRI SVR cases had ground truth manual segmentations performed and the mean GA was 28.56 weeks (range 20.71-37.86 weeks). 
1 - face segmentation pixel <br>
0 - background pixel

## Programming language:
Python 

## Libraries:
os, Shutil, Tempfile, Torch, Time, Matplotlib, NumPy, tqdm, Nibabel, SimpleITK, Monai: Medical Open Network for AI, Scikit-learn, Pandas, Plotlyexpress

## Algorithms:
- DiceCELoss: Dice coefficient combined with cross-entropy loss.
- GeneralizedDiceLoss: Generalized version of Dice loss.
- DiceMetric: Dice similarity coefficient metric.
- sliding_window_inference: Inference method for sliding window-based predictions.
- Various data augmentation and preprocessing transforms such as:
  - Adding channels.
  - Loading images.
  - Scaling intensity.
  - Converting to tensors.
  - Random Gaussian smoothing.
  - Random affine transformations.
  - Random Gibbs noise addition.
  - Discretization.

## Models built:
- AttentionUnet: Neural network architecture
- SegResNet: Neural network architecture
- 3D UNet: Neural network architecture
- VNet: Neural network architecture

## Methods of model evaluation
- Dice Coefficient: The Dice Coefficient is a measure of the
overlap between the predicted segmentation output of the model
and the ground truth, where the minimum value is 0 (no overlap)
and the maximum value is 1 (perfect overlap). These calculations
are based on the total number of pixels in the specific image that
is segmente.
- Hausdorff Distance: Hausdorff distance measures the
largest distance between a pair of points from the predicted segmentation
and ground truth by implementing Euclidean distance,
therefore the greatest error produced by the segmentation.
- Recall: Recall represents the proportion of correctly classified
pixels (True Positives Value).
- Precision: Precision is the proportion of true positives in
relation to all positives (True positives and False Positives).

## Summary of Results:
![image](https://github.com/cee98/portfolio/assets/112065175/90fa2f1d-ac55-4a2c-b3c9-8476ed6f24e7)

<img width="514" alt="Screenshot 2024-03-14 at 22 33 32" src="https://github.com/cee98/portfolio/assets/112065175/145afe17-fc54-405d-b2d6-4869a5a52220">

![image](https://github.com/cee98/portfolio/assets/112065175/50db9c23-14a3-4e24-9241-f09670759263)

![image](https://github.com/cee98/portfolio/assets/112065175/1b1ee67f-fb3d-49c5-a3a5-920c2001284a)


From these results:<br>

-The average dice scores across each model ranged from 0.8913 (UNet with no augmentations) to 0.9753 (Ensemble model).
- Additionally, the average Recall ranged from 0.9637 (UNet with no augmentations) to 0.9894 (UNet with augmentations).
- The precision ranged from 0.8356 (UNet with no augmentations)to 0.9780 (Attention UNet with augmentations).
- Though the models produced results within a small range, the UNet with augmentations model consistently gave rise to the lowest metric scores, indicating its poor performance.
- Both UNet models produced the largest variation of the evaluation metrics, including the dice score, precision and recall.
- When qualitatively evaluating the segmentation results from the test set, both the Attention UNet (with augmentations) and SegResNet (no augmentations) produced the highest number of segmentations rated as ”Better”, but had segmentations also rated
as ”Fail”, 2/10 and 4/10 times, respectively.
- Considering the lowest proportion of segmentations rated as ”Fail”, the model that achieved this was the ensemble model, where segmentations rated as ”Better” were 2/10, ”Same” were 8/10, and ”Fail” were 0/10.
- Moreover, the UNet model (no augmentations), performed the worst, qualitatively, with all segmentation outputs being rated as ”Fail”.
  - Followed by UNet (with augmentations) where ”Fail” was 9/10, and ”Same” was 1/10.
- Therefore, although the UNet (with augmentations) model gave rise to a higher average recall value out of all the models, visually, the segmentation did not improve when compared to the ground truth.
- Regarding selecting the best performing model, based on the quantitative and qualitative measures and for this particular task, the Attention UNet (with augmentations), and ensemble models fit this criterion.
- When assessing these models quantitatively, there is a low variation in the dice score within the MRI images that were segmented, which demonstrates robustness of these models .
- Therefore, it can be inferred that these models generalise well to unseen data, especially since the quality of the MRI images used in both training, validation, and testing varied greatly.
- 
## Limitations:
- There were a large number of features compared to the number of samples, so the classifiers were prone to overfitting.
- The dataset used was unbalanced so the smaller class (preterm) will be more difficult to predict correctly.



