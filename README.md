<div align="center">

# 🎯 Self-Driving Car — PID Controller

### Feedback Control for Autonomous Vehicle Steering

![C++](https://img.shields.io/badge/C++-Control_Systems-blue?style=for-the-badge&logo=cplusplus)
![PID Control](https://img.shields.io/badge/PID-Feedback_Control-green?style=for-the-badge)
![Autonomous Driving](https://img.shields.io/badge/Autonomous_Driving-Steering_Control-orange?style=for-the-badge)
![Control Theory](https://img.shields.io/badge/Control-Theory-red?style=for-the-badge)
![Self Driving Cars](https://img.shields.io/badge/Domain-Vehicle_Control-purple?style=for-the-badge)

Udacity Self-Driving Car Engineer Nanodegree Project

</div>

---

# Overview

Perception, localization, and planning are only part of the autonomous driving challenge.

A vehicle must also convert decisions into physical actions.

This project implements a **PID (Proportional–Integral–Derivative) Controller** that continuously adjusts vehicle steering based on cross-track error (CTE) to keep the vehicle centered on the road.

The controller receives real-time feedback from the simulator and computes steering corrections that allow the vehicle to navigate the track smoothly and autonomously.

---

# Project Objectives

The goals of this project were to:

- Implement a PID controller in C++
- Minimize cross-track error (CTE)
- Maintain lane position
- Reduce oscillations
- Tune controller parameters
- Explore automatic parameter optimization with Twiddle

---

# Feedback Control Loop

```text
Vehicle Position
        ↓
Cross Track Error (CTE)
        ↓
PID Controller
        ↓
Steering Command
        ↓
Vehicle Response
        ↓
Updated Position
```

The controller continuously adjusts steering to reduce the error between the vehicle's current position and the desired trajectory.

---

# PID Components

A PID controller combines three feedback mechanisms:

## Proportional (P)

The proportional term reacts to the current error.

- Large error → strong steering correction
- Small error → small steering correction

This component provides immediate response to deviations from the center of the lane. :contentReference[oaicite:0]{index=0}

---

## Derivative (D)

The derivative term reacts to the rate of change of error.

Its purpose is to:

- Reduce oscillations
- Improve stability
- Smooth steering behavior

Without a derivative term, the vehicle may overcorrect and continuously weave from side to side. :contentReference[oaicite:1]{index=1}

---

## Integral (I)

The integral term accumulates error over time.

It helps compensate for:

- Persistent bias
- Mechanical imperfections
- Systematic drift

This component improves long-term accuracy by penalizing cumulative error. :contentReference[oaicite:2]{index=2}

---

# Controller Architecture

```text
          +-------------+
CTE ----->|     PID     |-----> Steering
          +-------------+
                │
                │
          P + I + D
                │
                ▼
        Vehicle Control
```

The steering command is computed from the weighted combination of the three PID terms.

---

# Parameter Tuning

Controller performance depends heavily on selecting appropriate gains.

Initial tuning was performed manually before applying automated optimization. :contentReference[oaicite:3]{index=3}

Initial values:

```cpp
vector<double> p = {0.15000, 0.00100, 1.70000};
vector<double> dp = {0.01000, 0.00010, 0.1000};
```

These values provided a stable starting point for further optimization. :contentReference[oaicite:4]{index=4}

---

# Twiddle Optimization

The project also explores the **Twiddle algorithm**.

Twiddle is a simple optimization technique that automatically adjusts controller gains to improve performance. :contentReference[oaicite:5]{index=5}

The algorithm:

1. Adjusts one parameter
2. Evaluates performance
3. Keeps beneficial changes
4. Rejects poor changes
5. Repeats until convergence

This process helps identify improved PID coefficients without exhaustive manual tuning. :contentReference[oaicite:6]{index=6}

---

# Technical Skills Demonstrated

## Control Systems

- PID Control
- Feedback Loops
- Closed-Loop Control
- Stability Analysis

## Autonomous Driving

- Steering Control
- Vehicle Dynamics
- Trajectory Following

## Optimization

- Hyperparameter Tuning
- Twiddle Optimization
- Performance Evaluation

## Software Engineering

- Modern C++
- Real-Time Systems
- Numerical Computing

---

# Repository Structure

```text
src/
├── PID.cpp
├── PID.h
├── main.cpp

README.md
writeup.md
```

---

# Results

The controller successfully keeps the vehicle on the track while minimizing cross-track error.

The final solution demonstrates:

✅ Stable lane following

✅ Reduced oscillation

✅ Smooth steering corrections

✅ Successful autonomous navigation

The vehicle remains controllable despite the dynamic challenges of the simulated environment.

---

# Key Concepts Explored

- PID Controllers
- Feedback Control
- Vehicle Dynamics
- Closed-Loop Systems
- Optimization
- Autonomous Navigation
- Steering Control
- Real-Time Decision Making

---

# Why This Project Matters

Control systems are one of the foundational pillars of autonomous vehicles.

Even with perfect perception and planning, a vehicle must still execute commands safely and accurately.

PID controllers remain widely used throughout engineering because they provide:

- Simplicity
- Robustness
- Real-time performance
- Strong practical results

Applications include:

- Autonomous vehicles
- Drones
- Industrial robotics
- Aerospace systems
- Manufacturing automation

---

# Related Self-Driving Car Projects

This repository is part of a larger autonomous driving portfolio:

- Finding Lane Lines
- Advanced Lane Finding
- Traffic Sign Classifier
- Behavioral Cloning
- Extended Kalman Filter Sensor Fusion
- Kidnapped Vehicle Localization
- Highway Path Planning
- PID Controller

Together these projects cover perception, localization, planning, control, and autonomous navigation.

---

# Learning Outcomes

This project provided hands-on experience with:

- Classical Control Theory
- PID Controllers
- Controller Tuning
- Feedback Systems
- Autonomous Vehicle Control

It represents the final stage of the autonomous driving stack: converting decisions into physical vehicle actions.

---

# Disclaimer

This repository is provided for educational and portfolio purposes.

Students may study the code and reports for learning purposes, but submitting this work as coursework would constitute plagiarism and may violate academic integrity policies.

Copyright © Sabrina Palis
