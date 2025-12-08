# Face Reconstruction from Partially Leaked Facial Embeddings

This project is a part of the **AAI-521** course in the Applied Artificial Intelligence Program at the University of San Diego (USD).  

-- Project Status: **Completed**

## Installation

### Recommended: Run in Google Colab (Zero setup – 5 minutes)
1. Click here → [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1JDhrlSn_LkE7rInYY54dnTzgUVGFB2dq)
2. When prompted, upload your `mfr2.zip` file (or it will auto-download from Kaggle)
3. Runtime → Run all  
   → Everything installs and executes automatically

### Local Installation (Optional)
```bash
git clone https://github.com/SridharSurapaneni07/AAI521-group6-project.git
cd AAI521-group6-project

python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

pip install -r requirements.txt
jupyter notebook "Team06_Final.ipynb"
```


📌 **Project Objective**

This project demonstrates that raw facial embeddings used in modern face recognition systems are not privacy-safe. Even when an attacker has access to only 30% of a 512-D embedding (153 values), they can reconstruct a face that fully fools face recognition systems (mAP@1 = 1.0).

We simulate realistic leakage scenarios—data breaches, partial API exposure, and storage truncation—and show that current practices of storing/transmitting embeddings pose serious biometric privacy risks.
We also propose a lightweight defense, targeted masking of low-variance dimensions, which improves privacy by +8%, while preserving most utility.

✔ Relevant to: biometric security, mobile authentication, surveillance systems, and federated learning.

👥 **Contributors**

Sridhar Surapaneni

Sai Navyesh Pamarthi

Rohit Andani

🧠 **Methods Used**

Computer Vision

Deep Learning / Transfer Learning

Autoencoders & Transposed Convolutions

Embedding Inversion Attacks

Mask Detection (ConvNeXt)

Ablation Studies

Privacy & Ethics in AI

Data Visualization

🛠️ **Technologies**

Python

PyTorch / TorchVision

Hugging Face Transformers

facenet-pytorch

Google Colab / Jupyter Notebook

NumPy, Pandas, Matplotlib, Seaborn

scikit-image, OpenCV

LPIPS, PyTorch-FID

📂 **Dataset**

We use the MFR2 dataset (269 celebrity images, 53 identities) from Kaggle.
Images include mixed masked/unmasked faces with real-world lighting and pose variability.

**Preprocessing**

Applied ConvNeXt-FaceMask-Finetuned (99.61% accuracy)

Confidence threshold: 0.85 → retained 138 images

Final cleaned dataset: 71 high-quality full-face images

Resized to 128×128, normalized to [-1, 1]

🔧 **Pipeline Overview**

Generate 512D embeddings using InceptionResNetV1 (VGGFace2)

Separation gap: 0.8202

Simulate embedding leakage by masking:

10%

30%

50%

Train a transposed-convolutional autoencoder per leakage level.

Evaluate using:

MSE

SSIM

Cosine similarity (re-embedded)

LPIPS

FID

mAP@1 face-matching performance

Ablation study:

Random masking

Targeted low-variance masking (proposed defense)

🎯 **Key Challenges**

MFR2 lacks clean labels → used deep learning–based mask detection

Very small dataset (71 images) → required dropout, early stopping, strong regularization

FID unstable at small sample sizes → used trend-based interpretation instead

🚀 **Final Results** (30% Embedding Leakage)
Metric	Result
Reconstructed identity match	mAP@1 = 1.0000
Defense improvement	+8% cosine similarity reduction
Attack success	Attacker fully fools face recognition

**Conclusion**:
➡ Even partial embedding leakage leads to complete identity compromise.
➡ Simple defenses significantly improve privacy — but more robust methods are needed.

📜 **License**

This project is licensed under the MIT License.
See the LICENSE file for details.
