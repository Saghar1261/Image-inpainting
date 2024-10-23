# Image Inpainting: GAN vs. Diffusion Models

## Overview

This project compares Generative Adversarial Networks (GAN) and Diffusion Models in the task of image inpainting, where missing portions of an image are reconstructed based on contextual information from the remaining parts. The project evaluates both approaches using Peak Signal-to-Noise Ratio (PSNR) and Structural Similarity Index (SSIM) to measure their effectiveness.

## Authors
- Ana Maria Jaramillo - [GitHub Profile](https://github.com/Anmjaramillo412)
- Saghar Ghaffari - [GitHub Profile](https://github.com/Saghar1261)
  
## Table of Contents

- Project Structure
- Dataset
- Models
- GAN
- Diffusion Model
- Preprocessing
- Training and Evaluation
- Results
- Conclusions
- Future Work
- Project Structure



## Dataset

The Places365 dataset was used in this project. It consists of 36,000 images of various scenes, each resized to 128x128 pixels for computational efficiency. For image inpainting, parts of the images were randomly masked to simulate damage.

More information about the dataset can be found here.

## Models

### 1. Generative Adversarial Networks (GAN)
The GAN architecture includes:

Generator: A fully connected neural network with 3 layers using the LeakyReLU activation and batch normalization.
Discriminator: A 2-layer network using the Sigmoid activation for real/fake classification.
The GAN was trained to generate realistic images from random noise and then restore damaged images. The optimizer used is Adam, and the loss function is Binary Cross-Entropy for discriminator and generator, and MSE for the repair task.

### 2. Diffusion Model
The Diffusion Model adds Gaussian noise to the damaged images and gradually removes the noise to restore the image. A probabilistic approach using TensorFlow Probability was implemented. The model was trained using the Adam optimizer and MSE as the loss function.

### Preprocessing

The dataset was preprocessed by resizing all images to 128x128 pixels and normalizing the pixel values. A custom function was used to randomly mask sections of each image to create the "damaged" dataset for training.

Training and Evaluation

The training process was performed using TensorFlow, with a focus on comparing the performance of the two models:

### GAN: The generator and discriminator were trained for 1000 epochs.
### Diffusion Model: Trained for 999 epochs due to higher computational costs.
Metrics used:

PSNR: Measures the quality of image restoration.
SSIM: Assesses the structural similarity between the original and restored images.
Results

Model	PSNR	SSIM
GAN	10.78	0.46
Diffusion	17.39	0.82
The results show that the Diffusion Model outperformed the GAN in both PSNR and SSIM, though at the cost of greater computational resources and longer training times.

## Conclusions

The Diffusion Model demonstrated superior performance in terms of image quality, producing more accurate and structurally similar inpainted images compared to the GAN. However, GANs are more efficient in terms of time and computational power, making them a good choice for projects with limited resources.

## Future Work

- Implementing a Residual Block Structure within the diffusion process to improve feature learning.
- Exploring advanced GAN architectures such as WGAN to improve image quality.
- Extending the project to other datasets and higher-resolution images.
