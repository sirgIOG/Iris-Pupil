# U-Net Segmentation for Iris Images

## Overview
This project implements a small variant of the U-Net architecture with an encoder-decoder structure and skip connections for iris segmentation. The model is trained using a custom Dice Loss function, which is well-suited for segmentation tasks. Training is facilitated with a robust pipeline that includes data augmentation, early stopping, and checkpointing.

## Dataset

### Original Dataset
- **Source:** [IrisPupille - Roboflow](https://universe.roboflow.com/iris-annotation/irispupille)

### Enhancements
- The original dataset did not include masks for images in the training set. Masks for the training set were generated using OpenCV.

### Dataset Composition
- **Training Set:** 400 images
- **Test Set:** 45 images

### Dataset Structure
The dataset should be organized as follows:
```
data/ 
| ├── images/ 
│ | ├── image1.png 
│ | ├── image2.png 
│ | └── ... 
| ├── masks/ 
| | ├── mask1.png 
| | ├── mask2.png 
| | └── ...
```

- **Images:** Grayscale iris images (pixel values normalized to [0, 255]).
- **Masks:** Corresponding binary masks where the iris region is highlighted.

## Model Architecture
The U-Net model is implemented in the `build_unet_small` class. Key components include:

- **Encoder:**
  - Convolutional blocks (`conv_block`) consisting of two convolution layers with Batch Normalization, ReLU activation, and dropout.
  - Max pooling layers for downsampling.
- **Bottleneck:**
  - A convolutional block to capture high-level features.
- **Decoder:**
  - Transpose convolution layers for upsampling.
  - Skip connections that concatenate encoder features to retain spatial context.
- **Output:**
  - A final convolution layer followed by a Sigmoid activation to generate the segmentation mask.

## Requirements
- Python 3.7+
- PyTorch
- torchvision
- OpenCV (cv2)
- scikit-learn
- NumPy
- Matplotlib
- tqdm

## Accuracy
- Accuracy of Iris to Pupil ratio is 96.33%



For further reference - [U-Net: Convolutional Networks for Biomedical
Image Segmentation](https://arxiv.org/pdf/1505.04597)
