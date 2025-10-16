I apologize for the oversight. You are right; for a clean copy-paste into a GitHub `README` file, citations and unnecessary formatting should be completely removed.

Here is the absolutely clean, final Markdown content for your `README.md` file, ready to be copied directly:

# Summer Internship & B.Tech Project: Digital Twin for Micro-Plasma Metal Additive Manufacturing (μ-PMAM) 🔬

This file documents the work flow, methodology, and progress of developing an AI-driven **Digital Twin** framework for **Micro-Plasma Metal Additive Manufacturing ($\mu$-PMAM)**. The project evolved directly from foundational computer vision and data acquisition tasks completed during a preceding summer internship.

***

## 1. Foundational Summer Internship Work: Image-Based Height Detection

The summer internship focused on establishing the critical **computer vision (CV) pipeline** required for accurate, real-time data acquisition, which became the input source for the subsequent ML models.

### Key Internship Tasks:

* **Image Data Acquisition:** Utilized a high-resolution camera to capture raw process videos of the $\mu$-PMAM process.
* **Video Processing:** Converted raw video into individual frames for detailed observation and analysis.
* **Feature Annotation & Measurement:** Developed Python code using libraries like **`cv2` (OpenCV)** and **`NumPy`** for image annotation and precise length detection (similar to identifying the $\mathbf{X}$-coordinate of a reference line or deposited edge):
    * **Color Segmentation:** Employed BGR and HSV color conversions and masking to robustly isolate and detect the target feature (e.g., a yellow reference line).
    * **Geometric Extraction:** Extracted the coordinates of this feature across multiple frames.
* **Data Output:** The outputs—quantifiable length/height measurements over time—were integrated into Excel files, forming the foundational dataset for the Machine Learning pipeline.

***

## 2. B.Tech Project: AI-Driven Digital Twin Implementation

The B.Tech project scaled the internship's data foundation into a fully functional predictive and control system for deposition height uniformity.

### Project Objective: Adaptive Real-Time Control

The primary goal is to achieve uniform deposition and reduce waviness by creating a closed-loop system that uses Machine Learning to dynamically adjust process parameters:

* Powder feed rate
* Microplasma current
* Traverse speed / feed rate

### Methodology and Models:

1.  **Forward (Predictive) Modeling: Input $\rightarrow$ Output**
    * **Goal:** Predict the deposition height profile ($\mathbf{Y}$) based on machine settings ($\mathbf{X}$).
    * **Technique:** Fitted polynomial curves (from 2nd to 6th degree) to Height vs. Time data.
    * **Model:** Trained a **Random Forest Regressor** to map machine inputs (Powder Feed Rate, Current, Speed) to the coefficients used for simulation.

2.  **Inverse (Control) Modeling: Output $\rightarrow$ Input**
    * **Goal:** Predict the necessary machine settings (V-I) to achieve a **desired constant height**.
    * **Technique:** Used a **Neural Network (NN)** built with **PyTorch**.
    * **Inputs to NN:** Height, Time.
    * **Outputs from NN:** Predicted Powder Feed Rate, Microplasma Current.

### Work Done (Demonstrated Capabilities)

* **Simulator Application:** Developed a user-friendly Streamlit web application for simulation, training, and control.
* **Predictive Simulation:** Enabled users to input parameters and generate instant 3D deposition profiles using MATLAB integration.
* **Constant Height Control:** Implemented a module where the user inputs a **desired height**, and the trained inverse model predicts the required $\mu$-plasma current and powder feed rate to maintain it.

### Future Work (Digital Twin Deployment)

The immediate next steps toward a full Digital Twin implementation involve moving from simulation to physical control:

* Incorporate sensors and control systems into the machine for true real-time monitoring.
* Vary the microplasma current and powder feed rate on the physical machine to maintain constant deposition height.
* Test on the machine and use the resulting data to update and refine the digital twin for improved adaptive control.
