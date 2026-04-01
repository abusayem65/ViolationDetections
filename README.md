# Bus Stoppage Violation Detection System

This repository contains the implementation of an automated system designed to detect bus stoppage violations using the **YOLOv11** object detection model. This project is part of my final year thesis.

---

## 📌 Project Overview
The primary goal of this project is to identify whether a bus is stopping within the designated legal boundary or violating traffic rules by stopping elsewhere. The system processes images/videos from both CCTV and bus-mounted cameras.

- **Model:** YOLOv11 (Ultralytics)
- **Primary Classes:** Bus, Bus Stop, Shelter, Seating, Trash Can.
- **Input:** Images and Video Streams.

---

1. **Clone the repository**
    ```bash
    git clone https://github.com/jahidul17/Data-Science.git
    ```

2. **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    # On Windows
    venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3. **Install dependencies**
    ```bash
    pip install ultralytics opencv-python
    ```


4. **Run Detection**
   Place your test images in the data/ folder and execute:
    ```bash
    python detect.py
    ```
    
## 📊 Dataset & Results
#### 📂 Dataset (1,100+ Images)
The model was trained on a custom-curated dataset of over 1,200 images, specifically labeled for bus stop infrastructure and vehicle positioning to ensure high accuracy in violation detection.

**Dataset Link:** Download Dataset from Google Drive
https://drive.google.com/file/d/154_HpA77ra5RlFbzOm1sHJkzXNqR0otG/view?usp=sharing

## 📈 Thesis Project Results
Detailed training logs, confusion matrices, performance graphs, and inference results (output images/videos) are available here:

**Result Folder:** View Project Results on Google Drive
https://drive.google.com/drive/folders/1RBBKi4eG7KyfznEFwtxqylLeHqDB9xKi?usp=sharing

## 🛠️ Violation Logic
###### The system utilizes a Region of Interest (ROI) mapping technique:

**Detection:** The model identifies the 'Bus' and the 'Bus Stop' area in real-time.

**Coordinate Analysis:** If the bounding box of the 'Bus' remains stationary for a specific duration outside the designated 'Bus Stop' coordinates, a Violation is triggered and logged automatically.

