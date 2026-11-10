# Visual SLAM with Dynamic Object Handling

A complete computer vision pipeline that implements a classic Visual Odometry frontend (ORB features + Essential Matrix) and enhances it with **dynamic object filtering** using YOLOv8. Evaluated on the KITTI Odometry benchmark.

---

## Project Overview

Traditional Visual SLAM / Visual Odometry systems can be severely affected by moving objects (cars, pedestrians, cyclists). Features detected on these dynamic objects introduce incorrect motion estimates and increase drift.

This project implements:

- Classic monocular Visual Odometry using ORB features
- Dynamic object detection (person, car, bus, truck, bicycle, motorcycle)
- Feature filtering that removes keypoints lying on dynamic objects
- Side-by-side comparison of Original VO vs Dynamic-Filtered VO
- Trajectory evaluation against KITTI ground truth
- Interactive Gradio demo

---

## Key Features

- ORB feature detection and matching with Lowe’s ratio test
- Essential Matrix estimation + Pose recovery
- YOLOv8-based dynamic object masking
- Static-only feature tracking
- Absolute Trajectory Error (ATE) evaluation
- Rich visualizations (feature separation, trajectory dashboard)
- Gradio web interface

---

## Dataset

**KITTI Odometry**

- Sequences 00–10 (with ground truth poses)
- Stereo RGB images (`image_2` used for monocular VO)
- Camera calibration and timestamps included

---

## Pipeline Architecture

1. **Data Loading & Exploration**
2. **Feature Detection & Matching** (ORB)
3. **Classic Visual Odometry**
4. **Dynamic Object Detection** (YOLOv8)
5. **Dynamic Feature Filtering**
6. **Trajectory Comparison & Evaluation**
7. **Full Pipeline Integration**
8. **Gradio Deployment**

---

## Results (Example on Sequence 00)

| Method                  | ATE (m) | Final Drift (m) |
|-------------------------|---------|-----------------|
| Original VO             | 270.43  | 449.78          |
| Dynamic-Filtered VO     | 279.96  | 460.35          |

> Note: Absolute errors are relatively high because this is a basic frame-to-frame VO without keyframes, local bundle adjustment, or loop closure. The main contribution is the dynamic filtering pipeline.

---

## Installation

```bash
pip install ultralytics opencv-python matplotlib numpy pandas gradio tqdm
```

## How to Run
Download the KITTI Odometry dataset and place it in the expected directory structure.

Run the notebooks/scripts phase by phase (Phase 1 → Phase 8).

Launch the Gradio app (Phase 8) for interactive demonstration.

## Technologies Used

OpenCV (ORB, Essential Matrix, Pose Recovery)

Ultralytics YOLOv8

NumPy / Matplotlib

Gradio

Future Improvements

Keyframe-based VO

Local Bundle Adjustment

Loop Closure Detection

Better dynamic object segmentation (instance masks instead of boxes)

Stereo depth integration

Real-time performance optimization
