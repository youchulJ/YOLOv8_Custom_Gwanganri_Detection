# YOLOv8 Custom Gwanganri Detection

This project provides a comprehensive pipeline for object detection in aerial footage captured at Gwanganri Beach using YOLOv8. It includes the complete workflow from data preparation, model training, to inference and visualization. The project is designed to detect drones, researchers, and marine litter in video streams.

Multiple Jupyter Notebooks are provided, and it is essential to understand the **role** and **execution order** of each code before running them.

---

## 📚 Notebook Files - Detailed Description & Execution Order

### **1️⃣ KMI_project_part2(data_processing_part).ipynb**

**Role & Purpose:**
- This is the **starting point** of the entire project.
- Loads raw video data from Google Drive and downloads custom datasets from external sources (e.g., Roboflow).
- Converts and preprocesses datasets to match the **YOLO training format**.
- Allows verification of data distribution and labeling status by class.
- Designed to run in Google Colab environment.

**Key Features:**
- Mount Google Drive
- Download dataset from Roboflow
- Dataset format validation and conversion
- Verify image counts per class
- Data preprocessing and cleaning

**Necessity Level:** ⭐⭐⭐ **REQUIRED** - Must be executed first before any model training or inference steps.

---

### **2️⃣ step1__new_model_yolo_weight.ipynb**

**Role & Purpose:**
- The **core training code** that trains a new YOLOv8 model using the custom dataset.
- Installs the Ultralytics YOLOv8 environment and configures training parameters.
- Trains the model for 25 epochs using GPU acceleration (Tesla T4 or similar).
- Generates and saves model weights (best.pt, last.pt) for later inference.

**Key Features:**
- Install and verify YOLOv8 (ultralytics) environment
- GPU availability check
- Automatic Roboflow dataset download
- Model training (25 epochs, batch=16, imgsz=800)
- Visualize training results (confusion matrix, results.png, etc.)
- Save model weights (best.pt, last.pt)

**Generated Output:**
- `runs/detect/train/weights/best.pt` - Best performing model
- `runs/detect/train/weights/last.pt` - Last epoch model
- `runs/detect/train/results.png` - Training curves visualization
- `runs/detect/train/confusion_matrix.png` - Confusion matrix

**Necessity Level:** ⭐⭐⭐ **REQUIRED** - Model weights are essential for all subsequent inference steps.

---

### **3️⃣ step2_new_model_custom_dataset_application_23_09_12.ipynb**

**Role & Purpose:**
- Performs **inference and visualization** using the trained YOLOv8 model (best.pt, etc.).
- Loads video/image files and processes them frame-by-frame with the trained model.
- Uses **ByteTrack** for object tracking and **Supervision** for result visualization.
- Interprets results for actual research applications and saves processed videos.

**Key Features:**
- Load inference video from Google Drive
- Install and configure ByteTrack (object tracking library)
- Install Supervision (object detection visualization library)
- Detect objects in each frame
- Track detected objects across frames
- Display bounding boxes, class names, and confidence scores
- Save processed video with annotations

**Necessity Level:** ⭐⭐⭐ **REQUIRED** (for deployment) - Both trained model weights and target video/images must be prepared before execution.

---

### **4️⃣ __yolov8_custom_YC_11_09_23.ipynb**

**Role & Purpose:**
- **Supplementary code** for additional experiments and preliminary testing.
- Useful for experimenting with different model architectures, hyperparameters, and configurations.
- Serves as a prototype for exploring various settings and validating experimental results.

**Key Features:**
- Custom YOLOv8 configurations and testing
- Model parameter experimentation
- Alternative training approaches

**Necessity Level:** ❌ **OPTIONAL** - Use as needed for additional experiments and research explorations.

---

### **5️⃣ Project_sponsored by KMI_(Weight_part1_24.04.09).ipynb**

**Role & Purpose:**
- Contains **specialized experiments and data analysis** for KMI (Korea Institute of Marine Science and Technology) sponsored research.
- Includes collaborative research results and analysis materials.
- Focuses on specific research topics and deeper analysis.

**Key Features:**
- KMI project-specific model training
- Weight-based analysis
- Collaborative research results organization

**Necessity Level:** ❌ **OPTIONAL** - Reference when working with KMI collaboration or specialized research topics.

---

### **6️⃣ KMI_project_Part2_(자료처리).ipynb**

**Role & Purpose:**
- Handles **additional data preprocessing, format conversion, and statistical analysis**.
- Useful for improving data quality, fixing errors, and completing labeling annotations.
- Provides detailed data inspection and validation.

**Key Features:**
- Original data validation and cleaning
- Data statistical analysis
- Labeling error correction
- Image format conversion
- Data quality assurance

**Necessity Level:** ❌ **OPTIONAL** - Use for fine-tuning original data or handling special cases.

---

## 🪄 **Detectable Classes (Objects)**

| Class Name | Description |
|-----------|-------------|
| **Drone** | Unmanned Aerial Vehicle (UAV) |
| **Marine Litter** | Marine pollution (plastic, debris, etc.) |
| **Researcher** | Research personnel / Humans |

> ※ Check the `CLASS_NAMES_DICT` variable within each notebook to see the most up-to-date class information.

---

## 🚀 **Recommended Execution Order**

```
┌────────────────────────────────────────────────────────────┐
│ STEP 1: Data Preparation (Data Preprocessing)             │
│ KMI_project_part2(data_processing_part).ipynb             │
│ → Mount Google Drive & Download Roboflow dataset          │
└────────────────────────────────────────────────────────────┘
                         ↓
┌────────────────────────────────────────────────────────────┐
│ STEP 2: Model Training (Create New YOLOv8 Weights)         │
│ step1__new_model_yolo_weight.ipynb                        │
│ → Train YOLOv8 model for 25 epochs                        │
│ → Generate best.pt and last.pt weight files               │
└────────────────────────────────────────────────────────────┘
                         ↓
┌────────────────────────────────────────────────────────────┐
│ STEP 3: Model Inference & Visualization (Analyze Video)    │
│ step2_new_model_custom_dataset_application_23_09_12.ipynb │
│ → Analyze video using trained model                       │
│ → Track objects with ByteTrack                            │
│ → Visualize and save results                              │
└────────────────────────────────────────────────────────────┘
                         ↓
┌────────────────────────────────────────────────────────────┐
│ (OPTIONAL) Additional Analysis & Experiments              │
│ • __yolov8_custom_YC_11_09_23.ipynb                       │
│ • Project_sponsored by KMI_(Weight_part1_24.04.09).ipynb  │
│ • KMI_project_Part2_(자료처리).ipynb                      │
└────────────────────────────────────────────────────────────┘
```

---

## 💻 **System Requirements**

- **Python:** 3.x
- **GPU:** CUDA-enabled GPU (Tesla T4, RTX series, etc.) - Colab's free T4 recommended
- **Platform:** Google Colab or local Jupyter Notebook environment
- **Key Packages:**
  - `ultralytics` - YOLOv8 framework
  - `roboflow` - Dataset download and management
  - `ByteTrack` - Object tracking library
  - `supervision` - Detection result visualization
  - `torch` - PyTorch backend
  - `opencv-python` - Video/image processing

> Packages are automatically installed via `!pip install` cells in each notebook.

---

## 📊 **Training Results Example**

| Metric | Value |
|--------|-------|
| **Training Images** | 180 |
| **Validation Images** | 18 |
| **Epochs** | 25 |
| **Batch Size** | 16 |
| **Image Size** | 800x800 |
| **Final mAP50-95** | 0.945 |
| **Drone Detection Rate** | 99.5% |
| **Researcher Detection Rate** | 99.9% |

---

## 📁 **Project Structure**

```
YOLOv8_Custom_Gwanganri_Detection/
├── KMI_project_part2(data_processing_part).ipynb              [Step 1]
├── step1__new_model_yolo_weight.ipynb                         [Step 2]
├── step2_new_model_custom_dataset_application_23_09_12.ipynb  [Step 3]
├── __yolov8_custom_YC_11_09_23.ipynb                          [Reference]
├── Project_sponsored by KMI_(Weight_part1_24.04.09).ipynb     [Reference]
├── KMI_project_Part2_(자료처리).ipynb                        [Reference]
├── roboflow_Gwangalli beach                                   [Roboflow Info]
└── README.md                                                  [This file]
```

---

## 💡 **Usage Tips & Important Notes**

1. **Dataset Preparation:**
   - Step 1 requires Google Drive and Roboflow account access.
   - Roboflow API key must be configured for automatic dataset download.

2. **GPU Memory Management:**
   - Colab's free T4 GPU (~15GB memory) is sufficient for training.
   - Adjust batch size or image size to control memory usage if needed.

3. **Training Time:**
   - 25 epochs training takes approximately 1-2 hours (Tesla T4 GPU).

4. **Results Storage:**
   - All output files (weights, images, monitoring files) are automatically saved in `runs/detect/train/`.
   - Must save to Google Drive before Colab session ends to preserve data.

5. **Hyperparameter Adjustment:**
   - Training parameters like `epochs`, `batch`, `imgsz`, `lr0`, etc. can be modified in the notebook cells.
   - Adjust based on your specific requirements and available GPU memory.

6. **Model Performance:**
   - The provided model achieves excellent performance on the Gwanganri dataset.
   - For new datasets, retrain using Step 1 and Step 2.

---

## 🔍 **Quick Reference Guide**

**I want to...**

- **Train a new model:** Run Step 1 → Step 2
- **Analyze a video:** Run Step 1 → Step 2 → Step 3
- **Test different settings:** Use Step 4 notebook
- **Inspect and clean data:** Use Step 6 notebook
- **View specialized analysis:** Use Step 5 notebook

---

**Last Updated:** 2026-03-25

**Author:** Youchul Jeong
