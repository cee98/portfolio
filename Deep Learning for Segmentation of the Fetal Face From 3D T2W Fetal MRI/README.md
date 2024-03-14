# Deep Learning for Segmentation of the Fetal Face From T2W Fetal MRI

## Problem description:
- Assessing fetal craniomaxillofacial malformalities,affecting soft tissue and bone, through 3D Magnetic Resonance Imaging (MRI) provides anatomical details of such conditions that arise congenitally, due to good soft tissue contrast, and the advantage of examining such features from multiple planes.
- Having detailed segmentations is essential for planning and implementing high-quality postnatal care since these abnormalities can greatly affect the newborn’s wellbeing. However, segmentations
are usually derived manually, posing challenges such as its time-consuming nature, and potential for interobserver variability.
- Therefore, using Deep Learning (DL) techniques provides automated segmentations with an accurate degree, contributing to further comprehending anatomical characteristics of orofacial conditions. DL medical segmentation techniques have been widely applied to cardiology, neurology, and placental health in fetal medicine, but still lacks research regarding craniofacial development.
- This study aims to implement and evaluate DL pipelines for the segmentation of the fetal face from 3D T2-weighted fetal MRI.

## Feature variables:
Fetal MRI Images: All of the maternal participants were scanned on the Philips Ingenia 1.5T system using a body coiland SSTSE acquisition (TE = 80ms, TR = 18000ms, flip angle,fa,=90°, acquisition resolution, a, = 1·25×1·25x2.5 mm, and
slice overlap, SO,=1·25 mm). 

## Target variables:
Segmentation of Ground Truth Labels: Manual segmentations were performed by a single operator using ITK snap (version 2.2.0) by implementing a semi-automated method based on image thresholding and manual editing. 82
fetal MRI SVR cases had ground truth manual segmentations performed and the mean GA was 28.56 weeks (range 20.71-37.86 weeks).<br> 
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

## Models Built:
- AttentionUnet: Neural network architecture
- SegResNet: Neural network architecture
- 3D UNet: Neural network architecture
- VNet: Neural network architecture

## Quantitative Methods of Model Evaluation
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

## Qualitative Method of Model Evaluation
The qualitative visual assessment was conducted using ITKSNAP to assess the quality of the segmentation output (3D model) in comparison to the ground truth.<br>
The model segmentations were rated as:
1. Better - meaning that the output is better in quality compared to the ground truth, by producing a smoother surface, and more detailed and defined facial features (such as the eyes,ears, nose, and orofacial region).
2. Same - both the ground truth segmentation and model output are of the same quality
3. Fail - Major segmentation errors (of one-third or more) occurred in the model segmentation and are of worse quality compared to the ground truth due to obscuring facial features and head.
<img width="1000" alt="Screenshot 2024-03-14 at 22 33 32" src="https://github.com/cee98/portfolio/assets/112065175/145afe17-fc54-405d-b2d6-4869a5a52220">

## Summary of Results:

<img width="1000" alt="Screenshot 2024-03-14 at 22 33 32" src="https://github.com/cee98/portfolio/assets/112065175/459a029f-9d81-4c91-844b-7188c23d2ecb">
<img width="1000" alt="Screenshot 2024-03-14 at 22 33 32" src="https://github.com/cee98/portfolio/assets/112065175/9201741f-0bfa-4168-bbad-196ead05c00b">
<img width="1000" alt="Screenshot 2024-03-14 at 22 33 32" src="https://github.com/cee98/portfolio/assets/112065175/93b611aa-f869-477d-a1fc-3bbaa2875763">
<img width="1000" alt="Screenshot 2024-03-14 at 22 33 32" src="https://github.com/cee98/portfolio/assets/112065175/4d1a6c33-9674-499a-adc8-97c76d2c8e52">

## From these results:<br>

- The average dice scores across each model ranged from 0.8913 (UNet with no augmentations) to 0.9753 (Ensemble model).
- Additionally, the average Recall ranged from 0.9637 (UNet with no augmentations) to 0.9894 (UNet with augmentations).
- The precision ranged from 0.8356 (UNet with no augmentations)to 0.9780 (Attention UNet with augmentations).
- Though the models produced results within a small range, the UNet with augmentations model consistently gave rise to the lowest metric scores, indicating its poor performance.
- Both UNet models produced the largest variation of the evaluation metrics, including the dice score, precision and recall.
- When qualitatively evaluating the segmentation results from the test set, both the Attention UNet (with augmentations) and SegResNet (no augmentations) produced the highest number of segmentations rated as ”Better”, but had segmentations also rated as ”Fail”, 2/10 and 4/10 times, respectively.
- Considering the lowest proportion of segmentations rated as ”Fail”, the model that achieved this was the ensemble model, where segmentations rated as ”Better” were 2/10, ”Same” were 8/10, and ”Fail” were 0/10.
- Moreover, the UNet model (no augmentations), performed the worst, qualitatively, with all segmentation outputs being rated as ”Fail”.
  - Followed by UNet (with augmentations) where ”Fail” was 9/10, and ”Same” was 1/10.
- Therefore, although the UNet (with augmentations) model gave rise to a higher average recall value out of all the models, visually, the segmentation did not improve when compared to the ground truth.
- Regarding selecting the best performing model, based on the quantitative and qualitative measures and for this particular task, the Attention UNet (with augmentations), and ensemble models fit this criterion.
- When assessing these models quantitatively, there is a low variation in the dice score within the MRI images that were segmented, which demonstrates robustness of these models .
- Therefore, it can be inferred that these models generalise well to unseen data, especially since the quality of the MRI images used in both training, validation, and testing varied greatly.

## Limitations:
- Since the fetal face is a large structure, the dice score alone does not fully demonstrate whether the model is appropriate for this task.
- Therefore, conducting qualitative assessments is vital to visualise whether, in this case, the facial characteristics are more detailed, and whether the output is smoother when compared to the ground truth.
- The quality of the MRI images varied, therefore images that were poorer in quality resulted in worse segmentations by the model; that is, they were qualitatively worse when compared to the ground truth.
  - This aspect may also indicate which models are more robust to such variation in image quality, since noise, motion artefacts, and bias fields are a common occurrence when acquiring MRI images, especially in fetal applications.
- The number of training images available (82) may have limited the potential and capacity for the model to learn, and although augmentation solves this issue to an
extent, having a large training set enables the model to learn natural variations in not just image quality, but anatomy. Also, Generative
  - Adversarial Networks (GANs) could be implemented to provide a larger training set.


