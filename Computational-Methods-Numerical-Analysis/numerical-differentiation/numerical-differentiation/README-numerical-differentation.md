# Numerical Differentiation — FD vs DFT Matrix vs FFT

This project studies numerical differentiation for a smooth **periodic** function on a uniform grid over **x ∈ [−1, 1]**.  
Three approaches are implemented and compared in terms of:

- **Accuracy vs grid size N** (log–log)
- **Runtime vs N** (log–log)
- FFT performance behavior when **N = 2^k**

---

## Problem

We consider:

f(x) = exp( ½·sin(3πx) − ¼·cos(5πx) ),  for x ∈ [−1, 1]

The objective is to compute:
- first derivative: df/dx  
- second derivative: d²f/dx²  
using multiple numerical methods, and compare against analytic expressions.

---

## Analytic derivatives (reference)


Define:

g(x) = ½·sin(3πx) − ¼·cos(5πx)  
f(x) = exp(g(x))

Then:

g'(x) = (3π/2)·cos(3πx) + (5π/4)·sin(5πx)

g''(x) = −(3π/2)²·sin(3πx) + (5π/4)²·cos(5πx)

Using:
- f'(x) = f(x)·g'(x)
- f''(x) = f(x)·( (g'(x))² + g''(x) )

Final forms:

df/dx = f(x) · [ (3π/2)·cos(3πx) + (5π/4)·sin(5πx) ]

d²f/dx² = f(x) · { [ (3π/2)·cos(3πx) + (5π/4)·sin(5πx) ]²  
                   − (3π/2)²·sin(3πx) + (5π/4)²·cos(5πx) }

---

## Methods implemented

### 1) Centered Finite Differences (FD)
Centered stencils are used for first and second derivatives with:
- 3-point, 5-point, 7-point, 9-point stencils

This family shows **algebraic convergence** with grid refinement (Δx → 0).

### 2) DFT differentiation matrix (explicit spectral operator)
A Discrete Fourier Transform (DFT) matrix is constructed explicitly and used to build:
- first-derivative operator D₁
- second-derivative operator D₂

Derivatives are computed as:
- f' ≈ D₁ f
- f'' ≈ D₂ f

This is spectrally accurate for smooth periodic functions but scales as **O(N²)**.

### 3) FFT-based spectral differentiation
Using NumPy FFT:
1) transform f → Fourier space  
2) multiply modes by (ik) for first derivative and (−k²) for second derivative  
3) inverse transform back to physical space

This preserves spectral accuracy with cost **O(N log N)** and tends to be especially fast for **N = 2^k**.


