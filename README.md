# Scratch-Detection-on-Text-Images
Scratch Detection on Text Images
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

This repository satisfies all the requirements listed by Mowito for their internship evaluation.

📂 Repository Structure
project-root/
│
├── Script/
│   ├── classifier_inference.py
│   ├── segmentation_inference.py
│   ├── hybrid_inference.py
│   ├── utils_preprocessing.py
│   ├── utils_visualization.py
│   ├── (other scripts used in training/testing)
│
├── models_weights/
│   ├── efficientnet_b3_best.pt
│   ├── unetpp_best.pt
│   ├── hybrid_thresholds.json
│
├── results/
│   ├── confusion_matrix.png
│   ├── precision_recall_curve.png
│   ├── sample_predictions/
│   ├── segmentation_masks/
│
├── .gitignore
├── README.md
└── requirements.txt

🔧 Installation
1️⃣ Install dependencies
pip install -r requirements.txt

🚀 How to Run the Models
1️⃣ Classification (EfficientNet-B3)

Run prediction on a single image:

python Script/classifier_inference.py --image path/to/image.jpg

Output example:
Image: text_005.jpg
Predicted: BAD
Bad Probability: 0.9372
Threshold: 0.50

2️⃣ Segmentation (U-Net++)

Generate a scratch mask:

python Script/segmentation_inference.py --image path/to/image.jpg


Output:

A binary scratch mask saved in results/segmentation_masks/

3️⃣ Hybrid Final Prediction

Uses classifier + segmentation mask + decision thresholds:

python Script/hybrid_inference.py --image path/to/image.jpg


Output:

Classifier says BAD (p=0.84)
Segmentation scratch area = 0.0063
Threshold = 0.0050
Hybrid Final Decision: BAD
Mask saved at: results/segmentation_masks/img_mask.png

📈 Model Performance
EfficientNet-B3 Classification
Metric	Value
Precision (Bad)	1.0000
Recall (Bad)	0.9976
F1 Score (Bad)	0.9988
Accuracy	97.68%

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

🧾 Notes for Reviewer (Mowito)

This repository contains:

✔ All scripts (training, evaluation, inference)
✔ All trained model weights
✔ A complete README with instructions
✔ Results with visual outputs
✔ A hybrid pipeline implementation

📬 Contact

If you need help running the models:

Email: shivshankareppa23@gmail.com
