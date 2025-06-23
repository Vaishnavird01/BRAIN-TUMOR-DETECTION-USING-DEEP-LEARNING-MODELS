# Brain Tumor Detection Using Deep Learning

## Project Overview

This project presents an end-to-end deep learning system for detecting brain tumors from MRI images. By leveraging **Convolutional Neural Networks (CNN)** and a **custom-built VGG-16 architecture**, the system classifies brain scans into *tumorous* and *non-tumorous* categories. It aims to support radiologists and clinicians in early diagnosis through automation and accuracy.

> **Published at: [2020 IEEE INDISCON Conference](https://ieeexplore.ieee.org/document/9344555)**  
> *IEEE Xplore Document ID:* 9344555

---

## Datasets Used

- **Source:** Private MRI collection  
- **Total Images:** 253  
  - Tumorous: 155  
  - Non-tumorous: 98  

### Post-Augmentation Dataset

- Tumorous: 1085  
- Non-tumorous: 980  

### Data Splits

| Dataset      | Tumorous | Non-Tumorous | Total |
|--------------|----------|--------------|-------|
| Training     | 758      | 687          | 1445  |
| Validation   | 152      | 158          | 310   |
| Testing      | 175      | 135          | 310   |

---

## Data Preprocessing

To ensure quality and consistency in input images, we performed:

- **Data Augmentation** (rotation, flipping, zoom)
- **Grayscale Conversion**  
- **Noise Removal** using erosions, dilations, and Gaussian blur  
- **Contour Detection** and **Extreme Point Cropping**
- **Resizing**:  
  - 240×240 for CNN  
  - 224×224 for VGG-16  
- **Normalization** and standardization of pixel values  
- **Dataset Split** into training, validation, and testing sets

---

## Algorithms and Models

| Domain         | Method             | Description |
|----------------|--------------------|-------------|
| Tumor Detection | CNN (Custom)       | Built from scratch with convolutional + pooling layers |
| Tumor Detection | VGG-16 Architecture | Constructed custom VGG-16 without transfer learning |

### CNN Highlights

- Layers: Conv2D → BatchNorm → ReLU → MaxPooling  
- Final Layers: Flatten → Dense → Sigmoid  
- Input: 240x240x3

### VGG-16 Highlights

- Stacked 3×3 convolutions with increasing filters  
- MaxPooling after each block  
- Dense: 4096 → 1000 → 1 (Sigmoid)  
- Input: 224x224x3

---

## Tech Stack & Tools

- **Language:** Python  
- **Libraries:**
  - Data Handling: `pandas`, `numpy`, `cv2`
  - Deep Learning: `TensorFlow`, `Keras`
  - Visualization: `matplotlib`, `seaborn`
  - Augmentation: `ImageDataGenerator`

---

## Key Results

| Metric             | CNN      | VGG-16   |
|--------------------|----------|----------|
| Training Accuracy  | 93.36%   | 97.16%   |
| Validation Accuracy| 86.45%   | 97.42%   |
| Test Accuracy      | 91.60%   | 91.90%   |
| Training Time      | 5 mins   | 15 mins  |

### Takeaways

- **CNN** is faster and more lightweight, suitable for real-time applications  
- **VGG-16** achieves superior accuracy, better for high-stakes diagnostics  
- VGG-16 peaked at **epoch 17**, after which validation accuracy plateaued

---

## Future Scope

- Incorporate **transfer learning** (e.g., pretrained VGG, ResNet)  
- Expand dataset to cover **tumor types** (glioma, meningioma, etc.)  
- Build a **real-time web-based diagnostic tool**  
- Add **explainability** tools (Grad-CAM, SHAP) for medical transparency  
- Explore **transformer-based vision models (ViT)**

---

## References

1. Karen Simonyan & Andrew Zisserman, *"Very Deep Convolutional Networks for Large-Scale Image Recognition,"* ICLR 2014

2. Yuehao Pan et al., *"Brain Tumor Grading using CNNs,"* IEEE

3. Taranjit Kaur et al., *"Automated Brain Image Classification with VGG-16,"* ICIT 2019

---

> 💡 “This system bridges AI and radiology to enable faster, more accurate brain tumor diagnosis through deep learning.”
