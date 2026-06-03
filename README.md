# Physics-Constrained Neural Network for Bridge Tilt and Deflection Reconstruction

**Author:** Ridwan Ademola Ibrahim
**Program:** Erasmus Mundus MSc in Smart Cities and Communities (SMACCs)

---

## Overview

This repository contains the implementation of a Physics-Constrained Neural Network (PCNN) framework for reconstructing full-field bridge slope and deflection from sparse tiltmeter measurements. The work is based on data collected from the IDA-KI OpenLab Research Bridge at TU Dresden and forms part of a Master's thesis on physics-guided machine learning for structural health monitoring.

The framework combines data-driven learning with Euler–Bernoulli beam theory to reconstruct structural response, identify distributed loads, and predict future bridge behavior using a hybrid autoregressive and physics-constrained approach.

---

## Bridge Case Study

**Structure:** IDA-KI OpenLab Research Bridge, TU Dresden

* Two-span continuous prestressed concrete bridge
* Span configuration: 2 × 15 m
* Instrumented middle T-girder
* Tiltmeters located at:

  * x = 11 m
  * x = 19 m

### Dataset

* 253 daily observations
* February–October 2024
* Four loading phases
* Temperature and tilt measurements
* FEM-generated reference slopes, deflections, and loads

---

## Repository Structure

### FEM_Baseline_notebook.ipynb

Generates the finite element (FEM) baseline used throughout the study, including:

* Full-field slope reconstruction
* Full-field deflection reconstruction
* Daily distributed load estimation

The FEM results serve as the reference solution for validating all PCNN models.

---

### AR_Predictive_Model_Notebook.ipynb

Implements an AR(1) cross-sensor predictive model for next-day Tilt-X forecasting.

Features include:

* Cross-sensor coupling
* Temperature effects
* Phase-dependent loading
* Ridge regression regularization
* Bias correction

The model predicts future sensor responses used as input to the AR-PCNN framework.

---

### SPTF_PCNN_Notebook.ipynb

Implements the Constant-EI Physics-Constrained Neural Network (CEI-PCNN) using a:

**SPTF – Single Polynomial Trial Function**

Features:

* Single neural network for the full beam
* Hard enforcement of primary boundary conditions
* PDE-constrained training
* Distributed load identification

---

### PPTF_PCNN_Notebook.ipynb

Implements the CEI-PCNN using:

**PPTF – Piecewise Polynomial Trial Functions**

Features:

* Separate trial functions for each span
* Span-specific boundary condition enforcement
* Hard enforcement of all boundary conditions
* Continuity constraints across the interior support

---

### PETF_PCNN_Notebook.ipynb

Implements the CEI-PCNN using:

**PETF – Pretrained EnvelopeNet Trial Function**

Features:

* Neural-network-based trial function
* EnvelopeNet pretraining
* Fourier feature encoding
* Smooth representation of span behavior
* Physics-constrained reconstruction

---

### AR_PCNN_Notebook.ipynb

Implements the complete AR-PCNN framework by combining:

1. AR-based next-day Tilt-X prediction
2. Physics-constrained full-field reconstruction

Workflow:

```text
Measured Data
      ↓
AR Prediction
      ↓
Predicted Tilt-X
      ↓
Trained PCNN
      ↓
Full-Field Slope & Deflection Prediction
```

This notebook provides future structural response prediction beyond the measured period.

---

### outputs/

Contains generated outputs from the notebooks, including:

* Reconstructed slopes
* Reconstructed deflections
* Predicted sensor responses
* Identified distributed loads
* Figures and plots
* CSV exports

---

## Methodology

The PCNN framework incorporates:

* Euler–Bernoulli beam theory
* Physics-constrained trial functions
* Automatic differentiation
* Distributed load identification
* Fourier feature encoding
* Boundary condition enforcement
* Continuity constraints at interior supports

Loss functions include:

* Data loss
* PDE residual loss
* Continuity loss
* Boundary-condition loss (where applicable)

---

## Validation

Model predictions are validated against FEM reconstructions of:

* Slope
* Deflection
* Distributed loading

Validation locations include:

* x = 5 m
* x = 10 m
* x = 20 m
* x = 25 m

Performance is assessed using:

* R²
* RMSE
* MAE
* MAPE
* Bias
* Pearson correlation coefficient

---

## Requirements

Main dependencies include:

* Python 3.10+
* PyTorch
* NumPy
* Pandas
* SciPy
* Scikit-learn
* Matplotlib
* Jupyter Notebook

Install dependencies using:

```bash
pip install -r requirements.txt
```

---

## Usage

Run the notebooks sequentially from top to bottom.

Recommended workflow:

1. Generate the FEM baseline
2. Train the AR predictive model
3. Train the SPTF model
4. Train the PPTF model
5. Train the PETF model
6. Train and evaluate the AR-PCNN framework
7. Compare results against FEM reference solutions

---

## Research Areas

* Structural Health Monitoring (SHM)
* Physics-Constrained Machine Learning
* Physics-Informed Neural Networks (PINNs)
* Bridge Monitoring
* Smart Infrastructure
* Digital Twins

---

## License

This repository is provided for academic and research purposes.
