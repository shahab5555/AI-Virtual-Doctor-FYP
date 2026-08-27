 AI Virtual Doctor: A Multimodal Integrated Diagnostic Engine with Enhanced 34-Symptom Fusion and XAI

![AWKUM Banner](https://img.shields.io/badge/AWKUM-Department%20of%20Computer%20Science-blue)
![Python](https://img.shields.io/badge/Python-3.12-brightgreen)
![Streamlit](https://img.shields.io/badge/Streamlit-App-ff4b4b)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10+-orange)
![XAI](https://img.shields.io/badge/Explainable%20AI-Grad--CAM-yellowgreen)

An advanced, Explainable AI (XAI) driven multi-modal decision-support platform designed to solve the healthcare **Triage Gap**. By fusing fine-tuned **MobileNetV2** deep feature extraction with an enhanced **34-symptom clinical checklist profile** and **OCR lab report scanning**, the system delivers accurate multi-class diagnoses alongside transparent Grad-CAM heatmaps.

---

## 📌 Key Highlights & Features

* **Multimodal Fusion Engine:** Late-fusion architecture combining fine-tuned **MobileNetV2** image feature extraction with tabular clinical symptom inputs.
* **Enhanced 34-Symptom Checklist Profile:** Interactive clinical symptom checklist and tabular feature vectoring for nuanced patient triage.
* **Explainable AI (XAI Hub):** Refined **Grad-CAM heatmaps** generated directly from the un-nested output layers (`out_relu`) to visually highlight the exact anatomical zone of infection.
* **Smart Heatmap Deactivation:** Heatmaps are intelligently deactivated when processing lab test sheets to avoid telemetry artifacts and provide pure tabular insight.
* **OCR Telemetry Scanner:** Integrated **Tesseract OCR Engine** to automatically parse printed medical/lab records and auto-populate patient clinical attributes.
* **Streamlit Interactive UI:** A clean, production-ready web interface (`app_2.py`) designed for seamless clinical workflow execution.
* **Resource-Optimized:** Built for lightweight execution on standard local hardware using optimized batch generators and custom Keras inference pathways.

---

## 📊 Performance & Validation Results

* **Validation Accuracy:** ~85.96%
* **AUC-ROC Score:** ~0.97
* **Loss Metric:** Low Loss (0.51)
* **Dataset Scale:** 150,000+ Total Aggregate Records across Pathology, Sonography, Radiology, and Clinical Diagnostic wings.

---

## 🏗️ System Architecture

```text
                     +-----------------------------------+
                     |           Patient UI              |
                     +-----------------+-----------------+
                                       |
                +----------------------+----------------------+
                |                                             |
   +------------v------------+                   +------------v------------+
   |   Image Input Wing      |                   |    Tabular Symptom Wing |
   |   (Radiology/Sonography)|                   |   (34-Symptom Checklist)|
   +------------+------------+                   +------------+------------+
                |                                             |
     Fine-Tuned MobileNetV2                               Dense Layers
                |                                             |
                +----------------------+----------------------+
                                       |
                              Late Fusion Concatenate
                                       |
                           34-Class Softmax Output
                                       |
                 +---------------------+---------------------+
                 |                                           |
    Differential Diagnosis Engine                   XAI Grad-CAM Generator
     (Top Diagnostic Possibilities)               (Anatomical Heatmap Overlay)
```

---

## 🛠️ Project Structure

```text
.
├── app_2.py                 # Main Streamlit web application dashboard
├── models/                  # Trained Keras models (.h5) & weight checkpoints
├── src/
│   ├── ocr_scanner.py       # Tesseract OCR report parsing engine
│   ├── model_builder.py     # Un-nested MobileNetV2 + Symptom Late-Fusion architecture
│   ├── gradcam.py           # Grad-CAM heatmap extraction module
│   └── data_loader.py       # Data generators & preprocessing pipelines
├── data/                    # Dataset directories (Radiology, Sonography, Pathology)
├── assets/                  # Poster images, UI screenshots, and diagrams
├── requirements.txt         # Required dependencies
└── README.md                # Project documentation
```

---

## 🚀 How to Run the Project

### 1. Prerequisites
Ensure you have **Python 3.10+** installed on your system along with **Tesseract OCR**.

### 2. Installation & Setup
Clone the repository and install required packages:
```bash
git clone https://github.com/your-username/AI-Virtual-Doctor.git
cd AI-Virtual-Doctor

# Create and activate virtual environment
python -m venv venv
# On Windows:
venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 3. Launching the Dashboard App
Run the following command in your terminal to launch the Streamlit app:
```bash
python -m streamlit run app_2.py
```
This will automatically open the interactive web interface in your default web browser at `http://localhost:8501`.

---

## 🔮 Future Work Roadmap

* **Real-time Camera Integration:** Live video feed integration for real-time ultrasound and skin lesion scanning.
* **Expanded Diagnostic Scope:** Scaling disease coverage to **39+ clinical conditions**.
* **Mobile Deployment:** Mobile application suite (Android/iOS) for field triage in rural healthcare clinics.

---

## ⚠️ Disclaimer

This system is built as a **Clinical Decision-Support System (CDSS)** for preliminary triage and decision aid. It is **not** a replacement for professional clinical diagnosis. All recommendations should be reviewed and signed off by a certified medical practitioner.

---

## 👨‍💻 Project Team & Credit

* **Students:** Amir Salman (`AWKUM-22142195`), Shahab Uddin (`AWKUM-22135693`), Yasir Ali (`AWKUM-22154931`)
* **Supervisor:** Sawera Qureshi, Lecturer
* **Institution:** Department of Computer Science, Abdul Wali Khan University Mardan (AWKUM)
