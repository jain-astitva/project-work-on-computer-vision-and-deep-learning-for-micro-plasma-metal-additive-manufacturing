# Summer Internship & B.Tech Project: Digital Twin for Micro-Plasma Metal Additive Manufacturing (μ-PMAM) 🔬

This repository documents the work flow, methodology, and progress of developing an AI-driven **Digital Twin** framework for **Micro-Plasma Metal Additive Manufacturing ($\mu$-PMAM)**. The project evolved directly from foundational computer vision and data acquisition tasks completed during a preceding summer internship.

***

## 1. Foundational Summer Internship Work: Image-Based Height Detection

The summer internship focused on establishing the critical **computer vision (CV) pipeline** required for accurate, real-time data acquisition, which became the input source for the subsequent ML models.

### Key Internship Tasks:

* [cite_start]**Image Data Acquisition:** Utilized a high-resolution camera (e.g., Xiris XVC-1000/1100 Weld Camera [cite: 138][cite_start]) to capture raw process videos [cite: 103, 102] of the $\mu$-PMAM process.
* [cite_start]**Video Processing:** Converted raw video into individual frames for detailed observation and analysis[cite: 104, 105].
* [cite_start]**Feature Annotation & Measurement:** Developed Python code using libraries like **`cv2` (OpenCV)** and **`NumPy`** to perform image annotation and precise distance measurement[cite: 106, 110]:
    * **Color Segmentation:** Employed BGR and HSV color conversions and masking (`cv2.inRange`) to robustly detect and isolate a target feature, like a yellow reference line or the deposited layer's edge.
    * **Geometric Extraction:** Extracted the coordinates (e.g., the $\mathbf{X}$-coordinate) of this feature across multiple frames.
* [cite_start]**Data Output:** The outputs—quantifiable height measurements over time—were integrated into Excel files [cite: 111, 112][cite_start], forming the foundational dataset for the Machine Learning pipeline[cite: 113].

***

## 2. B.Tech Project: AI-Driven Digital Twin Implementation

[cite_start]The B.Tech project scaled the internship's data foundation into a fully functional predictive and control system for deposition height uniformity[cite: 22].

### Project Objective: Adaptive Real-Time Control

[cite_start]The primary goal is to achieve uniform deposition and reduce waviness [cite: 28] [cite_start]by creating a closed-loop system that uses Machine Learning to dynamically adjust process parameters[cite: 22]:

* [cite_start]Powder feed rate [cite: 24]
* [cite_start]Microplasma current [cite: 26]
* [cite_start]Traverse speed / feed rate [cite: 27]

### Methodology and Models:

1.  [cite_start]**Forward (Predictive) Modeling: Input $\rightarrow$ Output** [cite: 484, 511]
    * [cite_start]**Goal:** Predict the deposition height profile ($\mathbf{Y}$) based on machine settings ($\mathbf{X}$)[cite: 547].
    * [cite_start]**Technique:** Fitted polynomial curves (from 2nd to 6th degree [cite: 449, 295][cite_start]) to Height vs. Time data for each experiment group[cite: 527, 528].
    * [cite_start]**Model:** Trained a **Random Forest Regressor** to map machine inputs (Powder Feed Rate, Current, FeedRate) to the Polynomial Coefficients [cite: 536, 538] used for simulation.

2.  [cite_start]**Inverse (Control) Modeling: Output $\rightarrow$ Input** [cite: 556]
    * [cite_start]**Goal:** Predict the necessary machine settings (V-I) to achieve a **desired constant height**[cite: 311, 564].
    * [cite_start]**Technique:** Used a **Neural Network (NN)** built with **PyTorch**[cite: 558, 562].
    * [cite_start]**Inputs to NN:** Height, Time[cite: 560, 586].
    * [cite_start]**Outputs from NN:** Predicted Powder Feed Rate, Microplasma Current[cite: 561, 588].

### [cite_start]Work Done (Demonstrated Capabilities) [cite: 179]

* [cite_start]**Simulator Application:** Developed a user-friendly Streamlit web application for simulation, training, and control[cite: 127, 182].
* [cite_start]**Predictive Simulation:** Enabled users to input parameters (Powder Feed Rate, current, speed) and generate instant 3D deposition profiles using MATLAB integration[cite: 177, 291].
* [cite_start]**Constant Height Control:** Implemented a module where the user inputs a **desired height**, and the trained inverse model predicts the required $\mu$-plasma current and powder feed rate to maintain it[cite: 310, 317].

### [cite_start]Future Work (Digital Twin Deployment) [cite: 590]

The immediate next steps toward a full Digital Twin implementation involve moving from simulation to physical control:

* [cite_start]Incorporate sensors and control systems into the machine for true real-time monitoring[cite: 591].
* [cite_start]Vary the microplasma current and powder feed rate on the physical machine to maintain constant deposition height[cite: 592].
* [cite_start]Test on the machine and use the resulting data to update and refine the digital twin for improved adaptive control[cite: 593].