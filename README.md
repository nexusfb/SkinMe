# Skin Cancer (Melanoma) Detection System

This repository contains the code and resources for the development of a **Skin Cancer (Melanoma) Detection System** using Convolutional Neural Networks (CNNs) and Long Short-Term Memory networks (LSTMs). 

This project was undertaken as part of the **Deep Learning course** at La Sapienza for the academic year 2022/2023.

## Overview

Skin cancer, particularly **melanoma**, is a significant health concern worldwide. Early detection is crucial for effective treatment, as the survival rate drops significantly if cancer is detected in later stages. This project aims to build a robust detection system utilizing advanced deep learning techniques to help with early diagnosis through a user-friendly application.

## Features

- **CNNs** for image feature extraction and classification.
- **LSTMs** for sequential data analysis to improve prediction accuracy.
- Leverages **state-of-the-art deep learning methodologies** for a comprehensive approach to skin cancer detection.
- Uses the **HAM10000** dataset, containing high-quality dermatoscopic images of skin lesions across seven cancer classes.

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Models](#models)
- [Results](#results)
- [Usage](#usage)
- [Contributors](#contributors)

## Introduction

The goal of the **SkinMe** project is to provide an early detection system for skin cancer through the use of deep learning models. Users can upload an image of their skin lesion, and the system will return a prediction on whether it is benign or malignant, along with its classification into one of seven skin cancer types.

While this tool is not intended to replace professional medical diagnosis, it can assist with preliminary screening, enabling users to seek further medical advice if needed.

## Dataset

We utilized the **HAM10000** ("Human Against Machine with 10000 training images") dataset, which is the state-of-the-art dataset in this domain. The dataset consists of **10,015 dermatoscopic images** with metadata including patient information such as age, gender, and lesion location.

The seven classes of skin cancer in the dataset are:
1. **Melanocytic nevi (nv)**
2. **Melanoma (mel)**
3. **Benign keratosis-like lesions (bkl)**
4. **Basal cell carcinoma (bcc)**
5. **Actinic keratoses (akiec)**
6. **Vascular lesions (vasc)**
7. **Dermatofibroma (df)**

The dataset is highly imbalanced, with **nv** being the most common class. Techniques such as **SMOTE** were used to balance the training data.

## Models

### Convolutional Neural Network (CNN)
- Implemented using the **Keras Sequential API**.
- The CNN includes multiple Conv2D layers followed by MaxPooling and Dropout layers for regularization.
- The architecture progressively increases filters from **32 to 256**, learning features at different abstraction levels.
- **Mish** activation function was used in Dense layers, while **Softmax** was used in the output layer for class probabilities.
- Trained using **Adam optimizer** and **categorical cross-entropy loss**.

### Long Short-Term Memory (LSTM)
- Sequential image data is reshaped to fit into a **3D array** for the LSTM model.
- LSTMs are used for capturing temporal dependencies within the image sequences.
- The model architecture includes **LSTM layers**, followed by Dropout and Dense layers with **Softmax** as the output.
- Trained using **100 epochs** and **batch size of 128**.

## Results

Both the CNN and LSTM models performed exceptionally well:

- **CNN**:
  - Total parameters: 504,103
  - Accuracy: 99.7%
  - Loss: 0.0024
- **LSTM**:
  - Total parameters: 71,623
  - Accuracy: 99.26%
  - Loss: 0.0240

The CNN achieved slightly better accuracy, but the LSTM was more efficient in terms of parameter usage, making it a more lightweight alternative.

### Performance Metrics:
- **Confusion Matrix**: Both models showed high accuracy across most classes, with room for improvement in classes such as **bkl** and **df**.
- **Accuracy and Loss Curves**: The models demonstrated steady improvement in both metrics over the epochs, with optimal performance achieved around **10 epochs** for the CNN and **15 epochs** for the LSTM.

## Usage

To use the system, follow the steps below:

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/SkinMe.git
   cd SkinMe
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
  
3. To train the models:
   ```bash
   python train.py --model cnn  # To train the CNN model
   python train.py --model lstm  # To train the LSTM model
   ```
  
4. To make predictions:
   ```bash
   python predict.py --image_path path_to_image
   ```

   This will return a diagnosis of the input image, classifying the skin lesion into one of the seven classes of skin cancer.

## Contributors
- Federica Bruni
- Alessio Borgi
- Maria Emilia Russo

This project was supervised by Professor Tony Huynh as part of the Deep Learning course at La Sapienza.
