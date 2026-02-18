# 🏏 Cricket Ball Detection, Tracking & Trajectory Estimation

This project implements a computer vision pipeline for detecting and tracking a cricket ball in broadcast match videos using YOLOv8. The system generates annotated output videos showing the ball trajectory and produces per-frame centroid annotations in CSV format for further analysis.

---

### 📂 Repository Structure

```text
.
├── annotations/          # 15 CSV files (per-frame centroid annotations)
├── code/                 # Jupyter notebook with training + inference pipeline
├── runs/                 # Trained YOLOv8 weights (best.pt, yolov8l.pt)
├── results/              # 15 annotated output videos (.mp4)
├── report.pdf            # Final project report
└── README.md             # Project documentation
```

🚀 Running the Pipeline
All code is provided inside the Jupyter notebook located in the code/ folder.

Step 1: Open Notebook

* Launch Jupyter from your terminal:

* Navigate to the code/ folder and open the notebook.

Step 2: Set Paths Inside Notebook

Update the following variables in the configuration cell to match your local environment:

```
MODEL_PATH = "code/runs/detect/train/weights/best.pt"
INPUT_VIDEO = "path_to_input_video.mp4"
OUTPUT_DIR = "results"
CSV_OUTPUT_DIR = "annotations"
```

Step 3: Run Inference
[!IMPORTANT]

* To process videos and see results, run the Inference section only. Do not run the Training section unless you intend to retrain the model (which takes ~11 hours).

The notebook will:

* Load the trained YOLOv8 model.

* Perform detection and tracking.

* Generate an annotated video in results/.

* Save the centroid CSV file in annotations/.

📤 Outputs
For each input video, the system generates:

1. Annotated Video (.mp4):
A processed video showing the bounding box, historical trajectory, and path predictions.

2. Centroid CSV File:
A data file containing the tracking coordinates for every frame.
Format: frame_index, x_centroid, y_centroid, visibility_flag

📊 Notes
* Some frames may not contain detections due to motion blur or occlusion.
* Temporal post-processing enables reconstruction of a smooth trajectory despite occasional missed detections.

## 📦 Dataset
The training dataset consists of annotated cricket ball images collected from broadcast cricket videos. The dataset is used to train the YOLOv8 model for ball detection.
Due to large file size, the dataset is hosted externally.

🔗 **Download Link:**  
https://drive.google.com/file/d/1P-C7g5rB1tAt4tVlxTx-DjvByRRpyALO/view?usp=sharing

### Dataset Contents
- Images extracted from broadcast videos  
- YOLO-format annotations (`.txt`)  
- Train / validation split  
