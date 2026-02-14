# Computational Methods — Numerical Analysis (Python)

This repository collects my Python implementations and numerical experiments developed for **MSN 514: Computational Methods for Materials Science and Complex Systems** (Bilkent University).

The goal of this repository is to document and present key numerical methods in a clean, reproducible, and portfolio-grade format. Each topic is organized as a self-contained mini-project with:
- a Jupyter notebook implementation (`.ipynb`)
- exported figures (plots) for quick inspection
- a short project README explaining the physics/mathematics, methods, and main results

---

## Contents

### 1) Time Integration of Linear Dynamical Systems  
**Folder:** `time-integration/`

A numerical study of time integration methods for a multi-degree-of-freedom mechanical system (three-mass spring model). The project compares:
- **Velocity Verlet integration** (explicit time stepping)
- **Time evolution operator / matrix exponential** (state-space formulation)

Main outputs include position/velocity time histories and a comparison between numerical and analytical evolution for linear systems.

---

### 2) Numerical Differentiation: Finite Differences vs Spectral Methods  
**Folder:** `numerical-differentiation/`

A comparative study of numerical differentiation methods for a smooth **periodic** function on a uniform grid. The project includes:
- **Centered finite difference stencils** (3, 5, 7, 9 points) for first and second derivatives
- **DFT differentiation matrix** (explicit DFT-based operator)
- **FFT-based differentiation** using NumPy’s FFT

Main outputs include:
- log–log error vs grid size **N**
- log–log runtime vs **N**
- performance investigation for **N = 2^k** (FFT efficiency)

---

## How to Run

Open the notebooks in Jupyter:

```bash
pip install -r requirements.txt
jupyter notebook
