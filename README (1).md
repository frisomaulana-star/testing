<div align="center">

# 🦠 Mpox Skin Lesion Classification

### Kelompok 6 — Deep Learning for Skin Lesion Classification

<p>
  <img src="https://img.shields.io/badge/Python-3.x-blue?logo=python" />
  <img src="https://img.shields.io/badge/Framework-PyTorch-red?logo=pytorch" />
  <img src="https://img.shields.io/badge/Deep%20Learning-CNN-orange" />
  <img src="https://img.shields.io/badge/Task-Image%20Classification-purple" />
</p>

**A deep learning project to classify skin lesion images into six categories using CNN-based models.**

</div>

---

## 📌 Overview

This project explores the use of deep learning for classifying skin lesion images related to Mpox. The repository provides a training pipeline, model configurations, and utilities for loading image data and conducting model experiments.

The models are trained and evaluated using a **5-fold cross-validation** approach to examine model performance across different data splits.

> **Disclaimer:** This project is developed for educational and research purposes. It is not a medical diagnostic tool and must not be used as a substitute for professional medical evaluation.

---

## 🎯 Objectives

- Build image classification models for skin lesion images.
- Train and compare multiple CNN-based architectures/configurations.
- Evaluate training behavior using loss and accuracy.
- Use 5-fold cross-validation to assess model performance across folds.
- Review model performance and classification errors to identify areas for improvement.

---

## 🧠 Models

The repository currently contains three model configurations in `config.py`.

| Model ID | Architecture | Input Image Size | Batch Size | Epochs | Learning Rate | Early Stopping |
|---|---|---:|---:|---:|---:|---|
| `model1` | SimpleCNN | 100 × 100 | 32 | 100 | 0.001 | No |
| `model2` | SimpleCNNReg | 100 × 100 | 16 | 20 | 0.0001 | Patience 5 |
| `efficientnetb0` | EfficientNet-B0 (pretrained) | 224 × 224 | 16 | 20 | 0.0001 | Patience 5 |

All configurations are set to produce **6 output classes**.

---

## ⚙️ Methodology

The general workflow of the project:

1. **Data loading** — image data and labels are loaded through the utilities in `Utils/`.
2. **Preprocessing** — images are prepared according to the input size specified for each model.
3. **Training** — model parameters are optimized using Adam and the NLL loss function.
4. **Validation** — validation loss and accuracy are calculated during training.
5. **Checkpointing** — the model checkpoint with the lowest validation loss is saved.
6. **Cross-validation** — training is performed across the selected folds (default: 5).
7. **Visualization & logging** — training/validation loss curves and per-epoch history are saved.

---

## 📊 Results

Training outputs are saved under `Results/<model_name>/`.

Examples of generated files:

- `training_fold1.png` — training and validation loss curve for Fold 1.
- `history_fold1.csv` — per-epoch training loss, validation loss, and validation accuracy.
- Similar files are generated for other folds.

### Training Curves

Add your generated plots below after running the training process. The image paths must point to files committed to this repository.

```md
![Model 1 Fold 1 Training Curve](Results/model1/training_fold1.png)
```

### Performance Summary

Fill this table using the actual evaluation output. Do not enter estimated or unverified scores.

| Model | Fold | Best Epoch | Best Validation Loss | Validation Accuracy | Test Accuracy |
|---|---:|---:|---:|---:|
| SimpleCNN (`model1`) | — | — | — | — | — |
| SimpleCNNReg (`model2`) | — | — | — | — | — |
| EfficientNet-B0 | — | — | — | — | — |

> Metrics can be added once the evaluation results are available.

---

## 🔍 Error Analysis

Error analysis can be used to identify:

- Which class is most frequently misclassified.
- Which pairs of classes are often confused.
- Whether the model performs consistently across categories.
- Possible effects of image quality, visual similarity, or class imbalance.

If a confusion matrix is available, add it here:

```md
![Confusion Matrix](Results/confusion_matrix.png)
```

Update the image path to match the actual file location.

---

## 🗂️ Repository Structure

```text
tugas-kelompok-6-mpox/
│
├── Models/
│   ├── CNN.py
│   ├── CNN2.py
│   └── efficientnet_b0.py
│
├── Results/
│   └── <model_name>/
│       ├── training_fold1.png
│       └── history_fold1.csv
│
├── Utils/
│   └── Dataset and image-loading utilities
│
├── config.py
├── train.py
├── test.py
├── requirements.txt
└── README.md
```

*The tree above is a simplified overview. Actual dataset and output files may vary depending on your setup.*

---

## 🛠️ Installation

### 1. Clone this repository

```bash
git clone https://github.com/auliyasalwahayati-web/tugas-kelompok-6-mpox.git
cd tugas-kelompok-6-mpox
```

### 2. Create a virtual environment (optional)

```bash
python -m venv .venv
```

Activate it:

**Windows**
```bash
.venv\Scripts\activate
```

**macOS / Linux**
```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🚀 Training

The training script accepts a model name from the configurations in `config.py`.

### Train Model 1

```bash
python train.py --model model1
```

### Train Model 2

```bash
python train.py --model model2
```

### Train EfficientNet-B0

```bash
python train.py --model efficientnetb0
```

By default, training runs through 5 folds and uses the epoch count specified in `config.py`.

### Run a small test

For a quick check using only one fold and two epochs:

```bash
python train.py --model model1 --folds 1 --epochs 2
```

---

## 📁 Output Files

The training script creates output folders for checkpoints and results:

```text
Checkpoints/
└── <model_name>/
    └── <model_name>_fold<fold>.pt

Results/
└── <model_name>/
    ├── training_fold<fold>.png
    └── history_fold<fold>.csv
```

- **Checkpoints** contain saved model weights and training information.
- **PNG plots** show training and validation loss over epochs.
- **CSV history** records epoch-level training loss, validation loss, and validation accuracy.

---

## 🧰 Technologies

- Python
- PyTorch
- Torchvision (if used by the installed model implementation)
- NumPy
- Matplotlib
- DataLoader
- CNN / EfficientNet-B0

*Please refer to `requirements.txt` for the project's dependency list.*

---

## 👥 Team

**Group 6 — Mpox Skin Lesion Classification**

Add team member names and roles here:

| No. | Name | Role |
|---:|---|---|
| 1 | Member 1 | — |
| 2 | Member 2 | — |
| 3 | Member 3 | — |
| 4 | Member 4 | — |

---

## 📚 References

- Project repository: [tugas-kelompok-6-mpox](https://github.com/auliyasalwahayati-web/tugas-kelompok-6-mpox)
- PyTorch documentation: https://pytorch.org/docs/
- EfficientNet paper: *EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks*

---

<div align="center">

**Group 6 | Mpox Skin Lesion Classification**

*Created for academic and research purposes.*

</div>
