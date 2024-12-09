- The aim of this project is to apply registration and segmentation techniques to delieate white matter in a brain MRI image.
<img width="622" alt="Screenshot 2024-04-25 at 12 46 12" src="https://github.com/cee98/portfolio/assets/112065175/d46e5566-32d9-497b-8865-9a0c321b4687">
<img width="649" alt="Screenshot 2024-04-25 at 12 48 00" src="https://github.com/cee98/portfolio/assets/112065175/a0f81277-fbc0-433a-81ef-a1fc50b01bc1">

##Problem Description:
- The project involves segmenting white matter (WM) from brain MRI images using a combination of affine registration, Gaussian Mixture Models (GMM), and Expectation Maximization (EM) with probabilistic atlases. The goal is to accurately separate brain tissues (WM, GM, and CSF) by preprocessing the MRI data, registering it to a template, and performing tissue segmentation with an evaluation of the segmentation quality.

Feature Variables:
MRI image intensities for brain tissue (white matter, gray matter, cerebrospinal fluid).
Mask data for brain tissue extraction.
Probability maps for tissue classification (WM, GM, CSF).
Target Variables:
White matter segmentation.
Dice coefficient, Hausdorff distance, and average Hausdorff distance as evaluation metrics.
Programming Languages:
Python
Libraries:
SimpleITK for image processing and registration.
Numpy for array manipulation and data handling.
Scikit-learn for Gaussian Mixture Model (GMM) implementation.
Matplotlib for visualization.
Custom libraries for displaying, segmenting, and evaluating image data.
Algorithms:
Affine Registration for image alignment.
Gaussian Mixture Model (GMM) for initial segmentation of white matter (WM).
Expectation Maximization (EM) for refined tissue classification using probabilistic atlases.
Models Built:
Affine Registration: Registers the template image and its mask to the input image.
GMM Segmentation: Uses GMM to segment the brain tissue (3-class segmentation: WM, GM, and CSF).
EM Segmentation: Refines the segmentation using probabilistic atlases with EM to update tissue classification iteratively.
Qualitative Method of Model Evaluation:
Visual inspection of segmented images, especially the white matter areas.
Displayed 3D visualizations of the original and segmented images for qualitative comparison.
Summary of Results:
GMM Segmentation: Achieved a Dice coefficient of 0.84 for white matter segmentation with good average accuracy (Hausdorff distance of 15.17mm and average Hausdorff distance of 0.21mm). However, some over-segmentation occurred due to misalignment or model instability (Dice coefficient variance).
EM Segmentation: Improved results with a Dice coefficient of 0.85, Hausdorff distance of 15.13mm, and average Hausdorff distance of 0.19mm, showing better accuracy in surface representation.
From These Results:
GMM segmentation showed good initial results but had variability in Dice coefficient due to random initialization. The EM refinement provided more stable and improved segmentation results, demonstrating the advantage of probabilistic atlases in refining segmentation boundaries.
Limitations:
Over-segmentation or misalignment in the white matter region could occur due to inaccuracies in affine registration or initialization of model parameters.
The results are sensitive to random initialization and affine registration quality.
The computational complexity of the algorithms may increase with larger datasets or higher resolution images, requiring more iterations for accurate convergence.
