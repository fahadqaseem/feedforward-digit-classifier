# 🎓 Assignment 2: Feedforward Digit Classifier — Implementation Plan

## Goal

Build a **feedforward neural network** that classifies handwritten digits (MNIST dataset), then document everything in `README.md` so you can export it as a PDF report for the professor.

We'll do this **together**, step by step, so you understand every decision made.

---

## 📋 What the Professor Requires

The PDF report must contain:

| # | Requirement | Our Plan |
|---|---|---|
| 1 | **Network architecture diagram** | We'll produce a visual diagram of the network layers |
| 2 | **Source code** | Clean, well-commented Python script using PyTorch |
| 3 | **Training & testing info** | Hyperparameters, optimizer, loss function, epochs, dataset split |
| 4 | **Test results** | Final accuracy, loss curves, confusion matrix |

---

## ⚙️ Framework Decision: **PyTorch ✅** (not TensorFlow)

> [!IMPORTANT]
> **Why PyTorch?**
> - PyTorch 2.7.1 is **already installed** on your machine. TensorFlow is not.
> - PyTorch is the **dominant framework in academia and research** as of 2024–2026.
> - It has a more intuitive, "Pythonic" style that makes it easier to *learn* what's happening under the hood.
> - The professor's own reference example links to a PyTorch tutorial — so it aligns perfectly.
> - **No installation needed.** We can start coding immediately.

---

## 🧠 What You'll Learn Along the Way

As your mentor, I'll explain each concept as we build it:

1. **What MNIST is** — the "Hello World" of deep learning
2. **What a feedforward neural network is** — layers, neurons, weights, biases
3. **Activation functions** — why ReLU is used and what it does
4. **Loss functions** — CrossEntropyLoss and why it works for classification
5. **Backpropagation** — how the network learns from mistakes
6. **Optimizers** — Adam vs SGD and which to choose
7. **Overfitting** — what it is and how to detect it
8. **Evaluation** — accuracy, confusion matrix, what good results look like

---

## 🏗️ Proposed Network Architecture

```
Input Layer       Hidden Layer 1    Hidden Layer 2    Output Layer
  784 neurons  →    256 neurons   →   128 neurons   →   10 neurons
  (28×28 px)       + ReLU              + ReLU          (digits 0–9)
                   + Dropout(0.2)      + Dropout(0.2)  + Softmax (implicit)
```

**Why these sizes?**
- **784**: Each MNIST image is 28×28 pixels = 784 input features (flattened)
- **256 → 128**: Gradually compress the representation (common pattern)
- **10**: One output neuron per digit (0 through 9)
- **Dropout**: Prevents overfitting (a regularization technique you'll learn about)

---

## 📁 File Structure We'll Create

```
feedforward-digit-classifier/
├── homework_instructions.md     # (already exists)
├── README.md                    # Final report (we'll populate this)
├── model.py                     # Neural network definition
├── train.py                     # Training script
├── evaluate.py                  # Evaluation & result generation
├── requirements.txt             # Dependencies (for reproducibility)
└── outputs/
    ├── training_curves.png      # Loss & accuracy plots
    ├── confusion_matrix.png     # Visual breakdown of predictions
    └── sample_predictions.png  # Sample images with predicted labels
```

---

## 📐 Step-by-Step Implementation Plan

### Step 1 — Setup & Dependencies
Create `requirements.txt` listing PyTorch, torchvision, matplotlib, numpy.

### Step 2 — Define the Model (`model.py`)
```python
import torch.nn as nn

class DigitClassifier(nn.Module):
    def __init__(self):
        super().__init__()
        self.network = nn.Sequential(
            nn.Flatten(),               # 28x28 → 784
            nn.Linear(784, 256),        # Hidden Layer 1
            nn.ReLU(),
            nn.Dropout(0.2),
            nn.Linear(256, 128),        # Hidden Layer 2
            nn.ReLU(),
            nn.Dropout(0.2),
            nn.Linear(128, 10)          # Output: 10 classes (digits 0-9)
        )
    
    def forward(self, x):
        return self.network(x)
```

### Step 3 — Training Script (`train.py`)
- Load MNIST dataset via `torchvision.datasets` (auto-downloads ~11 MB)
- Dataset split: **60,000 train / 10,000 test** (standard MNIST split)
- Optimizer: **Adam** (lr=0.001) — better than SGD for beginners
- Loss: **CrossEntropyLoss**
- Epochs: **10** (fast but effective for MNIST)
- Batch size: **64**
- Save best model weights → `best_model.pth`
- Track loss & accuracy per epoch → printed to console

### Step 4 — Evaluation Script (`evaluate.py`)
- Load the saved model
- Run on test set → print final accuracy
- Generate and save:
  - 📈 Training loss & accuracy curves (per epoch)
  - 🔢 Confusion matrix (10×10 heatmap)
  - 🖼️ Sample predictions (grid of images with true vs. predicted labels)

### Step 5 — Populate `README.md`
The README will be structured exactly for PDF export:
- Network architecture section with diagram
- All hyperparameters in a table
- Full source code (embedded or linked)
- Embedded result images
- Discussion of results with analysis

---

## 🎯 Expected Results

For MNIST with this architecture:
- **Test accuracy: ~98%+** (this is a well-studied benchmark)
- Training time: **< 2 minutes** on CPU

---

## ✅ Verification Plan

### Automated Tests
```bash
python3 train.py        # Trains model, prints epoch-by-epoch accuracy
python3 evaluate.py     # Prints ~98% accuracy, saves 3 plots to outputs/
```

### Manual Verification
- Check that all plots are saved in `outputs/`
- Review `README.md` to ensure it covers all 4 professor requirements
- Verify the network diagram is clear enough for the PDF report

---

## ❓ Open Questions — Please Answer Before We Start!

> [!IMPORTANT]
> **I need your input on these before I write any code:**

1. **Your current experience level?**
   - Complete beginner (never coded before)
   - Know Python basics, new to ML
   - Familiar with ML concepts, new to PyTorch

2. **File format preference?**
   - `.py` scripts (clean, professional, runs from terminal)
   - Jupyter Notebook `.ipynb` (run cell-by-cell, see outputs inline — great for learning)

3. **Mentor style preference?**
   - Write code with **detailed inline comments explaining every concept** as we go
   - Write **clean code first**, then I'll answer your questions afterward

4. **Any grading rubric or scoring criteria** the professor shared beyond the 4 requirements listed?
