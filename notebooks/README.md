# Project Notebooks & Execution Guide

This directory contains the four core Jupyter notebooks that make up the end-to-end pipeline for the **Workplace Safety PPE Detection System**. 

## How to Run

You have three options for running this project depending on your hardware and goals.

### **Requirements**
* **Python**: 3.8 or higher
* **RAM**: 8GB minimum
* **GPU**: Recommended for training (CPU works but is very slow)
* **Disk Space**: ~2GB free

### **Dataset**
* **Source**: Construction Site Safety (Roboflow/Kaggle)
* **Size**: 2,801 images with YOLO format annotations
* **Classes**: 10 (Hardhat, NO-Hardhat, Safety Vest, NO-Safety Vest, Mask, NO-Mask, Person, Safety Cone, Machinery, Vehicle)

---

### Option A: Run Demo Only (Fastest - 5 minutes)
*Use this if you just want to see the model in action without training.*

1.  **Clone the repository**:
    ```bash
    git clone <your-repo-url>
    cd PPE-2
    ```
2.  **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```
3.  **Download the trained model**:
    * Download `best.pt` from the project Google Drive.
    * Place the file in `models/trained/best.pt`.
4.  **Open the demo notebook**:
    ```bash
    jupyter notebook notebooks/04_demo.ipynb
    ```
5.  **Run all cells**:
    * Click "Kernel" > "Restart & Run All".
    * Upload your own construction site images to test or use provided samples.

---

### Option B: Run Full Pipeline (2-3 hours)
*Use this if you want to train the model from scratch on your local machine.*

1.  **Setup**: Clone repo and install dependencies (as above).
2.  **Set up Kaggle API**:
    * Go to [kaggle.com](https://kaggle.com) > Account > Create New API Token.
    * Download `kaggle.json`.
    * Place in `~/.kaggle/kaggle.json` (Linux/Mac) or `C:\Users\<username>\.kaggle\kaggle.json` (Windows).
3.  **Execute Notebooks in Order**:
    * **Step 1**: Run `01_data_exploration.ipynb` (~10 mins).
    * **Step 2**: Run `02_model_training.ipynb` (~1.5 hrs on GPU).
    * **Step 3**: Run `03_evaluation.ipynb` (~15 mins).
    * **Step 4**: Run `04_demo.ipynb` (~10 mins).
4.  **View Results**:
    * Metrics: `results/metrics.txt`
    * Visualizations: `results/visualizations/`

---

### Option C: Run on Google Colab (Free GPU)
*Recommended for fastest training if you don't have a local GPU.*

1.  **Open Google Colab**: Go to [colab.research.google.com](https://colab.research.google.com).
2.  **Upload Notebooks**: Upload all 4 files from this folder.
3.  **Enable GPU**: Click "Runtime" > "Change runtime type" > Select "GPU" (T4).
4.  **Mount Drive**: Add this code to the top of each notebook to save progress:
    ```python
    from google.colab import drive
    drive.mount('/content/drive')
    ```
5.  **Run in Order**: Execute notebooks 01 through 04 sequentially.

---

## In-Depth Notebook Analysis

Here is a detailed technical breakdown of the logic and code within each notebook.

### **1. `01_data_exploration.ipynb` (Data Prep)**
This notebook handles the ETL (Extract, Transform, Load) process for the project.
* **Data Acquisition**: Uses the `kaggle` API to download the "Construction Site Safety" dataset directly into the environment. It handles zip extraction and directory structuring.
* **Data Cleaning**: Iterates through the raw data to identify corrupted images or label files with missing coordinates.
* **Stratified Splitting**: Instead of a random split, this implements a **stratified 70/15/15 split**. This ensures that rare classes (like `NO-Hardhat` or `NO-Safety Vest`) are proportionally represented in Training, Validation, and Test sets to prevent class imbalance issues.
* **YAML Generation**: Automatically generates the `dataset.yaml` file required by YOLOv8, writing absolute paths to the training and validation images.
* **Visualization**: Uses Matplotlib to plot the distribution of classes (bar charts) and display sample images with bounding boxes to verify annotation integrity.

### **2. `02_model_training.ipynb` (The Engine)**
This is the core training loop using the Ultralytics YOLOv8 framework.
* **Model Selection**: Initializes a `yolov8s.pt` (Small) model using transfer learning (pre-trained on COCO). The 'Small' variant was chosen as the optimal trade-off between accuracy (better than Nano) and speed (faster than Medium/Large).
* **Hyperparameter Tuning**: Configures the training run with specific parameters:
    * `epochs=200`: High epoch count to ensure convergence.
    * `patience=50`: Early stopping to prevent overfitting if validation loss plateaus.
    * `batch=16`: Optimized for standard GPU memory (16GB).
    * `imgsz=640`: Standard YOLO input resolution.
* **Augmentation Pipeline**: Implements aggressive data augmentation to improve robustness:
    * **Mosaic (1.0)**: Stitches 4 images together (forces model to detect small objects).
    * **Mixup (0.1)**: Blends images to reduce confidence in ambiguous regions.
    * **Rotation/Flip**: Simulates different camera angles on construction sites.
* **Artifact Handling**: Automatically saves the best weights (`best.pt`) and training logs (CSV events) to the output directory.

### **3. `03_evaluation.ipynb` (Performance Audit)**
This notebook acts as the quality assurance phase, validating the model against data it has never seen (the Test set).
* **Metrics Calculation**: Runs `model.val()` to compute:
    * **mAP@50** (Mean Average Precision at 50% IoU): The primary metric for detection accuracy.
    * **Precision & Recall**: To balance false positives vs. missed detections.
* **Confusion Matrix**: Generates a confusion matrix to visualize which classes are being confused (e.g., is the model confusing "Person" with "Safety Vest"?).
* **Confidence Analysis**: Runs inference at varying confidence thresholds (0.25, 0.50, 0.75) to determine the optimal deployment threshold.
* **Per-Class Breakdown**: Outputs a table showing accuracy for *each* specific class (e.g., "How accurately do we detect missing hardhats vs. machinery?").

### **4. `04_demo.ipynb` (Deployment & Inference)**
This notebook simulates the production environment where the model processes raw images and outputs safety reports.
* **Custom Inference Pipeline**: Defines wrapper functions (`run_inference`) to standardize prediction settings (IoU thresholds, etc.).
* **Safety Logic (`check_safety_compliance`)**: This is the business logic layer. It iterates through detections to flag specific violations:
    * If `NO-Hardhat` is detected → **Trigger Alert**.
    * If `NO-Safety Vest` is detected → **Trigger Alert**.
    * If `Person` is detected but no PPE → **Cross-reference**.
* **Visualization Engine**: Uses OpenCV (`cv2`) to draw color-coded bounding boxes and labels (Red for danger/missing PPE, Green for compliance).
* **Batch Processing**: Demonstrates running the model over a folder of new images and generating a summary report of total violations detected.
