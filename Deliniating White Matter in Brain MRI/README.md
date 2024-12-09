
# Deliniating White Matter in Brain MRI
- The aim of this project is to apply registration and segmentation techniques to delieate white matter in a brain MRI image.
<img width="622" alt="Screenshot 2024-04-25 at 12 46 12" src="https://github.com/cee98/portfolio/assets/112065175/d46e5566-32d9-497b-8865-9a0c321b4687">
<img width="649" alt="Screenshot 2024-04-25 at 12 48 00" src="https://github.com/cee98/portfolio/assets/112065175/a0f81277-fbc0-433a-81ef-a1fc50b01bc1">

## Problem Description:
- The project involves segmenting white matter (WM) from brain MRI images using a combination of affine registration, Gaussian Mixture Models (GMM), and Expectation Maximization (EM) with probabilistic atlases. The goal is to accurately separate brain tissues (WM, GM, and CSF) by preprocessing the MRI data, registering it to a template, and performing tissue segmentation with an evaluation of the segmentation quality.

## Feature Variables:
- MRI image intensities for brain tissue (white matter, gray matter, cerebrospinal fluid).
- Mask data for brain tissue extraction.
- Probability maps for tissue classification (WM, GM, CSF).

## Target Variables:
- White Matter (WM) Segmentation: The target variable is a segmentation of the white matter in the brain, as indicated by a binary mask.
  
## Programming Languages:
- Python: Used for implementing all algorithms and processing steps.

## Libraries:
- SimpleITK: For loading, processing, and displaying 3D MRI images.
- NumPy: For numerical operations, particularly with image arrays.
- Matplotlib: For plotting 3D images.
- Scikit-learn: For Gaussian Mixture Models (GMM).
- itk: For advanced image registration and transformation operations.
- Custom libraries for displaying, segmenting, and evaluating image data.
  
## Algorithms:
- Affine Registration: Used to align the image and the atlas.
- Gaussian Mixture Model (GMM): Applied for segmenting the white matter from the brain MRI.
- Expectation Maximization (EM): Used for probabilistic segmentation based on a probabilistic atlas (WM, GM, CSF).
- Template Propagation: Propagating the labels based on a predefined template.
  
## Models Built:
- Affine Registration: Registers the template image and its mask to the input image.
- GMM Segmentation: Uses GMM to segment the brain tissue (3-class segmentation: WM, GM, and CSF).
- EM Segmentation: Refines the segmentation using probabilistic atlases with EM to update tissue classification iteratively.
  
## Qualitative Method of Model Evaluation:
- Visual Inspection: Displaying the segmented white matter overlaid on the original MRI images. This allows for a manual check of whether the segmentation is accurate, especially in complex regions like the brain's center.
- Overlaying Images: Checking the alignment of the segmented image with the original and the probabilistic atlas using 3D visualization.

## Quantitative Methods of Model Evaluation:
- Dice Coefficient: Measures the overlap between the predicted segmentation and the ground truth segmentation of the white matter. A higher Dice coefficient indicates a better segmentation.
  - Example: Dice = 0.84 (for GMM) and Dice = 0.85 (for EM)
- Hausdorff Distance: Measures the maximum distance between the surface of the segmented white matter and the ground truth. A smaller Hausdorff distance indicates better accuracy in capturing the boundaries of the white matter.
  - Example: Hausdorff Distance = 15.17 (GMM) and 15.13 (EM)
- Average Hausdorff Distance: Measures the average of the maximum distances between the predicted and ground truth surfaces. This metric helps identify misclassified voxels further from the surface.
  - Example: Average Hausdorff Distance = 0.21mm (GMM) and 0.19mm (EM)

## Summary of Results:
- GMM Segmentation: Achieved a Dice coefficient of 0.84 for white matter segmentation with good average accuracy (Hausdorff distance of 15.17 and average Hausdorff distance of 0.21). However, some over-segmentation occurred due to misalignment or model instability (Dice coefficient variance).
- EM Segmentation: Improved results with a Dice coefficient of 0.85, Hausdorff distance of 15.13, and average Hausdorff distance of 0.19, showing better accuracy in surface representation.
  
## From These Results:
- GMM segmentation showed good initial results but had variability in Dice coefficient due to random initialization. The EM refinement provided more stable and improved segmentation results, demonstrating the advantage of probabilistic atlases in refining segmentation boundaries.
## Limitations:
- Over-segmentation or misalignment in the white matter region could occur due to inaccuracies in affine registration or initialization of model parameters.
- The results are sensitive to random initialization and affine registration quality.
- The computational complexity of the algorithms may increase with larger datasets or higher resolution images, requiring more iterations for accurate convergence.
