# CSE150A Project — Probabilistic Modeling of Near-Earth Asteroids

## Overview

This project applies **probabilistic modeling** to predict whether a **Near-Earth Object (NEO)** is hazardous using NASA asteroid data.

We implement two probabilistic models:

- Bayesian Network (BN)
- Hidden Markov Model (HMM)

The goal is to model **uncertainty in asteroid hazard prediction**.

---

# Dataset

## Dataset Description

We use the **NASA Near Earth Objects Dataset**, which contains observations of near-Earth asteroids collected by NASA.

- Dataset size: **90,836 samples**
- Source: NASA
- Task: Hazard prediction

### Features

| Feature | Description |
|---------|-------------|
| est_diameter_max | Maximum estimated diameter |
| relative_velocity | Velocity relative to Earth |
| miss_distance | Distance from Earth |
| absolute_magnitude | Intrinsic brightness |
| hazardous | Target variable |

Identifier fields such as `id` and `name` were removed.

---

## Tasks

Using this dataset:

1. Classification  
2. Probabilistic inference  
3. Sequential modeling  

We estimate:

$$
P(Hazardous \mid Features)
$$

---

## Why Probabilistic Modeling?

Asteroid hazard prediction is uncertain:

- Large asteroid may still be safe  
- Fast asteroid may be far away  
- Observations contain measurement noise  

Thus probabilistic modeling is appropriate.

---

# Dataset Properties

| Property | Description |
|----------|-------------|
| Size | 90,836 samples |
| Source | NASA |
| Reliability | High |
| Type | Continuous + categorical |

---

# Data Preprocessing

### Feature Selection

We selected:

- Diameter  
- Velocity  
- Distance  
- Magnitude  
- Hazard label  

---

### Discretization

Continuous variables were discretized:

| Feature | Bins |
|---------|------|
| diameter | small / medium / large |
| velocity | low / medium / high |
| distance | near / medium / far |
| magnitude | low / medium / high |

---

### Train Test Split

- 80% training  
- 20% testing  

---

### Class Balancing

Original dataset:

- Non-hazardous ≈ 90%
- Hazardous ≈ 10%

Balanced using downsampling.

---

# PEAS Analysis

## Performance Measure

- Accuracy  
- Log likelihood  
- Hidden state inference  

## Environment

Near-Earth asteroid environment

## Actuators

- Predicted hazard label  
- Probability output  

## Sensors

- Diameter  
- Velocity  
- Distance  
- Magnitude  

---

# Bayesian Network

## Structure
