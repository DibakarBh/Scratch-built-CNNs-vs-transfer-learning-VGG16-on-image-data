# CNN Image Classification: Scratch Built vs. Transfer Learning

This project benchmarks Convolutional Neural Network (CNN) strategies for binary classification. It investigates how dataset size affects a model's ability to generalize when training from scratch versus leveraging pretrained features from a VGG16 backbone.

## Project Structure
The experiment follows a four-step protocol testing different Train/Val/Test splits:

1. **Custom CNN (Scratch)**: Multi-layer convolutional architecture with aggressive dropout and augmentation.
2. **Transfer Learning (VGG16)**: 
    - **Phase 1**: Feature extraction with frozen base weights.
    - **Phase 2**: Fine-tuning top layers to adapt to specific "Cats vs. Dogs" features.

## Experimental Results
| Strategy | Training Samples | Test Accuracy |
| :--- | :--- | :--- |
| **Scratch** | 1,000 | 75.8% |
| **Scratch** | 2,000 | 84.0% |
| **Pretrained + Fine-Tuning** | 1,000 | 96.6% |
| **Pretrained + Fine-Tuning** | 2,000 | 98.3% |

## Key Findings
- **Transfer Learning Dominance**: Pretrained models achieved ~96.6% accuracy with only 1,000 images, outperforming the scratch model by over 20%.
- **Data Scaling**: Increasing training data from 1,000 to 2,000 for scratch models yielded a significant jump in performance (0.758 to 0.840).
- **Fine-Tuning Efficacy**: Unfreezing top VGG16 layers allowed the model to reach near-perfect accuracy (98.3%) on the "ideal" dataset split.

## Tech Stack
- **Framework**: TensorFlow / Keras
- **Backbone**: VGG16 (ImageNet weights)
- **Techniques**: Data Augmentation, Dropout, Model Checkpointing, Fine-Tuning
