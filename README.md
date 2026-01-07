# Push & Learn: Learning Object Push Dynamics  
**Machine Learning for Robotics (RBE 577) – Project 2**

## 📌 Overview
This project studies **object push dynamics** by modeling how a robotic manipulator (UR10) pushes an object on a planar surface.  
The goal is to **predict the final position and orientation of an object after a push**, and to compare three modeling approaches:

1. **Physics-based model**
2. **Neural Network (MLP) model**
3. **Hybrid Physics + Neural Network model**

This project demonstrates how **classical physics models and data-driven learning** can be combined to improve prediction accuracy in robotic manipulation tasks.

Completed as part of **RBE 577: Machine Learning for Robotics** :contentReference[oaicite:0]{index=0}.

---

## 🎯 Problem Statement
Given:
- Initial object state  
  \[
  s_{start} = [x_0, y_0, \theta_0]
  \]
- Push parameters  
  \[
  (\theta_{push}, d, D, T)
  \]
- Object properties (mass, size)

Predict the final object state:
\[
s_{final} = [x_f, y_f, \theta_f]
\]

---

## 📂 Dataset & Configuration
- **Inputs:**  
  - Initial object pose  
  - Push direction, contact point, distance, duration
- **Outputs:**  
  - Final object pose (ground truth)
- **Files:**
  - `data_x_cracker_box.npy` – push parameters
  - `data_y_cracker_box.npy` – ground truth final states
  - `config/default.yaml` – object mass, size, and physical constants

---

## 🧠 Models Implemented

### 1️⃣ Physics-Based Model
A deterministic model based on **rigid-body dynamics**:
- Velocity profile defined analytically
- Torque and angular acceleration computed using physical equations
- Numerical integration used to update:
  - Orientation
  - Position (local → global frame)

**Loss Function:** Mean Squared Error (MSE)

This model provides **interpretability and physical consistency**, but is sensitive to modeling assumptions.

---

### 2️⃣ Neural Network Model (MLP)
A purely **data-driven approach**:
- Multi-Layer Perceptron with at least one hidden layer
- Learns push dynamics directly from data
- Trained using supervised learning

This model captures **nonlinear relationships** that physics alone may fail to model.

---

### 3️⃣ Hybrid Physics + Neural Network Model
A **hybrid approach** that combines the strengths of both worlds:
- Physics model predictions used as **input features** to the neural network
- Neural network learns to correct physics-based errors
- Achieves improved generalization and accuracy

---

## 📊 Evaluation & Visualization
For all models:
- Mean Squared Error (MSE) computed
- Training loss curves plotted
- Predicted trajectories compared with ground truth

Visual outputs include:
- Training curves
- Prediction vs ground truth plots

---

## 🗂️ Project Structure
