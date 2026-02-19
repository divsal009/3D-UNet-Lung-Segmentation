# 3D U-Net Lung Segmentation with Positional Encoding

This repository contains the implementation of a deep 3D U-Net architecture with sinusoidal positional encoding for automated left and right lung segmentation from volumetric thoracic CT scans.

The network follows a symmetric encoder–decoder structure (32–64–128–256–512 bottleneck) and is implemented in PyTorch. Training supervision combines Cross-Entropy and Dice loss for multi-class segmentation (background, left lung, right lung).

---

## Datasets

### NHS BRUCI Thoracic CT Dataset (Restricted Access)

Clinical volumetric CT scans from the BRUCI cohort were used for model development and evaluation.

Due to patient confidentiality and institutional governance restrictions, these data are not publicly available.

Access may be granted upon reasonable request and subject to appropriate ethical approvals and data sharing agreements.

---

### Lung CT Segmentation Challenge 2017 (LCTSC) – Public Dataset

To ensure reproducibility, the model can be evaluated using the publicly available LCTSC dataset:

Yang et al., 2017  
Data from Lung CT Segmentation Challenge 2017  
DOI: https://doi.org/10.7937/K9/TCIA.2017.3R3FVZ08  
Available via The Cancer Imaging Archive (TCIA).

---

## Model Architecture

- 3D U-Net backbone  
- Channel progression: 32 → 64 → 128 → 256 → 512  
- Sinusoidal positional encoding  
- Multi-class output (Background, Left Lung, Right Lung)  
- Dice + Cross-Entropy loss  

---

## Reproducibility

This repository ensures experimental reproducibility through:

Fixed random seed across NumPy and PyTorch

Deterministic training configuration to minimise stochastic variability

Complete training and inference pipeline implementation

Publicly available trained model weights (model_epoch15.pth)

External dataset validation provided via a dedicated validation notebook

---

## Running the Code

Set dataset paths using environment variables:

Linux / macOS:
export CT_DIR=/path/to/ct
export MASK_DIR=/path/to/masks

Windows (PowerShell):
setx CT_DIR "D:\path\to\ct"
setx MASK_DIR "D:\path\to\masks"

Then run:
python train.ipynb
