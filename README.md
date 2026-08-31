# DTD Texture Classification using EfficientNetB3

A Computer Vision project for multi-class texture classification using the **Describable Textures Dataset (DTD)** and an **EfficientNetB3-based transfer learning pipeline**.

## Project Overview

Texture is an important visual characteristic in computer vision. In this project, the task is to classify texture images into one of the predefined texture categories provided by the Describable Textures Dataset (DTD).

The project follows an end-to-end computer vision workflow:

Dataset
→ Exploratory Data Analysis
→ Data Validation
→ Image Preprocessing
→ Label Encoding
→ Data Augmentation
→ EfficientNetB3 Transfer Learning
→ Model Training
→ Evaluation

## Dataset

### Describable Textures Dataset (DTD)

The Describable Textures Dataset is a collection of texture images "in the wild", organized into **47 human-perception-inspired texture categories**.

The dataset contains:

- 5,640 images
- 47 texture categories
- 120 images per category
- Images ranging from 300×300 to 640×640 pixels
- Predefined training, validation and test splits
- 40 images per class in each split

The project uses the dataset's provided split files rather than creating a new random train/validation/test split.

### Dataset Source

Describable Textures Dataset — Visual Geometry Group, University of Oxford

[[OFFICIAL DTD DATASET PAGE]](https://www.robots.ox.ac.uk/~vgg/data/dtd/index.html)

### Dataset Citation

Cimpoi, M., Maji, S., Kokkinos, I., Mohamed, S., & Vedaldi, A. (2014).

**Describing Textures in the Wild.**

Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR).

## Project Workflow

### 1. Dataset Configuration

The project uses:

- Image size: 300 × 300
- Batch size: 32
- Random seed: 42
- Number of classes: 47
- DTD split: Split 1

The dataset is loaded using the provided:

- `train1.txt`
- `val1.txt`
- `test1.txt`

Each split file is used to obtain the corresponding image paths and texture labels.

### 2. Data Organization

The image paths and labels are organized into separate Pandas DataFrames for:

- Training
- Validation
- Testing

A combined DataFrame is also created for overall dataset inspection.

### 3. Exploratory Data Analysis

The current notebook performs the following dataset checks:

- Dataset size and class count
- Class distribution
- Missing image path verification
- Corrupt image verification
- Visual inspection of representative images
- One sample image from each texture category

These steps are performed to understand the dataset and verify its quality before model development.

### 4. Image Preprocessing

Images are prepared for the EfficientNetB3 model using the following pipeline:

1. Read image
2. Convert BGR to RGB
3. Resize to 300 × 300
4. Convert to `float32`
5. Apply EfficientNet-compatible preprocessing

The preprocessing is designed specifically for the selected EfficientNetB3 architecture.

### 5. Label Encoding

The 47 texture class names are converted into numerical class labels using `LabelEncoder`.

The encoder is fitted using the training classes and then used to transform the training, validation and test labels.

### 6. Data Augmentation

Training data augmentation is defined using:

- Random horizontal flipping
- Random rotation
- Random zoom
- Random contrast

Augmentation is intended to be applied only to training data, while validation and test data remain unchanged.

### 7. Model Development

The project uses **EfficientNetB3** as the selected convolutional neural network architecture.

The model is intended to use **transfer learning**, leveraging pretrained visual features for the 47-class texture classification task.

> Model architecture, training configuration and evaluation results will be documented here after model development and training are completed.

## Technologies Used

- Python
- TensorFlow / Keras
- EfficientNetB3
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- Google Colab

## Project Structure

```text
DTD-Texture-Classification-EfficientNetB3/
│
├── DTD_Texture_Classification.ipynb
├── README.md
├── requirements.txt
└── ...
