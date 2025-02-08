# Dental OPG Image Synthesis using GAN

This repository contains a complete pipeline for synthesizing dental OPG images using a Generative Adversarial Network (GAN). The project includes two major components:

1. **Data Preprocessing:**  
   Loads raw dental OPG images from a specified directory, resizes them to 256×256 pixels, normalizes them to the range [-1, 1], computes basic statistics, and saves the preprocessed images.

2. **GAN Training:**  
   Trains a DCGAN-inspired architecture (with a Generator and a Discriminator) on the preprocessed images. The network is designed to generate 256×256 synthetic images. The training loop includes label smoothing, loss logging, and periodic saving of generated samples and evaluation plots.

## Table of Contents

- [Overview](#overview)
- [Features](#features)

## Overview

The aim of this project is to generate realistic synthetic dental OPG images using GANs. The pipeline consists of:

- A preprocessing script (Cell 1) that:
  - Reads raw images from your Google Drive.
  - Resizes them to a fixed resolution of 256×256.
  - Normalizes the images (so pixel values lie in [-1, 1]).
  - Computes and prints useful metrics (number of images, average dimensions, per-channel mean, and standard deviation).
  - Saves the preprocessed images for further use.

- A GAN training script (Cell 2) that:
  - Loads the preprocessed images using `torchvision.datasets.ImageFolder`.
  - Defines a Generator and a Discriminator (both designed for 256×256 images).
  - Uses label smoothing and noise injection for robust adversarial training.
  - Logs and saves training losses and evaluation metrics.
  - Saves generated sample images at each epoch and produces plots of loss curves, evaluation metrics (dummy FID and Inception Score), and side-by-side comparisons of real vs. generated images.

## Features

- **Data Preprocessing:**  
  - Resizes images to 256×256 pixels.
  - Normalizes images to [-1, 1].
  - Computes statistics (e.g. average width, average height, per-channel mean and std).
  - Saves processed images for downstream use.

- **GAN Architecture:**  
  - **Generator256:** Upsamples a latent vector (nz = 50) through 7 stages to generate 256×256 images.
  - **Discriminator256:** Processes 256×256 images through several convolutional layers to output a single probability (using a Sigmoid activation).

- **Training Loop:**  
  - Implements adversarial training with label smoothing.
  - Logs generator and discriminator losses.
  - Saves generated image samples at each epoch.
  - Plots loss curves and evaluation metrics (FID and Inception Score placeholders).

