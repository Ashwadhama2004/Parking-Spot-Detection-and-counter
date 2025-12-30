

# Parking Spot Detection and Occupancy Monitoring using Computer Vision

This project implements a **computer vision–based parking spot detection system** that automatically identifies whether parking slots are **empty or occupied** using video footage. It uses **OpenCV**, **image processing**, and **frame differencing** to monitor parking availability in real time.

The system is efficient, does not require deep learning models, and works well for fixed-camera parking surveillance scenarios.

---

## Project Overview

The system works by:

* Using a **binary mask image** to define parking slot locations.
* Detecting individual parking spots using **connected components analysis**.
* Processing video frames at fixed intervals to reduce computation.
* Comparing consecutive frames to detect motion or changes.
* Classifying each parking spot as **empty or occupied**.
* Displaying results visually with **green (empty)** and **red (occupied)** bounding boxes.

---

## Methodology

### 1. Mask-Based Parking Spot Detection

* A binary mask image is used where each parking slot is marked.
* `cv2.connectedComponentsWithStats()` extracts bounding boxes for each parking spot.
* These bounding boxes remain fixed throughout execution.

### 2. Video Frame Processing

* Video is read frame-by-frame using OpenCV.
* Frames are processed every fixed interval (`step = 30`) to improve performance.

### 3. Frame Difference Calculation

* The mean pixel intensity of the current frame is compared with the previous frame.
* A difference score is calculated for each parking spot.
* Only spots with significant changes are re-evaluated.

### 4. Parking Slot Classification

* Each selected parking spot is cropped.
* The `empty_or_not()` function determines occupancy.
* Slot status is stored and reused until updated.

### 5. Visualization

* Green bounding box → Empty spot
* Red bounding box → Occupied spot
* Output is displayed in real time using OpenCV.

---

## Tech Stack

* Python
* OpenCV
* NumPy
* Matplotlib

---

## File Structure

```
.
├── data/
│   ├── mask_1920_1080.png
│   └── parking_1920_1080.mp4
├── utils.py
│   ├── get_parking_spots_bboxes()
│   └── empty_or_not()
├── main.py
└── README.md
```

---

## How to Run the Project

### 1. Install Dependencies

```bash
pip install opencv-python numpy matplotlib
```

### 2. Run the Script

```bash
python main.py
```

### 3. Controls

* Press `q` to quit the video window.

---

## Key Functions Explained

### `get_parking_spots_bboxes()`

Extracts bounding boxes of parking slots from the binary mask using connected components.

### `calc_diff(im1, im2)`

Calculates mean pixel intensity difference between two frames for motion detection.

### `empty_or_not(spot_crop)`

Determines whether a parking spot is empty or occupied based on visual features.

---

## Results

* Efficient real-time parking monitoring.
* Low computational cost.
* Works reliably for fixed-camera parking environments.
* Easily extendable to large parking areas.

---

## Limitations

* Requires a static camera.
* Mask must be manually created.
* Performance may reduce in extreme lighting or weather changes.

---

## Future Improvements

* Integrate deep learning for higher robustness.
* Add parking count and analytics dashboard.
* Deploy as a web application using Streamlit or Flask.
* Add night-time and weather adaptation.

---

## Author

Gaurang Chaturvedi
Computer Vision | Machine Learning | AI Development

