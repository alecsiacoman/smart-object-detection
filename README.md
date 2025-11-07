# Smart Object Recognition: Detection of Cups

## Introduction

### Problem Definition
This project aims to build an **object detection system** capable of identifying cups. The model will be trained using a dataset of labeled images and deployed in a real-world scenario through a **mobile application** that captures photos and identifies the object.

This task falls under **pattern recognition** and **computer vision**, with practical relevance in retail inventory management, smart kitchen assistants, waste sorting, and accessibility tools.

### Importance & Context
In everyday environments, being able to automatically recognize simple household items like mugs or bottles is a foundational step toward **intelligent vision systems**.  
Applications include:
- **Retail automation:** automatic product recognition at checkout.
- **Smart home devices:** identifying utensils or containers.
- **Assistive technology:** describing items to users via voice.
- **Mobile AR experiences:** recognizing physical items through a phone camera.
- 

## Datasets

We use a **subset of the COCO dataset (Common Objects in Context)** — one of the most comprehensive and widely used datasets for object detection.

COCO provides over 118,000 training images and 5,000 validation images, each with **bounding box annotations** for 80 object categories.  
We will extract only the relevant category for our task:
- **cup** (category ID: 47)

This subset gives us a large, diverse, and realistic dataset that already contains high-quality annotations of cups in complex, real-world environments (e.g., kitchens, desks, restaurants).
Available at [https://cocodataset.org](https://cocodataset.org)

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

