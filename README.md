Lung Nodule Detection Using Deep Learning
**Creator:** Sampath Magapu

## Overview
This project implements a deep learning pipeline for detecting lung nodules from DICOM medical images using convolutional neural networks (CNNs). The model classifies input scans as containing lung nodules or not, automating a critical step in computer-aided diagnosis for lung cancer screening.[1]

## Main Features
- DICOM image loading, preprocessing, and visualization.
- CSV metadata integration for image-label mapping.
- Binary classification model: Nodule vs. No Nodule.
- Train/Validation/Test splits with robust performance reporting.
- Prediction and inference for new images.
- Evaluation metrics: accuracy, precision, recall, F1-score, and confusion matrix visualizations.[1]

## Installation

### Requirements
- Python 3.11 or higher
- Jupyter Notebook
- pip packages: `numpy`, `pandas`, `pydicom`, `cv2`, `tensorflow`, `scikit-learn`, `matplotlib`, `seaborn`[1]

### Setup
```bash
pip install numpy pandas pydicom opencv-python tensorflow scikit-learn matplotlib seaborn
```
Place DICOM images and metadata CSV in the proper directory structure as referenced in the notebook (e.g., `SDP/images/`, `SDP/lidc_metadata.csv`).[1]

## Usage

### Data Preparation
- The notebook loads DICOM images from paths derived from metadata CSV entries.[1]
- Images are resized to $$224 \times 224 $$ pixels and normalized for CNN input.[1]
- Labels: 1 for nodule, 0 for no nodule (mapped from findings in metadata).[1]

### Model Architecture
- Sequential CNN:
  - Conv2D (32 filters, 3x3) → MaxPooling2D
  - Conv2D (64 filters, 3x3) → MaxPooling2D
  - Conv2D (128 filters, 3x3) → MaxPooling2D
  - Flatten → Dense (128 units, ReLU) → Dropout (0.5)
  - Output: Dense (1 unit, Sigmoid) for binary classification[1]
- Optimizer: Adam
- Loss: Binary Crossentropy[1]

### Training & Evaluation
- Training is done for 10+ epochs, with accuracy and loss tracked for train and validation splits.[1]
- Performance metrics and confusion matrices are generated on the test set and full dataset.[1]
- Model achieves high accuracy (typically >92%) on validation and test sets.[1]

### Prediction
- To predict a new scan, use the `predict_nodule(image_path)` function, which preprocesses the image and runs inference using the trained model.[1]
- Returns "Nodule Detected" or "No Nodule Detected".[1]

## Visualization
- Matplotlib is used for displaying DICOM images and model training curves.
- Seaborn is used for plotting confusion matrices.[1]

## File Structure
```
LungNoduleDetection.ipynb
SDP/
   ├── images/                 # DICOM image files (.dcm)
   └── lidc_metadata.csv       # CSV with image IDs and findings
```

## Citation
If you use this code in academic work, please cite:
```
@creator{Sampath Magapu,
  title = {Lung Nodule Detection Using Deep Learning},
  year = {2025}
}
```

## License
This project is released under MIT License.

***

For further details, see the implementation and cell comments inside the notebook.[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/101076500/440c5318-8bd2-474d-af79-2124a4be3b18/LungNoduleDetection.ipynb)
