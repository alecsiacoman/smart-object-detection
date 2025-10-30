# Smart Object Recognition: Classification of Coffee Mugs and Water Bottles

## Introduction

### Problem Definition
This project aims to build an **image classification system** capable of distinguishing between **coffee mugs** and **water bottles**. The model will be trained using a dataset of labeled images and deployed in a real-world scenario through a **mobile application** that captures photos and identifies the object category.

This task falls under **pattern recognition** and **computer vision**, with practical relevance in retail inventory management, smart kitchen assistants, waste sorting, and accessibility tools.

### Importance & Context
In everyday environments, being able to automatically recognize simple household items like mugs or bottles is a foundational step toward **intelligent vision systems**.  
Applications include:
- **Retail automation:** automatic product recognition at checkout.
- **Smart home devices:** identifying utensils or containers.
- **Assistive technology:** describing items to users via voice.
- **Mobile AR experiences:** recognizing physical items through a phone camera.

By developing a robust classification system for these two categories, we demonstrate how small-scale image classification models can form the basis for larger AI systems.

## Datasets

### 1. Water Bottle Image Classification Dataset  
- *Source:* [Kaggle – “Water Bottle Image Classification Dataset”](https://www.kaggle.com/datasets/chethuhn/water-bottle-dataset)  
- *Description:* A collection of images showing water bottles in various contexts (lighting, backgrounds, poses).  
- *Usage:* We will use this dataset to represent the “bottle” class in our classification and detection tasks.  
- *Preparation:* We’ll split into training and validation sets, possibly remove or label any irrelevant or mis-labeled images, and resize/normalize as required by our model.

### 2. Cup / Mug Dataset  
- *Source:* [Kaggle – “Cup_mug_dataset”](https://www.kaggle.com/datasets/malikusman1221/cup-mug-dataset/data)  
- *Description:* A dataset consisting of images of cups and mugs in different settings (differing shapes, colors, with/without handles, different backgrounds).  
- *Usage:* This dataset will represent the “mug” class. Because mugs and cups sometimes look different (handle/no handle, glass vs ceramic), we’ll inspect and possibly filter images to focus on mugs (or treat “cup” and “mug” interchangeably if appropriate).  
- *Preparation:* As above — clean the data, split into train/val, apply consistent preprocessing.

### Combined Dataset Strategy  
- For *classification*, we will merge both classes into a simple two-class dataset: mug vs bottle.  
- For *detection* - TBD (CoCo dataset)

## Libraries & Frameworks

Here are the primary libraries and tools we will use for the ML pipeline, from training through export and mobile integration:

### Training / Experimentation (in Jupyter notebooks)
- *PyTorch* – Core deep learning framework for model training and evaluation.
- *Ultralytics YOLOv8* – Used for both classification (task=classify) and, later, object detection (task=detect).
- *Torchvision* – Provides pre-trained models and utilities for loading image datasets.
- *Jupyter Notebook / JupyterLab* – Interactive environment for data exploration, training, and testing.

### Model Export & iOS Integration
- *Ultralytics export utility* – To convert trained PyTorch models into mobile-friendly formats.  
  Example:
  bash
  yolo mode=export model=best.pt format=coreml
  
- *Core ML* – Apple’s on-device machine learning framework; runs models efficiently on iPhone using the Neural Engine or GPU.
- *Core ML Tools (coremltools)* – Python package to convert models from PyTorch (via ONNX) into .mlmodel format for iOS deployment.
- *Vision Framework (iOS)* – Apple’s API for image analysis tasks; we’ll use it to run the Core ML model and obtain classification or detection results in the app.

### Mobile App Framework (Frontend)
- *Ionic Angular* – Cross-platform UI framework for building the mobile app using web technologies.
- *Capacitor* – Bridge between the Angular web layer and native iOS functionality (camera access, Core ML inference).
- *Camera Preview Plugin* – Enables live camera feed inside the Ionic app; used to capture frames.

### Supporting Tools
- *Git* – For version control and collaboration.
- *Python virtual environment (venv or conda)* – To manage dependencies cleanly across development environments.

