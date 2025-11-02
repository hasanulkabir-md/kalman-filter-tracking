# 🚗 Kalman Filter for Motion Tracking

This project implements a **Kalman Filter** for tracking a moving object in 2D under **noisy sensor measurements**.  
It demonstrates how to combine a simple motion model with uncertain observations to estimate the *true position and velocity* of a target — a foundational technique in **robotics**, **autonomous systems**, and **applied mathematics**.

---

## 🧠 Overview

The Kalman Filter is a recursive Bayesian estimator that fuses two sources of information:
1. **Prediction** from a dynamic model (physics / kinematics)  
2. **Observation** from noisy sensors  

This notebook shows how to:
- Simulate an object’s 2D motion with constant velocity  
- Add Gaussian noise to position readings  
- Implement the full Kalman equations manually  
- Compare noisy vs filtered trajectories  
- Quantify how much error reduction the filter achieves  

---

## 🧱 Project Structure

```

kalman-filter-tracking/
├── data/                → saved sensor readings (CSV)
│   └── kalman_data.csv
├── figures/             → saved plots for analysis
│   ├── kalman_trajectory.png
│   └── kalman_error.png
├── notebooks/
│   └── kalman_filter_tracking.ipynb
├── requirements.txt     → Python dependencies
├── .gitignore           → ignored files/folders
└── README.md            → this file

````

---

## ⚙️ Setup Instructions

### 1️⃣ Create a virtual environment
```bash
python3 -m venv venv
source venv/bin/activate
````

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Launch the notebook

```bash
jupyter notebook notebooks/kalman_filter_tracking.ipynb
```

---

## 📊 Results

### 🔹 Trajectory Comparison

The green line shows **true motion**, gray dots are **noisy measurements**,
and the red dashed line is the **Kalman-estimated trajectory**.

![Kalman Trajectory](figures/kalman_trajectory.png)

### 🔹 Error Comparison

The Kalman Filter reduces position error significantly compared to raw measurements.

![Error Plot](figures/kalman_error.png)

---

## 📈 Mean Error Example

| Source             | Mean Position Error |
| :----------------- | :------------------ |
| Noisy Measurements | 0.52                |
| Kalman Estimate    | 0.16                |

*(Values may vary slightly depending on random seed.)*

---
## 🧮 Mathematical Model

### State Vector
**xₖ = [x, y, vₓ, v_y]ᵀ**

### System Equations
**Prediction:**
> xₖ = F · xₖ₋₁ + wₖ₋₁

**Observation:**
> zₖ = H · xₖ + vₖ

Where:

| Symbol | Meaning |
|:--------|:---------|
| F | State transition matrix (constant velocity model) |
| H | Measurement matrix (position only) |
| Q | Process noise covariance |
| R | Measurement noise covariance |
| wₖ | Process noise (Gaussian) |
| vₖ | Measurement noise (Gaussian) |

These equations describe a **linear Gaussian system** —  
the foundation of the Kalman Filter, which recursively estimates hidden states from noisy data.

---

## 💾 Outputs

| Folder     | Content                                                             |
| :--------- | :------------------------------------------------------------------ |
| `data/`    | Combined true, measured, and filtered positions (`kalman_data.csv`) |
| `figures/` | Generated plots (`kalman_trajectory.png`, `kalman_error.png`)       |

---

## 🧩 Applications

* Autonomous robot localization
* GPS/IMU sensor fusion
* Object tracking in video
* Vehicle and drone navigation

---

## 🧠 References

* R.E. Kalman, *A New Approach to Linear Filtering and Prediction Problems*, 1960.
* S. Thrun, W. Burgard, D. Fox — *Probabilistic Robotics* (MIT Press, 2005).
* Welch & Bishop, *An Introduction to the Kalman Filter*.

---

## 👨‍💻 Author

**Md. Hasanul Kabir**
Master’s Student – Computer Science & Technology
Nanjing Normal University
📧 [hasanulkabir-md](https://github.com/hasanulkabir-md)

