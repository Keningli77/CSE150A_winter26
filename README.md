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
Hazard
├── Diameter
├── Velocity
├── Distance
└── Magnitude


## Joint Distribution

$$
P(H, D, V, S, M) =
P(H|D,V,S,M)P(D)P(V)P(S)P(M)
$$

Where:

- H = Hazard  
- D = Diameter  
- V = Velocity  
- S = Distance  
- M = Magnitude  

---

# CPT Estimation

We use Maximum Likelihood Estimation:

$$
P(X|Pa(X)) =
\frac{N(X,Pa(X))}{N(Pa(X))}
$$

Example:

$$
P(Hazard = yes | Diameter = large)
=
\frac{N(H=yes,D=large)}
{N(D=large)}
$$

---

# Hidden Markov Model

## Model Structure

$$
Z_t \rightarrow Z_{t+1}
$$

$$
Z_t \rightarrow O_t
$$

Where:

- $Z_t$ = hidden risk state  
- $O_t$ = observation  

---

# HMM Parameters

Initial distribution:

$$
\pi_i = P(Z_1 = i)
$$

Transition matrix:

$$
A_{ij} = P(Z_{t+1}=j|Z_t=i)
$$

Emission matrix:

$$
B_j(k) = P(O_t=k|Z_t=j)
$$

---

# Baum-Welch Algorithm

### E-Step

- Forward algorithm  
- Backward algorithm  
- Compute $\gamma$  
- Compute $\xi$  

### M-Step

Update:

- $\pi$
- $A$
- $B$

---

# Training

## Bayesian Network

We compute:

- Prior probability  
- CPT tables  
- Predictons  

---

# Results

## Bayesian Network Accuracy
Accuracy: 0.766
Baseline:0.902


---

# Confusion Matrix

| | Pred Hazard | Pred Non |
|---|---|---|
| Hazard | 1763 | 5 |
| Non | 4239 | 12161 |

---

# HMM Results

Accuracy:0.603

Confusion Matrix:
[[3778 3294]
[2320 4752]]



---

# Visualization

We generated:

- CPT plots  
- Confusion matrix  
- Log likelihood curve  

---

# Discussion

Observations:

- Large diameter strongly correlates with hazard  
- High velocity increases risk  
- Distance reduces risk  

---

# Limitations

- Discretization loses information  
- Only two hidden states  
- No true temporal order  

---

# Future Work

Possible improvements:

- Continuous Bayesian networks  
- More hidden states  
- Additional asteroid features  
- Dynamic Bayesian networks  

---

---

# References

NASA Near Earth Objects Dataset  
https://www.kaggle.com/

Rabiner, 1989 Hidden Markov Model Tutorial

---

# AI Usage

This project used generative AI for:

- Documentation  
- Formatting  
- Explanation  

