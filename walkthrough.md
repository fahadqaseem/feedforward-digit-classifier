# ✅ Assignment 2: Walkthrough — Completed

## What Was Built

A complete **feedforward neural network** for handwritten digit classification, trained and evaluated on MNIST.

---

## Files Delivered

| File | Purpose |
|---|---|
| [`digit_classifier.ipynb`](file:///Users/fahad/Downloads/To%20keep/2026/09%20Sep/AR_VR/assignment_2/feedforward-digit-classifier/digit_classifier.ipynb) | Full notebook: model, training, evaluation (10 sections with mentor explanations) |
| [`README.md`](file:///Users/fahad/Downloads/To%20keep/2026/09%20Sep/AR_VR/assignment_2/feedforward-digit-classifier/README.md) | **The professor's report** — covers all 4 required sections |
| [`best_model.pth`](file:///Users/fahad/Downloads/To%20keep/2026/09%20Sep/AR_VR/assignment_2/feedforward-digit-classifier/best_model.pth) | Saved model weights (best checkpoint at epoch 9) |
| [`requirements.txt`](file:///Users/fahad/Downloads/To%20keep/2026/09%20Sep/AR_VR/assignment_2/feedforward-digit-classifier/requirements.txt) | Python dependencies |
| `outputs/training_curves.png` | Loss & accuracy curves across 10 epochs |
| `outputs/confusion_matrix.png` | 10×10 heatmap of predictions vs. true labels |
| `outputs/sample_predictions.png` | 32 test images with predicted/true labels |
| `outputs/sample_mnist.png` | Sample training images |
| `outputs/class_distribution.png` | Dataset class balance chart |

---

## Results Achieved

| Metric | Value |
|---|---|
| **Best Test Accuracy** | **98.09%** |
| Best epoch | 9 of 10 |
| Final test loss | 0.0713 |
| Training time | 55.4 seconds |
| Device used | Apple MPS (Metal GPU) |

### Epoch Summary
| Epoch | Train Acc | Test Acc |
|---|---|---|
| 1 | 91.31% | 96.55% |
| 5 | 97.67% | 97.87% |
| **9** | **98.34%** | **98.09% ← best** |
| 10 | 98.40% | 98.07% |

---

## Professor Requirements — All Covered ✅

| Requirement | Where it appears in README.md |
|---|---|
| ✅ Network architecture (with diagram) | Section 1 |
| ✅ Source code | Section 2 |
| ✅ Training & testing information | Section 3 |
| ✅ Test results (accuracy + confusion matrix + plots) | Section 4 |

---

## How to Export README → PDF

You have a few options:

### Option A: VS Code (Recommended)
1. Open [`README.md`](file:///Users/fahad/Downloads/To%20keep/2026/09%20Sep/AR_VR/assignment_2/feedforward-digit-classifier/README.md) in VS Code
2. Install the **"Markdown PDF"** extension
3. Right-click in the editor → **"Markdown PDF: Export (pdf)"**

### Option B: Typora
Open the file in [Typora](https://typora.io) → File → Export → PDF

### Option C: GitHub
Push to a GitHub repo → view README there → print page as PDF (Cmd+P → Save as PDF)

> [!IMPORTANT]
> The images are referenced as **relative paths** (`outputs/training_curves.png`), so the `outputs/` folder must be in the same directory as `README.md` when converting to PDF.

