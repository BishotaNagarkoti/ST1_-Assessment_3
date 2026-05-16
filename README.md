# ST1_Assessment_3

# Macroinvertebrate Image Analysis System

## Group
Software Technology 1- 4483 ( Assignment 3  )
Group 7, Wednesday 09:30-11:30  
Members:  (u3309753),  (u3313565),  (u3306446)

## Project Goal
A modular Python application that indexes macroinvertebrate images,
performs EDA (exploratory data analysis), trains a baseline Random Forest
classifier, and predicts species from input images.

## Main Features
- dataset indexing
- class distribution analysis
- image size analysis
- baseline image classification
- image prediction with confidence score

## Python Packages Used
- pandas - image index as DataFrame
- numpy - numerical array operations
- opencv-python - image reading and resizing
- matplotlib - EDA charts and confusion matrix
- seaborn - styled charts and heatmap
- scikit-learn - model training and evaluation
- joblib - model saving and loading
- pathlib - file path handling

## Important Note About the Dataset
The raw image dataset is not included in this submission due to file 
size constraints. Please download it from Kaggle:

    https://www.kaggle.com/datasets/mistag/arthropod-taxonomy-orders-object-detection-dataset

After downloading, place the images inside data/raw/ so the folder 
structure looks like this:

    data/
    └── raw/
        ├── Gammarus sp/
        │   ├── image1.jpg
        │   └── image2.jpg
        ├── Asellus sp/
        │   └── image1.jpg
        └── ... (one folder per species)

## Installation

### Step 1 — Create a virtual environment

    python3 -m venv .venv

### Step 2 — Activate the virtual environment
On Mac/Linux:

    source .venv/bin/activate
On Windows:

    .venv\Scripts\activate

### Step 3 — Install dependencies

    pip3 install -r requirements.txt

## How to Run
### Run the full pipeline

    python3 -m src.main

This will automatically:
- Index all images from data/raw/
- Generate EDA charts saved to outputs/eda/
- Train the Random Forest classifier
- Save the model to outputs/models/
- Ask for an image path to predict

### Sample Prediction
- After training the model is saved to outputs/models/macro_classifier.joblib
- User is prompted to enter a full image path
- Model loads from disk and predicts the species
- Confidence score is displayed alongside the predicted species
- Example: Predicted Asellus sp with 64.50% confidence

## Folder Structure

    Software_Technology_1_Assessment_3/
    ├── data/
    │   └── raw/                 ← Kaggle dataset images
    ├── outputs/
    │   ├── eda/                 ← EDA charts
    │   └── models/              ← trained model and evaluation
    ├── screenshots/             ← manual testing evidence
    ├── src/
    │   ├── models/
    │   │   └── records.py
    │   ├── services/
    │   │   ├── classifier_service.py
    │   │   ├── dataset_indexer.py
    │   │   ├── eda_service.py
    │   │   ├── image_preprocessor.py
    │   │   └── workflow_service.py
    │   ├── config.py
    │   └── main.py
    ├── Implementation_Summary_ST1.pdf
    ├── MANUAL_TESTING.md
    ├── README.md
    └── requirements.txt

## Dataset
Macroinvertebrate image dataset from Kaggle.
Place images inside data/raw/ with one subfolder per species.
The folder name becomes the species label automatically.

## Model Results
- Overall accuracy: 70.36%
- Total images: 2,665 across 17 species
- Best performing class: Sphaerium sp (precision 0.95)
- Model: Random Forest with 200 estimators
