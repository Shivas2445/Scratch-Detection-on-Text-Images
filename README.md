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

## 🔧 Installation

```bash
pip install -r requirements.txt
```

## 📈 Model Performance

### **EfficientNet-B3 Classification Results**

| Metric          | Value  |
|-----------------|--------|
| Precision (Bad) | 1.0000 |
| Recall (Bad)    | 0.9976 |
| F1 Score (Bad)  | 0.9988 |
| Accuracy        | 97.68% |

### Additional Performance Visuals

- `results/confusion_matrix.png`
- `results/precision_recall_curve.png`

## 🧠 Hybrid Decision Logic

### Thresholds Used

USER_THRESHOLD = 0.005
CLASSIFIER_CONF_THRESHOLD = 0.50


### Decision Rules

- If classifier predicts **Bad** with high confidence → **BAD**
- Else if scratch mask area > threshold → **BAD**
- Otherwise → **GOOD**

### Advantages

- Ensures **high recall** (no bad images missed)
- Ensures **high precision** (minimal false positives)

---

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
