# Agroforestry Computer Vision Projects: YOLOv8 Canopy Segmentation & Tree Top Detection

This repository contains two primary Google Colab-based workflows utilizing the **Ultralytics YOLOv8** framework for aerial and drone-based agroforestry analysis:
1. **Canopy Segmentation & Spatial Surface Area Calculation** (YOLOv8m-seg)[cite: 1]
2. **Tree Top Detection & Counting** (YOLOv8m)

---

## Project Overview

### 1. Canopy Segmentation (`forest-3` Dataset)
* **Model:** `yolov8m-seg.pt` (Instance Segmentation)[cite: 1]
* **Objective:** Detect individual tree canopies, generate precise pixel-level masks, and calculate their physical surface area in square meters using a defined Ground Sampling Distance (GSD).
* **Key Features:**
  * Automated dataset download via the Roboflow API.
  * Fine-tuning with high-resolution image scaling (`imgsz=1024`) and customized batch sizing (`batch=8`) to handle high VRAM consumption.
  * Post-processing spatial math mapping pixel counts to real-world area ($\text{Area} = \text{Pixel Count} \times \text{GSD}^2$).

* **Sample Results**
  <img width="950" height="563" alt="Canopy results" src="https://github.com/user-attachments/assets/27fc50fd-1afa-4479-ad97-dede1b59407a" />


### 2. Tree Top Detection (`Tree-Top-View-6` Dataset)
* **Model:** `yolov8m.pt` (Object Detection)
* **Objective:** Identify and locate individual tree tops in dense aerial layouts.
* **Key Features:**
  * Fine-tuning with standard high-resolution overhead inputs (`imgsz=640`).
  * Custom inference tuning using NMS (Non-Maximum Suppression) confidence (`conf=0.45`) and IoU (`iou=0.4`) thresholds to accurately count trees and avoid double-counting overlapping crowns.
 
* **Sample Results**
  <img width="950" height="563" alt="Tree count result" src="https://github.com/user-attachments/assets/02e3a95a-a720-41e5-9ec0-f6628b4b0f2f" />


---

## Repository Structure

```text
├── canopy_segmentation.ipynb         # Instance segmentation & surface area workflow
├── tree_top_detection.ipynb          # Object detection & bounding box inference workflow
└── README.md                         # Project documentation
