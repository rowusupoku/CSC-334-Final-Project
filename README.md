# CSC-334-Final-Project

# Copy-Move Forgery Detection: SIFT vs UNet

## Overview
    This project explores methods for detecting copy-move forgeries in biomedical images. Copy-move forgery occurs when a region of an image is duplicated elsewhere in the same image, often to falsify or enhance experimental results.

## The two approaches I'll be exploreing:

    -SIFT (Scale-Invariant Feature Transform) – a classical, feature-based method that detects keypoints and matches repeated regions within an image (Lowe, 2004).
    
    -UNet-based Deep Learning – a modern, pixel-level segmentation model that learns spatial patterns to identify manipulated regions (Ronneberger et al., 2015).

  The goal is to compare these approaches in terms of accuracy, and strengths/limitations for practical forgery detection.
  
##SIFT Approach

    -Preprocessing: Images converted to grayscale.
    -Keypoint Detection: SIFT identifies distinct local features.
    -Feature Matching: Matches similar keypoints across the image.
    -Filtering: RANSAC removes inconsistent matches to reduce false positives.
    -Region Clustering: DBSCAN groups matched points into duplicated regions.  
    -Mask Generation: Clusters are converted to binary masks for visualization.

##UNet Approach

    -Preprocessing: Images resized and normalized.
    -Model Architecture: UNet encoder-decoder with skip connections for pixel-level segmentation.
    -Training: Trained using annotated masks from the Kaggle dataset.   
    -Evaluation: Performance assessed using pixel-wise accuracy and IoU metrics. 
    -Inference: Generates predicted binary masks for test images.

## Key Findings & Challenges

    -SIFT is lightweight and interpretable but struggles with subtle manipulations and produces 0 feature matches if the parameters are too strict.
    -UNet handles complex patterns and subtle anomalies but requires significant computational resources and training time. 
    -Trade-offs: High-resolution images improve detection for both methods but increase runtime and memory usage.

## Next Steps
    -Apply SIFT and UNet to the full dataset for batch mask generation.
    -Explore parameter tuning (DBSCAN eps, UNet depth) to improve performance.
    -Benchmark detection accuracy, runtime, and reliability for large-scale images.

##References

    -Lowe, D. G. (2004). Distinctive Image Features from Scale-Invariant Keypoints. International Journal of Computer Vision.
    -Ronneberger, O., Fischer, P., & Brox, T. (2015). U-Net: Convolutional Networks for Biomedical Image Segmentation. MICCAI.
    -Recod.ai/LUC - Scientific Image Forgery Detection | Kaggle
