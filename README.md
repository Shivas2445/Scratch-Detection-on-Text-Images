# Scratch Detection on Text Images  
### Deep Learning-Based Quality Inspection System

---

## 📌 Project Overview

This repository implements a complete deep-learning pipeline for detecting scratches on printed text images.  
The system consists of three components:

---

## ✅ 1. Image Classification (EfficientNet-B3)

Classifies an image as:

- **Good** — No scratches  
- **Bad** — Contains scratches  

---

## ✅ 2. Scratch Segmentation (U-Net++)

For images classified (or suspected) as *bad*, a U-Net++ model generates a segmentation mask to locate scratches.

---

## ✅ 3. Hybrid Decision Logic

The final decision is made by combining:

- Classifier prediction confidence  
- Scratch mask area from segmentation  

This ensures an accurate and robust quality-inspection flow.

---

### Thresholds Used

- **USER_THRESHOLD = 0.005**
- **CLASSIFIER_CONF_THRESHOLD = 0.50**

### Decision Rules

- If classifier predicts **BAD** and scratch area > threshold → **BAD**
- If classifier predicts **BAD** but confidence < confidence threshold → **BAD**
- If classifier predicts **BAD** with high confidence but scratch area < threshold → **GOOD**
- If classifier predicts **GOOD** but scratch area > threshold → **BAD**
- Otherwise → **GOOD**

## 🔍 Threshold Optimization (Grid Search)

A grid search was conducted to find the most effective thresholds for the hybrid decision pipeline.  
The search evaluated hundreds of combinations of:

- **Scratch Area Threshold (USER_THRESHOLD)**
- **Classifier Confidence Threshold (CONF_THRESHOLD)**

Each threshold pair was assessed across the full test set using precision, recall, F1-score, and accuracy.

---

### ✅ Final Selected Thresholds (Best Performing)

From the grid search, the optimal thresholds were found to be:
- **USER_THRESHOLD =0.004484**
- **CLASSIFIER_CONF_THRESHOLD =0.551579**



## 📈 Model Performance

### **Hybrid Model Results**

| Metric          | Value  |
|-----------------|--------|
| Precision (Bad) | 0.9027|
| Recall (Bad)    | 1.0000 |
| F1 Score (Bad)  | 0.9499 |
| Accuracy        | 97.87% |

### Additional Performance Visuals

- `results/confusion_matrix.png`
- `results/precision_recall_curve.png`


### Advantages

- Ensures **high recall** (no bad images missed)
- Ensures **high precision** (minimal false positives)

---


## 🔧 Installation

```bash
pip install -r requirements.txt
```
## To clone this repo
```bash
git clone https://github.com/Shivas2445/Scratch-Detection-on-Text-Images.git
```

## 📁 Dataset Disclaimer

The dataset used for this task is private .

---

## 🧾 Notes for Reviewer

This repository includes:

- ✔ Complete training, evaluation, and inference scripts  
- ✔ Pretrained model weights  
- ✔ Well-structured README and installation instructions  
- ✔ Visual results and plots  
- ✔ End-to-end hybrid quality-inspection pipeline  

---

## 🔗 View Full Work

You can view the complete implementation here:

👉 **Kaggle Notebook:**  
https://www.kaggle.com/code/shivashankar2445/scratch-detection-on-text-images

---

## 📬 Contact

For queries or clarifications:

📧 Email: **shivas2445@gmail.com**
