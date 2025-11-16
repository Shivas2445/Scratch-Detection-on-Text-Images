Scratch-Detection-on-Text-Images

Deep Learning-Based Quality Inspection System

📌 Project Overview

This repository contains a complete deep-learning pipeline designed to detect scratches on printed text images. The system performs:

✅ 1. Image Classification using EfficientNet-B3

Predicts whether an input image is:

Good (no scratches)

Bad (contains scratches)

✅ 2. Scratch Segmentation using U-Net++

For images classified or suspected as bad, a segmentation model identifies the scratched region.

✅ 3. Hybrid Decision Logic

Combines classifier confidence + scratch mask area to produce highly accurate final decisions.
## 🔧 Installation

```bash
pip install -r requirements.txt


📈 Model Performance

EfficientNet-B3 Classification

| Metric          | Value  |
| --------------- | ------ |
| Precision (Bad) | 1.0000 |
| Recall (Bad)    | 0.9976 |
| F1 Score (Bad)  | 0.9988 |
| Accuracy        | 97.68% |


Confusion matrix and PR curve are available in:

results/confusion_matrix.png

results/precision_recall_curve.png

🧠 Hybrid Decision Logic

Thresholds used:

USER_THRESHOLD = 0.005  
CLASSIFIER_CONF_THRESHOLD = 0.50


Logic:

If classifier predicts bad confidently → BAD

If segmentation scratch area > threshold → BAD

Otherwise → GOOD

This ensures:

No bad image is missed (high recall)

False positives are minimized (high precision)

📁 Dataset Disclaimer

The dataset used for this assignment is private and provided by Mowito.
It is not included in this repository.

🧾 Notes for Reviewer

This repository contains:
✔ All scripts (training, evaluation, inference)
✔ All trained model weights
✔ A complete README with instructions
✔ Results with visual output
✔ A hybrid pipeline implementation

🔗 View Full Work

You can view the full implementation and notebook here:
👉 Kaggle Notebook: https://www.kaggle.com/code/shivashankar2445/scratch-detection-on-text-images


📬 Contact

For help or clarifications:
Email: shivas2445@gmail.com
