# A Cutting-Edge Visual Cartographer & Navigation within Enclosed Environment

![Python](https://img.shields.io/badge/Python-3.7-blue.svg) ![Simulator](https://img.shields.io/badge/Simulator-CARLA-orange.svg) ![Status](https://img.shields.io/badge/Status-Completed-green.svg)


This project is a **CARLA-based autonomous system** designed for advanced state estimation and real-time 3D point cloud generation. 

Addressing the limitations of individual sensors in autonomous driving—such as GNSS signal loss in tunnels or IMU drift over time—this system implements a robust **Sensor Fusion** approach. By integrating **GNSS**, **IMU**, and **LiDAR** data using an **Extended Kalman Filter (EKF)**, the system achieves highly accurate localization and mapping in dynamic urban environments.

---

# Project Demos

Watch the system in action through the following simulation recordings:

* [**🎬 Project Demo 1**](https://drive.google.com/file/d/1vkEWrqsHhmje5ttuZm8ZtSHV15ceBaUx/view?usp=sharing)
* [**🎬 Project Demo 2**](https://drive.google.com/file/d/1_zscse8AEFyigtUBNwyQHPmPVZ9hAYam/view?usp=sharing)
* [**🎬 Project Demo 3**](https://drive.google.com/file/d/18pW-PL4ZXU9JwQ7h-TfKL0JsrVMpM_M8/view?usp=sharing)
* [**🎬 Project Demo 4**](https://drive.google.com/file/d/1q559OPEnXnvtEddwElGQ3Gzq4Xz4qwKs/view?usp=sharing)
* [**🎬 Project Demo 5**](https://drive.google.com/file/d/1WwW43jt-k2HPL_KH3eGzz3GttK1O9mW8/view?usp=sharing)

## Key Features

* **Multi-Sensor Fusion:** Combines data from GNSS, IMU, and LiDAR to minimize position error.
* **Real-Time Localization:** Utilizes the Extended Kalman Filter (EKF) to predict and correct vehicle position dynamically.
* **3D Point Cloud Generation:** Generates high-quality 3D maps of the environment using LiDAR and RGB/Depth cameras.
* **LiDAR Odometry:** Implements the **Iterative Closest Point (ICP)** algorithm for scan matching and relative displacement calculation.
* **Robustness:** Mitigates the "drift" issue found in standalone IMU systems and the "multipath" errors found in standalone GNSS systems.

---

## System Architecture

The system operates within the **CARLA Simulator** using a Client-Server architecture. The workflow involves:

1.  **Data Acquisition:** Collecting raw data from GNSS (1 Hz), IMU (250 Hz), and LiDAR (10 Hz).
2.  **Front End:** Motion estimation using LiDAR odometry (ICP algorithm) and IMU acceleration data.
3.  **Sensor Fusion:** Applying the Extended Kalman Filter (EKF) to merge predictions (IMU) with measurements (GNSS/LiDAR).
4.  **Back End:** Generating the 3D Point Cloud map and updating the vehicle's state.

---

## Tech Stack & Dependencies

The project is built using **Python 3.7**.

| Component | Specification/Library |
| :--- | :--- |
| **Simulator** | CARLA (Car Learning to Act) |
| **Environment** | Anaconda (Virtual Env) |
| **Point Clouds** | Open3D |
| **Computer Vision** | OpenCV 4.4.0 |
| **Math/Plotting** | NumPy 1.19.5, Matplotlib 2.2.2 |
| **Game Engine** | Pygame |

---

## Hardware Requirements

To run the simulation with high fidelity (**Epic Mode**), the following specifications are recommended:

* **OS:** Windows 10+ or Ubuntu 20.04.
* **GPU:** NVIDIA RTX 3070 / 3080 / 4090 (Recommended).
    * *Note: The project was tested on a Radeon RX 570, which experienced high resource consumption and crashes.*
* **RAM:** Minimum 32GB.
* **CPU:** Intel i7/i9 (9th Gen+) or AMD Ryzen 7/9.

---

## Results

The project compared three localization methods to validate performance:

| Method | Observation |
| :--- | :--- |
| **GNSS Only** | Provided global coordinates but suffered from noise and signal gaps. |
| **IMU Only** | Accurate for short bursts but accumulated significant exponential error (drift) over time. |
| **Sensor Fusion** | **Achieved the highest accuracy.** |

**Final Accuracy:**
* Ground Truth vs. Estimated Position Error: **0.150** (Euclidean Distance).

---

## Future Work

- [ ] **NDT Integration:** Implementation of Normal Distributions Transform for potentially faster scan matching compared to ICP.
- [ ] **AI Integration:** Integration of Deep Learning methods for enhanced state estimation.
- [ ] **Optimization:** Testing on high-end hardware to resolve thermal throttling and V-RAM crashes encountered during testing.

---

## Authors

* **Muneeb Iqbal** 
* **Asad Ali** 

**Supervisor:** Engr. Muhammad Haris
**Institution:** Balochistan University of Information Technology, Engineering, and Management Sciences (BUITEMS)
