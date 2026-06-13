# 🇮🇳 Sanchay-AI: Smart Coin Audit & Savings Bridge

[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com)
[![YOLOv10](https://img.shields.io/badge/YOLOv10-Ultralytics-emerald?style=for-the-badge&logo=yolo)](https://github.com/ultralytics/ultralytics)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com)
[![Gradio](https://img.shields.io/badge/Gradio-orange?style=for-the-badge)](https://gradio.app)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org)

**Sanchay-AI** (bridging physical cash to digital wealth) is an automatic coin counter, detector, and micro-savings platform. It utilizes advanced computer vision techniques to detect, identify, and count Indian Rupee coins (₹1, ₹2, ₹5, ₹10, ₹20) from images or live video feeds, runs surface oxidation checks to ensure RBI compliance, and allocates the audited cash automatically between UPI digital credit, Digital Gold SIP, and CSR Impact/Charity.

🔗 **GitHub Repository Link:** [https://github.com/hema470/Automatic-coin-counter-and-detector](https://github.com/hema470/Automatic-coin-counter-and-detector)

---

## 🚀 Key Features

*   **AI Coin Denomination Recognition:** Integrated YOLOv10 model (`best.pt`) optimized for detection and localization of Indian coins (₹1, ₹2, ₹5, ₹10, and ₹20).
*   **RBI Compliance & Surface Audit:** Conducts real-time HSV color-space analysis to measure rust, dirt, and oxidation percentage, classifying coins as **FIT ✅** or **UNFIT ⚠️** for circulation.
*   **Mint Condition Bonus:** Offers an automatic cashback incentive (+₹0.50) for deposits of clean/mint-quality coins.
*   **Micro-Savings Split:** Allows custom distribution of detected coin values (e.g., 20% to Digital Gold SIP, 5% to Impact/CSR Fund, and the remainder directly to UPI Wallet).
*   **Dual Frontend Client:**
    1.  **FastAPI Premium Dashboard:** A sleek, dark-themed dashboard styled with Tailwind CSS and Alpine.js. Includes interactive doughnut charts, live webcam capturing, and asset ledgers.
    2.  **Gradio Interface:** A quick, interactive Python-native app interface for debugging and rapid prototyping.

---

## 📁 Repository Structure

*   [`run.py`](file:///c:/Users/hemz/Downloads/Automatic-coin-counter-and-detector-main/run.py): The main entry point script that checks dependencies and starts the FastAPI server.
*   [`backend/main.py`](file:///c:/Users/hemz/Downloads/Automatic-coin-counter-and-detector-main/backend/main.py): FastAPI backend script containing YOLOv10 object detection and HSV compliance algorithms.
*   [`backend/static/index.html`](file:///c:/Users/hemz/Downloads/Automatic-coin-counter-and-detector-main/backend/static/index.html): Custom Tailwind CSS and Alpine.js frontend served directly by the backend.
*   [`backend/app.py`](file:///c:/Users/hemz/Downloads/Automatic-coin-counter-and-detector-main/backend/app.py): Gradio app script serving the secondary user interface layout.
*   [`backend/best.pt`](file:///c:/Users/hemz/Downloads/Automatic-coin-counter-and-detector-main/backend/best.pt): Custom-trained YOLOv10 weights.
*   [`requirements.txt`](file:///c:/Users/hemz/Downloads/Automatic-coin-counter-and-detector-main/requirements.txt): Required packages for compiling and executing the project.

---

## 🛠️ Installation & Setup

### Prerequisites
Make sure you have Python 3.8+ and `pip` installed on your system.

### 1. Clone the Repository
```bash
git clone https://github.com/hema470/Automatic-coin-counter-and-detector.git
cd Automatic-coin-counter-and-detector
```

### 2. Install Dependencies
Install all required libraries including OpenCV, FastAPI, Uvicorn, and Ultralytics YOLO:
```bash
pip install -r requirements.txt
```

---

## 🚦 How to Run the Application

### Option A: Start the FastAPI Dashboard (Recommended)
Run the launcher script:
```bash
python run.py
```
Or run Uvicorn directly:
```bash
uvicorn backend.main:app --reload --port 8000
```
Open your browser and navigate to:
👉 **[http://127.0.0.1:8000](http://127.0.0.1:8000)**

### Option B: Start the Gradio Interface
For a simplified interface running on port `7860`:
```bash
python backend/app.py
```
Open your browser and navigate to:
👉 **[http://127.0.0.1:7860](http://127.0.0.1:7860)**

---

## 🔍 How it Works (Under the Hood)

1.  **Image Upload / Capture:** The user provides an image via the local webcam feed or files.
2.  **YOLOv10 Inference:** The backend runs the image through the custom-trained YOLOv10 model (`best.pt`) to locate and label coin denominations.
3.  **Oxidation Scoring:** The region inside each coin is mapped to the HSV color space. Pixels matching the rust color spectrum are calculated against the total coin pixel count.
4.  **Transaction Ledger Execution:** Value distributions are calculated according to user splits and credit ledgers are returned instantly as JSON payloads.
