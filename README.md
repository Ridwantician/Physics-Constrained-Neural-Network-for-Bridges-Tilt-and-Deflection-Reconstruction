# \# Physics-Constrained Neural Network for Bridge Tilt and Deflection Reconstruction

# 

# \## Overview

# 

# This repository contains the implementation of a Physics-Constrained Neural Network (PCNN) framework for reconstructing bridge slope and deflection fields from sparse tiltmeter measurements. The work is based on the IDA-KI OpenLab Research Bridge at TU Dresden and forms part of a Master's thesis on physics-guided machine learning for structural health monitoring.

# 

# The framework combines data-driven learning with Euler–Bernoulli beam theory to infer full-field structural response from limited sensor observations.

# 

# \---

# 

# \## Repository Contents

# 

# \### 1. CEI-PCNN

# 

# Constant-EI Physics-Constrained Neural Network for full-field slope and deflection reconstruction using measured tiltmeter data.

# 

# Three trial-function variants are implemented:

# 

# \* \*\*SPTF\*\* – Single Polynomial Trial Function

# \* \*\*PPTF\*\* – Piecewise Polynomial Trial Function

# \* \*\*PETF\*\* – Pretrained EnvelopeNet Trial Function

# 

# Each variant enforces bridge boundary conditions through a physics-constrained trial solution while satisfying the governing beam equation.

# 

# \### 2. AR Model

# 

# Autoregressive cross-sensor prediction model for next-day tiltmeter forecasting.

# 

# Features include:

# 

# \* Cross-sensor coupling

# \* Temperature effects

# \* Phase-dependent loading conditions

# \* Ridge regression regularization

# 

# \### 3. AR-PCNN

# 

# Hybrid framework combining:

# 

# 1\. AR-based next-day sensor prediction

# 2\. Physics-constrained full-field reconstruction

# 

# The AR model predicts future sensor responses, which are subsequently used by the trained PCNN to estimate future bridge slope and deflection fields.

# 

# \---

# 

# \## Bridge Case Study

# 

# \*\*Structure:\*\* IDA-KI OpenLab Research Bridge, TU Dresden

# 

# \* Two-span continuous prestressed concrete bridge

# \* Span configuration: 2 × 15 m

# \* Instrumented middle T-girder

# \* Tiltmeters located at:

# 

# &#x20; \* x = 11 m

# &#x20; \* x = 19 m

# 

# Dataset:

# 

# \* 253 daily observations

# \* February–October 2024

# \* Four loading phases

# 

# \---

# 

# \## Methodology

# 

# The PCNN framework incorporates:

# 

# \* Euler–Bernoulli beam physics

# \* Boundary condition enforcement through trial functions

# \* Automatic differentiation for high-order derivatives

# \* Trainable distributed load identification

# \* Fourier feature encoding for temporal and thermal effects

# 

# Loss functions include:

# 

# \* Data loss

# \* PDE residual loss

# \* Continuity loss

# \* Boundary-condition loss (where applicable)

# 

# \---

# 

# \## Validation

# 

# Model predictions are validated against Finite Element Method (FEM) reconstructions of:

# 

# \* Slope

# \* Deflection

# \* Distributed loading

# 

# Validation locations include:

# 

# \* x = 5 m

# \* x = 10 m

# \* x = 20 m

# \* x = 25 m

# 

# \---

# 

# \## Requirements

# 

# Main dependencies include:

# 

# \* Python 3.10+

# \* PyTorch

# \* NumPy

# \* Pandas

# \* SciPy

# \* Scikit-learn

# \* Matplotlib

# \* Jupyter Notebook

# 

# Install dependencies using:

# 

# ```bash

# pip install -r requirements.txt

# ```

# 

# \---

# 

# \## Usage

# 

# Run the notebooks sequentially from top to bottom.

# 

# Typical workflow:

# 

# 1\. Data preprocessing

# 2\. AR model training

# 3\. PCNN training

# 4\. Load identification

# 5\. Full-field reconstruction

# 6\. Validation against FEM

# 7\. AR-PCNN future prediction

# 

# \---

# 

# \## Author

# 

# \*\*Ridwan Ademola Ibrahim\*\*

# 

# Erasmus Mundus MSc in Smart Cities and Communities (SMACCs)

# 

# Research areas:

# 

# \* Structural Health Monitoring (SHM)

# \* Physics-Informed Machine Learning

# \* Digital Twins

# \* Smart Infrastructure

# \* Bridge Monitoring

# 

# \---

# 

# \## License

# 

# This repository is provided for academic and research purposes.



