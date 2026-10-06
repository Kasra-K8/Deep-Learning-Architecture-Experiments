# Deep Learning Architecture Experiments

## CNNs from Scratch, Residual & Inception Networks, Transfer Learning, and Denoising Autoencoders

# Deep Learning Architecture Experiments

## CNNs from Scratch, Residual & Inception Networks, Transfer Learning, and Denoising Autoencoders

This repository contains a collection of experimental projects completed as part of a graduate-level **Deep Learning** assignment during my M.Sc. studies in Biomedical Engineering at K. N. Toosi University of Technology.

The assignment explored several fundamental and advanced deep-learning concepts through four practical computer-vision experiments:

1. **CNN implementation from scratch using NumPy/CuPy and comparison with PyTorch**
2. **Baseline, Residual, and Inception-Residual CNN architecture comparison**
3. **Transfer learning using progressive backbone fine-tuning**
4. **Deep Convolutional Denoising Autoencoder with downstream classification**

Rather than focusing on a single network, the project investigates how implementation strategy, architecture design, hyperparameters, transfer learning, and representation learning affect model performance.

---

## Project Overview

| Task | Experiment | Dataset(s) |
|---|---|---|
| Task 2 | CNN from Scratch vs PyTorch + Hyperparameter Sensitivity | Fashion-MNIST, CIFAR-10, Flower17 |
| Task 3 | Baseline vs Residual vs Inception-Residual CNNs | Linnaeus 5 |
| Task 4 | Transfer Learning and Progressive Fine-Tuning | flower_photos |
| Task 5 | Deep Convolutional Denoising Autoencoder | Fashion-MNIST |

---

## Task 2 — CNN from Scratch vs PyTorch

A complete CNN training pipeline was implemented in two different ways:

- manually using **NumPy and CuPy**
- using **PyTorch and automatic differentiation**

The from-scratch implementation includes convolution, backpropagation, Batch Normalization, Max Pooling, fully connected layers, ReLU, Dropout, Softmax/Cross-Entropy, Adam optimization, and He initialization.

The same general architecture and experimental settings were used to allow comparison between the two implementations.

### Selected Results

| Dataset | NumPy/CuPy Accuracy | PyTorch Accuracy |
|---|---:|---:|
| Fashion-MNIST | 92.46% | 92.82% |
| CIFAR-10 | 74.78% | 75.94% |
| Flower17 | 63.00% | 59.34% |

A separate CIFAR-10 sensitivity analysis investigated the effects of learning rate, batch size, activation function, optimizer, regularization, dropout, and weight initialization.

---

## Task 3 — Residual and Inception-Residual CNNs

Three convolutional architectures were implemented and compared on the Linnaeus 5 dataset:

- Baseline CNN
- Residual CNN
- Inception-Residual CNN

Additional experiments examined the effect of network depth and width.

### Selected Results

| Architecture | Test Accuracy | Macro F1 |
|---|---:|---:|
| Baseline CNN | 79.35% | 79.41% |
| Residual CNN | **80.00%** | **79.98%** |
| Inception-Residual CNN | 79.50% | 79.41% |

---

## Task 4 — Transfer Learning

The Inception-Residual model trained in Task 3 was reused as a pretrained feature extractor for a five-class flower-classification task.

The experiment consisted of two stages:

1. **Frozen-backbone training**
2. **Progressive fine-tuning**, gradually unfreezing deeper portions of the backbone

### Results

| Training Strategy | Test Accuracy | Macro F1 |
|---|---:|---:|
| Frozen Backbone | 72.21% | 71.74% |
| Progressive Fine-Tuning | **75.89%** | **75.10%** |

Progressive fine-tuning improved test accuracy by approximately **3.68 percentage points**.

---

## Task 5 — Deep Convolutional Denoising Autoencoder

A Deep Convolutional Denoising Autoencoder was trained on Fashion-MNIST images corrupted with Gaussian noise.

The architecture consists of:

- Convolutional encoder
- Latent representation
- Transposed-convolution decoder
- MLP classifier

Following autoencoder pretraining, two classification strategies were compared:

- Frozen encoder
- End-to-end fine-tuning

### Results

| Strategy | Test Accuracy | Macro F1 |
|---|---:|---:|
| Frozen Encoder | **86.44%** | **86.30%** |
| Full Fine-Tuning | 85.81% | 85.78% |

Despite achieving substantially higher training accuracy, full fine-tuning did not improve test performance, indicating increased overfitting.

---

## Repository Structure

```text
.
├── notebooks/
│   ├── Task2_CNN_From_Scratch_vs_PyTorch.ipynb
│   ├── Task3_Residual_Inception_CNN_Comparison.ipynb
│   ├── Task4_Transfer_Learning_Flowers.ipynb
│   └── Task5_Denoising_Autoencoder_Classification.ipynb
│
├── report/
│   └── Deep_Learning_HW3_Report_FA.pdf
│
├── results/
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Technologies

- Python
- PyTorch
- Torchvision
- NumPy
- CuPy
- Scikit-learn
- Pandas
- Matplotlib
- CNNs
- Residual Networks
- Inception Networks
- Transfer Learning
- Autoencoders
- GPU Computing
- Hyperparameter Analysis

---

## Academic Context

**Course:** Deep Learning  
**Project Type:** Graduate Course Assignment  
**Program:** M.Sc. Biomedical Engineering  
**University:** K. N. Toosi University of Technology  
**Author:** Kasra Attar Kashani

The complete Persian-language assignment report is available in the `report/` directory.

---

## Notes

Datasets and trained model checkpoints are not included in this repository.

Task 4 uses the Inception-Residual model trained in Task 3 as its pretrained backbone. Therefore, Task 3 should be executed first when reproducing the full experimental pipeline.
