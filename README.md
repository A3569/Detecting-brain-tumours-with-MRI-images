# Brain Tumor Detection with Hybrid EfficientNet-DenseNet Model
Brain tumor detection from MRI scans is critical for early diagnosis. This project implements a deep learning model for brain tumor detection using MRI images. The hybrid EfficientNet-DenseNet model with Attention achieves 93.33% accuracy in tumor classification. The solution addresses key challenges like data imbalance and overfitting through techniques including data augmentation, class weighting, and dropout regularization.

## Proposed Method
### 1. Dataset Preparation: 
- Brain MRI images categorized as Positive (tumor) or Negative (no tumor)
### 2. Split Dataset: 
- 80% training, 20% testing
### 3. Preprocessing:
- Resize images to 224×224 pixels
- Normalize pixel values ​​to [0,1] range
### 4. Data Augmentation:
- Rotation (±15°)
- Width/height shifts (10%)
- Zoom variations (10%)
- Horizontal/vertical flips
- Brightness adjustments (±10%)
### 5. Backbone Networks:
- EfficientNetB0 (fine-tuned last 5 layers)
- DenseNet121 (frozen weights)
- Attention Mechanism: Adaptive feature weighting
- Classification Head:
- Global Average Pooling
- Fully connected layer (192 neurons, ReLU)
- 50% dropout regularization
- Optimization: Adam (α=0.001)
- Loss: Binary Cross-Entropy with label smoothing
### 6. Hyperparameter Tuning:
- Batch size: 32 (training), 15 (testing)
- Epochs: 50 (early stopping)
- Learning rate: 0.001
- Class Weighting: Compensates for 2:1 positive:negative imbalance

## Experimental results
- Accuracy 93.33%
- Tumor Recall 100%
- Tumor Precision 91%
- Non-tumor Precision 100% -
- AUC-ROC 0.99
- Confusion matrix showing 0 false negatives

## Performance Analysis
#### Strengths:
- 100% tumor detection rate (0 false negatives)
- Excellent AUC-ROC (0.99)
- Robust to class imbalance

#### Limitations:
- Mild overfitting (training loss: 0.13 vs validation loss: 0.25)
- Specificity of 80% (slightly below 85% target)

## Summary
- High diagnostic accuracy (93.33%) meeting clinical standards
- Perfect sensitivity (100% tumor detection)
- Effective handling of class imbalance through weighting
- Computational efficiency via transfer learning
