Here is your **final polished README.md (copy-paste ready for GitHub)** based on your conference paper .

---

# 🚦 Traffic Sign Detection and Recognition System

A deep learning-based system for **real-time traffic sign detection and classification** using a **two-stage pipeline** combining **YOLOv11** and **EfficientNet-B0**.

---

## 📌 Overview

Traffic sign recognition is a critical component of **Intelligent Transportation Systems (ITS)** and **Advanced Driver Assistance Systems (ADAS)**. This project addresses real-world challenges such as:

* 🌙 Low lighting conditions
* 🚗 Motion blur
* 🚧 Occlusions
* 🌆 Complex backgrounds

To overcome these challenges, a **two-stage architecture** is proposed:

* **Stage 1:** Detection using YOLOv11
* **Stage 2:** Classification using EfficientNet-B0

---

## 🧠 Architecture

```text
Input Image → YOLOv11 Detection → NMS → ROI Extraction → EfficientNet-B0 → Final Output
```
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/717b5a15-0484-4db3-807b-86e1402ce927" />

### 🔹 Workflow

1. Detect traffic signs using YOLOv11
2. Apply Non-Maximum Suppression (NMS)
3. Extract Regions of Interest (ROI)
4. Resize to 224×224
5. Classify using EfficientNet-B0
6. Display bounding boxes with labels

---

## 📂 Dataset

The system uses **two benchmark datasets and a custom dataset** for better generalization and real-world performance.

### 🔹 1. Indian Traffic Sign Dataset (ITSD – Custom)

* Collected from **dashboard camera images**
* Contains real-world conditions:

  * Motion blur
  * Occlusions
  * Lighting variations

#### ➤ Detection Dataset

* 5 coarse classes
* YOLO format (bounding boxes)

#### ➤ Classification Dataset

* 85 fine-grained classes
* ImageFolder format

---

### 🔹 2. German Traffic Sign Recognition Benchmark (GTSRB)

* 50,000+ images
* 43 classes
* Used for:

  * Baseline comparison
  * Model validation

---

### 📊 Dataset Summary

| Dataset               | Classes | Format      | Usage          |
| --------------------- | ------- | ----------- | -------------- |
| ITSD (Detection)      | 5       | YOLO bbox   | Detection      |
| ITSD (Classification) | 85      | ImageFolder | Classification |
| GTSRB                 | 43      | ImageFolder | Baseline       |

---

## 🎯 Detection Model – YOLOv11

* Single-stage object detector
* Real-time performance
* Multi-scale feature detection

### ⚙️ Configuration

* Input size: 640 × 640
* Epochs: 100
* Loss: CIoU + BCE
* Augmentation: Mosaic, HSV

### 📊 Performance

| Metric    | Value |
| --------- | ----- |
| Precision | 0.93  |
| Recall    | 0.91  |
| mAP@0.5   | 0.92  |
| FPS       | 45    |

---

## 🧠 Classification Model – EfficientNet-B0

* Fine-grained classification (85 classes)
* High accuracy with low computation

### ⚙️ Configuration

* Input size: 224 × 224
* Epochs: 50
* Optimizer: Adam
* Loss: Cross-Entropy

### 📊 Performance

* **Accuracy: 96.8%**

---

## 🔁 Two-Stage Pipeline (Key Innovation)

* Separates **detection** and **classification**
* Improves accuracy and modularity
* Reduces background noise using ROI cropping

### ✅ Advantages

* Better performance on small objects
* Higher classification accuracy
* Real-time execution
* Easy model replacement (modular design)

---

## 📊 Results

### 🔹 Model Comparison

| Model                         | Precision | Recall   | mAP      | FPS    |
| ----------------------------- | --------- | -------- | -------- | ------ |
| ResNet50 (Baseline)           | 0.86      | 0.83     | 0.84     | 32     |
| YOLOv11 Only                  | 0.89      | 0.86     | 0.88     | 58     |
| **YOLOv11 + EfficientNet-B0** | **0.93**  | **0.91** | **0.92** | **45** |

---

### 🔹 Key Insights

* EfficientNet-B0 improves classification accuracy
* NMS significantly improves detection quality
* Data augmentation boosts robustness

---

## ⚠️ Challenges

* Small/distant signs are hard to detect
* Similar-looking signs cause confusion
* Performance drops in low-light conditions
* Motion blur affects detection confidence

---

## 🛠️ Tech Stack

* **Language:** Python
* **Frameworks:** PyTorch, Torchvision
* **Libraries:** OpenCV, NumPy, Matplotlib
* **Models:** YOLOv11, EfficientNet-B0, ResNet50
* **Environment:** Google Colab / GPU

---

## 📁 Project Structure

```bash
Traffic-Sign-Detection/
│
├── dataset/
├── models/
├── detection/
├── classification/
├── utils/
├── results/
├── notebooks/
├── main.py
└── README.md
```

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/your-username/traffic-sign-detection.git
cd traffic-sign-detection
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the project

```bash
python main.py
```

---

## 📸 Output

* Detects traffic signs in real-time
* Draws bounding boxes with labels
* Displays confidence scores

*(Add screenshots here for better visualization)*

---

## 🔮 Future Work

* Deploy on edge devices (Jetson Nano, Raspberry Pi)
* Improve detection of small and distant signs
* Use video-based temporal modeling
* Add super-resolution techniques
* Expand dataset for global traffic signs

---



---

## 📜 License

This project is licensed under the **MIT License**.

---


