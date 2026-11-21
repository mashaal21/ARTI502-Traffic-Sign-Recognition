# Traffic Sign Classification on GTSRB: Custom CNN vs. YOLOv8n-cls

ARTI 502 Deep Learning, final project.
Department of Computer Science, College of Computer Science and Information Technology, Imam Abdulrahman Bin Faisal University.

This project compares two deep learning models for classifying traffic sign images into the 43 classes of the German Traffic Sign Recognition Benchmark (GTSRB):

1. **Custom CNN**, trained from scratch on 32 × 32 images.
2. **YOLOv8n-cls**, the classification variant of YOLOv8 nano, pretrained on ImageNet and fine-tuned on 128 × 128 images.

Both models use the same data split and are evaluated on the same official GTSRB test set (12,630 images).

## Team

| # | Member | Role |
|---|---|---|
| 1 | Jana Algahtani | Research and literature review |
| 2 | Nora Alqahtani | Dataset and preprocessing |
| 3 | Tayma Aldobas | Model 1: Custom CNN |
| 4 | Arwa Alqahtani | Model 2: YOLOv8n-cls |
| 5 | Joud Alshehri | Optimization and experiments |
| 6 | Mashaal Abdullah | Evaluation and final integration |

## Notebooks

Run them in this order. Each one is a Google Colab notebook.

| Notebook | Description |
|---|---|
| `notebooks/01_data_preparation.ipynb` | Loads GTSRB, analyzes the data, and creates the track-based 80/20 train/validation split (seed 42). |
| `notebooks/02_custom_cnn.ipynb` | Builds and trains the Custom CNN. |
| `notebooks/03_yolov8n_cls.ipynb` | Fine-tunes YOLOv8n-cls on the same split. |
| `notebooks/04_optimization.ipynb` | Hyperparameter experiments for both models. |
| `notebooks/05_evaluation.ipynb` | Evaluates both models on the test set: metrics table, confusion matrices, ROC curves, and per-class F1. |

## Dataset

[GTSRB – German Traffic Sign Recognition Benchmark](https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign) (Kaggle).

| Partition | Images |
|---|---|
| Training | 31,350 |
| Validation | 7,859 |
| Official test | 12,630 |

All images of the same physical sign (track) are kept in the same partition, so no sign appears in both training and validation.

## Results on the test set

| Model | Accuracy | Precision (macro) | Recall (macro) | F1 (macro) | ROC-AUC | Parameters |
|---|---|---|---|---|---|---|
| Custom CNN (initial) | 0.9360 | 0.9102 | 0.9083 | 0.9033 | 0.9970 | 361,067 |
| Custom CNN (optimized) | 0.9488 | 0.9337 | 0.9243 | 0.9235 | 0.9993 | 361,067 |
| YOLOv8n-cls (initial) | 0.9891 | 0.9882 | 0.9830 | 0.9844 | 0.9999 | 1,493,371 |
| YOLOv8n-cls (optimized) | 0.9859 | 0.9842 | 0.9763 | 0.9793 | 0.99995 | 1,493,371 |

## How to run

1. Open a notebook in Google Colab.
2. The notebooks read the shared project folder from Google Drive (`/content/drive/MyDrive/ARTI502_Project`) and download GTSRB with `kagglehub`.
3. Run the cells in order. The data split files must exist before the model notebooks are run.

Trained model weights and the dataset are not stored in this repository because of their size.
