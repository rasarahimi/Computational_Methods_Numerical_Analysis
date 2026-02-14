
# Time Integration of Linear Dynamical Systems

This repository presents a numerical study of time integration methods for linear dynamical systems, developed within the scope of the course *Computational Methods in Materials Science and Complex Systems*.

The problem is formulated in the context of classical mechanics and focuses on the dynamic response of a multi-degree-of-freedom system.

---

## Physical Problem Description

The system under consideration is a one-dimensional mechanical model consisting of **three point masses connected by linear springs**. Each mass is free to move along a single axis, and the springs obey Hooke’s law.

The governing equations are a set of coupled second-order ordinary differential equations derived from Newton’s second law:

- Masses are assumed to be identical
- Springs are linear and massless
- No external forcing or damping is applied

The objective is to compute the **time evolution of positions and velocities** of all masses given an initial displacement and velocity configuration.
        <img width="947" height="225" alt="image" src="https://github.com/user-attachments/assets/681f673a-2d07-4682-9965-e25834ed24e5" />


---

## Mathematical Formulation

The system of second-order equations is rewritten in **state-space form** by defining the state vector:

r = [x₁, x₂, x₃, v₁, v₂, v₃]ᵀ

This allows the equations of motion to be expressed as a first-order linear system:

dr/dt = A r

where A is the system matrix containing the stiffness and mass relations.

---

## Numerical Methods

Two different time integration approaches are implemented and compared:

### 1. Velocity Verlet Integration
Velocity Verlet is an explicit time-stepping method widely used in computational mechanics and molecular dynamics. It advances positions and velocities sequentially using local acceleration information and is conditionally stable depending on the time step size.

### 2. Time Evolution Operator (Matrix Exponential)
For linear systems, the exact solution can be written using the matrix exponential:

r(t) = exp(A*t) r(0)

This method provides an analytical time evolution for the state vector and serves as a reference solution for comparison with the numerical integration scheme.

---

## Implementation Details

- The system is implemented in Python using NumPy and SciPy
- Time histories of positions and velocities are computed for both methods
- Jupyter Notebook is used for numerical experiments and visualization
- The same initial conditions are used for both approaches to ensure consistency

---

## Results and Comparison

### Position Evolution (Velocity Verlet)
 <img width="679" height="455" alt="image" src="https://github.com/user-attachments/assets/1d0b8a45-6a60-4a90-bfb1-577bb096cd50" />


### Position Evolution (Matrix Exponential)
<img width="789" height="455" alt="image" src="https://github.com/user-attachments/assets/f5b6eed4-c8e8-465e-9c82-cb501b782f07" />


### Velocity Evolution (Velocity Verlet)
  <img width="684" height="455" alt="image" src="https://github.com/user-attachments/assets/ec1a0756-90bb-4408-9886-596a56f3fd42" />


### Velocity Evolution (Matrix Exponential)
<img width="795" height="455" alt="image" src="https://github.com/user-attachments/assets/9c3d678e-555d-4a7f-abf3-36b13987eacb" />


The comparison demonstrates that:
- The matrix exponential method reproduces the exact solution for the linear system
- The Velocity Verlet method closely approximates the analytical solution for sufficiently small time steps
- Differences between the two methods highlight numerical integration error and time-step sensitivity

---

## Remarks

This repository illustrates the relationship between numerical time integration schemes and analytical solutions for linear dynamical systems. It emphasizes the importance of state-space formulation, algorithm selection, and numerical accuracy in computational mechanics.

The implementation is intended both as a learning exercise and as a reusable refer
