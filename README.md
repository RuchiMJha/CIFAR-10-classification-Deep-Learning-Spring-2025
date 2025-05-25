# CIFAR-10 Image Classification with ResNet Architecture

This repository contains the implementation of a customized Residual Network (ResNet) for image classification on the CIFAR-10 dataset, developed as part of the Deep Learning Project for Spring 2025.

## Project Overview

The primary goal of this project was to design and train a modified ResNet model under the constraint of having fewer than 5 million trainable parameters. The model was developed from scratch using PyTorch and trained on CIFAR-10 to achieve a strong test accuracy while preserving efficiency and model clarity.

Final test accuracy: **93.41%**  
Total trainable parameters: **4,697,162**

## Model Architecture

The architecture consists of:
- **Initial Layer**: 3×3 convolution with 64 output channels
- **Layer 1**: 4 residual blocks with 64 channels (stride=1)
- **Layer 2**: 4 residual blocks with 128 channels (stride=2)
- **Layer 3**: 3 residual blocks with 256 channels (stride=2)
- **Output Layer**: Adaptive average pooling followed by a fully connected layer

Each residual block includes:
- Two 3×3 convolutional layers
- Batch normalization and ReLU activation
- Skip connections to improve gradient flow

## Methodology

Key techniques and strategies used:
- **Data Augmentation**: Random cropping, normalization, color jittering, rotation
- **Optimization**: SGD with momentum (0.9), CrossEntropyLoss, weight decay
- **Learning Rate Scheduling**: MultiStepLR with milestones at [30, 40, 60, 80]
- **Epochs**: Trained for 75 epochs
- **Batch Size**: 256
- **Weight Decay**: 1e-4

Hyperparameters were iteratively tuned to improve convergence and generalization.

## Training Progress

- Rapid accuracy gains observed in the first 30 epochs
- Validation accuracy plateaued after epoch 30
- Final training accuracy: ~99%
- Final test accuracy: ~93.41%

## Observations

- **Skip connections** significantly improved training stability and mitigated vanishing gradient issues.
- **Batch normalization** enabled the use of higher learning rates and accelerated convergence.
- **Model depth and width** were carefully balanced to remain under the 5M parameter constraint while maintaining representational capacity.

## Future Work

Potential areas for enhancement include:
- Exploring SE-ResNet or ResNeXt variants
- Integrating advanced regularization (e.g., Cutout, MixUp)
- Ensemble modeling
- Knowledge distillation to reduce model size without losing accuracy

## Repository Contents

- `final-code.ipynb`: Complete training and evaluation notebook with model architecture, plots, and accuracy reporting
- CIFAR-10 dataset loading and preprocessing
- Model checkpointing and parameter count validation

## Team Members

- Neha Patil  
- Ruchi Jha  
- Satvik Upadhyay 

## License

This repository is intended for educational purposes as part of NYU's Deep Learning course. All code is original unless explicitly cited.
