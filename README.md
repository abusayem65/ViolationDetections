# Bus Stoppage Violation Detection System

This repository contains the implementation of an automated system designed to detect bus stoppage violations using the **YOLOv11** object detection model. This project is part of my final year thesis.

---

## 📌 Project Overview
The primary goal of this project is to identify whether a bus is stopping within the designated legal boundary or violating traffic rules by stopping elsewhere. The system processes images/videos from both CCTV and bus-mounted cameras.

- **Model:** YOLOv11 (Ultralytics)
- **Primary Classes:** Bus, Bus Stop, Shelter, Seating, Trash Can.
- **Input:** Images and Video Streams.

# 🖥️ Local Model Testing via Web Interface

1. **Clone the repository**
    ```bash
    git clone https://github.com/thezahidul/ViolationDetections.git
    cd ViolationDetections/
    ```

2. **Create a virtual environment:**
    ```bash
    python -m venv venv
    ```

3. **Activate the virtual environment:**
    * **On Windows (Command Prompt):**
      ```cmd
      venv\Scripts\activate
      ```
    * **On Windows (PowerShell):**
      ```powershell
      .\venv\Scripts\activate
      ```
    * **On macOS/Linux:**
      ```bash
      source venv/bin/activate
      ```

4. **Install dependencies**
    ```bash
    # Navigate to the inner core project directory
    cd illegal-bus-stoppage-detection/
    
    # [Linux/Ubuntu Users Only] Run this if you face folder permission issues:
    # sudo chown -R $USER:$USER ../venv
    
    # Install the required software ecosystem
    pip install -r requirements.txt
    ```

5. **Run Detection (Streamlit App Interface)**
    Place your test validation frames or images in the `data/` folder and execute:
    ```bash
    streamlit run src/app.py
    ```
    *Open your web browser and navigate to the local host address:* `http://localhost:8501`


# 🔌 Production API Testing Guidelines (FastAPI backend)

This module allows developers, IoT edge devices (like Jetson Nano), or external systems to send physical parameters (bus speed) and image streams to verify traffic infractions programmatically.

---

## 🛠️ Launching the API Server

1. Ensure your virtual environment is activated (see setup instructions above).
2. Navigate directly to the API container directory:
    ```bash
    cd illegal-bus-stoppage-detection/src/api
    ```

3. Initialize the ASGI server instance:
    * **Standard Cross-Platform Command:**
      ```bash
      python -m uvicorn main:app --reload
      ```
    * **Alternative (Linux/macOS):**
      ```bash
      python3 -m uvicorn main:app --reload
      ```

Expected terminal output confirmation:

INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
    
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

