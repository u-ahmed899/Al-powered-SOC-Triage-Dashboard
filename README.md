# 🛡️ AI-Powered SOC Triage Dashboard

An advanced, real-time Security Operations Center (SOC) dashboard that leverages Machine Learning (Isolation Forest) to detect anomalies and visualize live cyber threats with a stunning 3D interactive UI.

![Python](https://img.shields.io/badge/Python-3.9+-blue?style=flat-square&logo=python)
![Flask](https://img.shields.io/badge/Flask-2.3+-lightgrey?style=flat-square&logo=flask)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3+-orange?style=flat-square&logo=scikit-learn)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow?style=flat-square&logo=javascript)
![Chart.js](https://img.shields.io/badge/Chart.js-4.0+-pink?style=flat-square&logo=chart.js)

<!-- Add a GIF or a high-quality Screenshot here -->
<!-- ![Dashboard Preview](screenshots/dashboard.png) -->

## 🚀 Overview

Security Operations Centers face severe "Alert Fatigue" due to thousands of daily logs. This project solves that by simulating real-time network logs, passing them through an AI anomaly detection model, and streaming the results to a modern, glassmorphism dashboard using **Server-Sent Events (SSE)**.

## ✨ Key Features

- **🧠 AI-Powered Triage:** Uses `IsolationForest` to detect anomalies and classify threats into Critical, High, Medium, and Low severities.
- **⚡ Real-Time Streaming:** A custom Python log generator appends new attacks to a CSV, which are instantly pushed to the frontend via SSE (No page reloads!).
- **🎨 Interactive 3D UI:** Features a modern dark theme, glassmorphism, dynamic Chart.js graphs, and mouse-tracking 3D tilt effects on KPI cards.
- **📊 Live Threat Feed:** Automatically updates and highlights new incoming attacks with their explanations and anomaly scores.
- **📈 Dynamic Charts:** Timeline and Doughnut charts update seamlessly with new data.

## 🏗️ Architecture & Workflow

1. **Log Simulator:** `live_log_generator.py` continuously generates normal and malicious logs, appending them to `data/live_logs.csv`.
2. **AI Engine:** `setup_complete.py` trains an `IsolationForest` model on synthetic historical data to identify feature anomalies.
3. **Backend (Flask):** `src/dashboard.py` watches the CSV, calculates anomaly scores for new logs, and streams them via `/api/attacks/stream`.
4. **Frontend:** Consumes the SSE stream, updates DOM elements, and triggers UI animations in real-time.

## 🛠️ Tech Stack

- **Backend:** Python, Flask, Pandas, Scikit-Learn, Flask-CORS
- **Frontend:** HTML5, CSS3 (Custom 3D Transforms), Vanilla JavaScript, Chart.js
- **Data Processing:** NumPy, Joblib

## ⚙️ Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/soc-triage-dashboard.git
   cd soc-triage-dashboard

2. Create a virtual environment & install dependencies:
    ```bash
   
   python -m venv venv
   # Windows: 
    venv\Scripts\activate
   # Mac/Linux:
   source venv/bin/activate

   pip install -r requirements.txt

3. Initialize Data & Train the Model:
This will generate initial synthetic logs and train the ML model.
   ```bash
   python setup_complete.py

4. Start the Log Generator (Terminal 1):
    ```bash
    python live_log_generator.py

5. Start the Flask Dashboard (Terminal 2):
    ```bash
   python src/dashboard.py

**View the Dashboard:**
Open http://localhost:5000 in your browser. You should see live attacks populating every few seconds!

**🔮 Future Enhancements**
□ Dockerize the application for easy deployment.
□ Integrate with real-world log sources (e.g., Wazuh, ELK Stack).
□ Implement user authentication (JWT) for SOC analysts.
□ Add an incident reporting export feature (PDF/CSV).
