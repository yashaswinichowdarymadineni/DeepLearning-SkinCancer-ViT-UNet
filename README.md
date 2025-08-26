# Deep Learning for Skin Cancer Segmentation & Classification using Vision Transformer and U-Net Hybrid Architecture

A deep learning project implementing a **hybrid Vision Transformer (ViT) + U-Net architecture** for automated skin lesion **segmentation** and **classification** (benign vs. malignant). Trained and evaluated on **ISIC datasets**, the model combines the **global context modeling of Vision Transformers** with the **precise spatial localization of U-Nets** to support early skin cancer detection.

---

##  What It Does
- **Segmentation** → Generates pixel-level lesion masks using a U-Net style decoder.  
- **Classification** → Predicts benign vs. malignant lesions with a ViT-based classification head.  
- **Loss Functions** → Combined Dice Loss + Binary Cross-Entropy (BCE) for segmentation; Weighted Cross-Entropy for classification to address class imbalance.  
- **Datasets** → ISIC dermoscopic datasets.  
- **Evaluation** → Dice Score, IoU, Accuracy, Sensitivity, Specificity, and AUC.  

---

## Model Architecture

- **Vision Transformer Encoder (ViT):**  
  The input image is divided into 16×16 patches and projected into embeddings. These embeddings are processed through multiple Transformer encoder layers using multi-head self-attention. This allows the model to capture **global dependencies** and contextual information across the image.

- **U-Net Style Decoder:**  
  The encoder’s output features are reshaped into a 2D map and progressively upsampled through transposed convolutions. Each stage refines the spatial resolution to reconstruct a segmentation mask, providing **fine-grained lesion boundaries**.

- **Classification Head:**  
  The special [CLS] token from the ViT encoder is passed through a linear layer to predict **benign vs. malignant** labels, enabling the model to perform **dual tasks** (segmentation + classification).

- **Loss Design:**  
  - **Segmentation:** BCE + Dice Loss ensures pixel-level accuracy while optimizing region overlap.  
  - **Classification:** Weighted Cross-Entropy mitigates class imbalance between benign and malignant samples.  

---

## Tech Stack
**Deep Learning** • **PyTorch** • **Vision Transformer (ViT)** • **U-Net** • **ISIC Dataset** • **Scikit-learn** • **NumPy** • **Pandas** • **Matplotlib/Seaborn**

---

## Results

### ISIC 2016 (Validation)
- Dice Score: **0.905**  
- IoU: **0.827**  
- Accuracy: **83%**

### ISIC 2017 (Test Set)
- Dice Score: **0.78**  
- IoU: **0.74**  
- Accuracy: **77%**  
- AUC: **0.77**

---


MIT
