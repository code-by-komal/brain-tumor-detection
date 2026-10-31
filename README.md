 # 🧠 Brain Tumor Detection using Deep Learning

A deep learning-based brain tumor classification project that uses **ResNet50 and Transfer Learning** to classify brain MRI images into four categories. The project also incorporates **Grad-CAM (Gradient-weighted Class Activation Mapping)** to visualize the regions of an MRI image that influence the model's predictions.

## 📌 Project Overview

Brain tumor detection through MRI scans is an important application of medical image analysis. This project explores how deep learning and computer vision can be used to classify brain MRI images.

A pre-trained ResNet50 model is used as the feature extraction backbone, followed by custom fully connected layers for multi-class classification. The model is initially trained with frozen pre-trained layers and subsequently fine-tuned to improve classification performance.

Grad-CAM is implemented to provide visual explanations of model predictions.

## ✨ Features

- **Multi-class Classification:** Classifies MRI images into four categories.
- **Transfer Learning:** Uses pre-trained ResNet50 weights from ImageNet.
- **Fine-tuning:** Unfreezes selected ResNet50 layers for additional training.
- **Image Augmentation:** Applies rotation, shifting, zooming, and horizontal flipping.
- **Model Evaluation:** Evaluates performance using accuracy, loss, and a confusion matrix.
- **Explainable AI:** Uses Grad-CAM to visualize important image regions influencing predictions.
- **Training Visualization:** Plots training and validation accuracy and loss.

## 🔬 Classification Categories

The model is trained to identify the following four categories:

| Category | Description |
|---|---|
| Glioma | Glioma tumor |
| Meningioma | Meningioma tumor |
| No Tumor | No tumor detected |
| Pituitary | Pituitary tumor |

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Programming language |
| TensorFlow & Keras | Deep learning and model development |
| ResNet50 | Pre-trained CNN architecture |
| OpenCV | Image processing |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Scikit-learn | Model evaluation |
| Google Colab | Development and GPU-based training |

## 🏗️ Model Architecture

The project uses **ResNet50**, a pre-trained Convolutional Neural Network (CNN), as its backbone.

The classification architecture consists of:

1. ResNet50 (pre-trained on ImageNet).
2. Global Average Pooling layer.
3. Dense layer with 512 neurons and ReLU activation.
4. Dropout layer (0.5).
5. Dense layer with 256 neurons and ReLU activation.
6. Dropout layer (0.3).
7. Output layer with 4 neurons and Softmax activation.

### Training Strategy

**Phase 1 – Transfer Learning**
- Load pre-trained ResNet50 weights.
- Freeze the base model layers.
- Train the custom classification layers.
- Initial learning rate: 0.0001.
- Train for 25 epochs.

**Phase 2 – Fine-tuning**
- Unfreeze the last 80 layers of ResNet50.
- Recompile the model with a lower learning rate of 0.000001.
- Continue training for up to 150 epochs.

## 📂 Dataset & Preprocessing

The dataset consists of 3,176 brain MRI images distributed across four classification categories.

The dataset is divided into:

| Dataset | Images | Split |
|---|---:|---:|
| Training | 2,535 | 80% |
| Validation | 641 | 20% |
| **Total** | **3,176** | **100%** |

### Image Processing

- Images are resized to 256 × 256 pixels.
- Pixel values are normalized using rescaling.
- Training images undergo data augmentation:
  - Rotation
  - Width and height shifting
  - Zooming
  - Horizontal flipping

### Expected Dataset Structure

```text
BrainTumorDatasets/
│
├── dataset/
│   ├── train/
│   │   ├── glioma/
│   │   ├── meningioma/
│   │   ├── no tumor/
│   │   └── pituitary/
│   │
│   └── val/
│       ├── glioma/
│       ├── meningioma/
│       ├── no tumor/
│       └── pituitary/
```

**Note:** The dataset is not included in this repository. You need to configure the dataset directory before running the notebook.

## 📊 Model Performance

The model was evaluated using the validation dataset.

| Metric | Initial Training | After Fine-tuning |
|---|---:|---:|
| Accuracy | 70.05% | 80.03% |

### Evaluation Techniques

- Training and validation accuracy curves.
- Training and validation loss curves.
- Confusion matrix.
- Class distribution visualization.
- Grad-CAM heatmap visualization.

## 🔍 Explainable AI – Grad-CAM

Grad-CAM is used to understand which regions of an MRI image contribute to the model's classification.

Instead of only displaying the predicted class, Grad-CAM generates a heatmap highlighting the image regions that have a stronger influence on the prediction.

This helps make the model's predictions more interpretable.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/ek-kudi/brain-tumor-detection.git

cd brain-tumor-detection
```

### 2. Install dependencies

```bash
pip install tensorflow opencv-python numpy matplotlib scikit-learn split-folders
```

### 3. Configure the dataset

Download and organize the MRI dataset into the directory structure described above.

Update the dataset paths in the notebook according to your local environment.

### 4. Run the notebook

Open `Brain_Tumor_Detector_GC.ipynb` using Google Colab or Jupyter Notebook.

For the original Google Colab workflow, configure Google Drive access and enable GPU acceleration.

Execute the notebook cells to prepare the dataset, train the model, evaluate performance, and generate Grad-CAM visualizations.

## 🔮 Future Improvements

- Experiment with other architectures such as EfficientNet and DenseNet.
- Improve classification performance through hyperparameter tuning.
- Add precision, recall, F1-score, and class-wise evaluation.
- Implement a web interface for uploading MRI images and viewing predictions.
- Save and deploy the trained model through a prediction API.
- Improve model interpretability and evaluate its generalization on independent datasets.

## ⚠️ Disclaimer

This project is developed for educational and research purposes only. It is not intended to provide medical diagnoses or replace professional medical evaluation. Model predictions should not be used for clinical decision-making.

## 👩‍💻 Author

**Komal Yadav**

- GitHub: [code-by-komal](https://github.com/code-by-komal)
- Project Repository: [Brain Tumor Detection](https://github.com/code-by-komal/brain-tumor-detection)

---

⭐ If you find this project interesting, feel free to explore the repository!
