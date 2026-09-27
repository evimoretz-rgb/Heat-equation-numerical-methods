# Heat-equation-numerical-methods
Numerical solution of the heat equation using Crank-Nicolson and Spectral methods, with accuracy, convergence, and computational performance analysis


## Overview

This repository provides a modern Python reimplementation of the numerical experiments presented in our 2020 publication, "On the Numerical Solutions of a One-Dimensional Heat Equation: Spectral and Crank-Nicolson Method."

The project compares the Chebyshev spectral method and the Crank-Nicolson method for solving the one-dimensional heat equation, focusing on numerical accuracy, convergence behavior, and computational performance.


## Problem Formulation

We consider the one-dimensional heat equation

```math
\frac{\partial u}{\partial t}
-
\frac{\partial^2 u}{\partial x^2}
= 0,
\qquad -1 < x < 1,\quad t \geq 0.
```

The Dirichlet boundary conditions are

```math
u(-1,t)=u(1,t)=0,
```

with the initial condition

```math
u(x,0)=\sin(\pi x).
```

For validation of the numerical methods, the exact solution is

```math
u(x,t)=e^{-\pi^2 t}\sin(\pi x).
```

## Numerical Methods

Two numerical methods are implemented and compared in this project:

1. **Chebyshev Spectral Method**
2. **Crank–Nicolson Method**

The numerical solutions are compared with the exact solution in terms of accuracy, convergence behavior, and computational performance.

### Chebyshev Spectral Method

The spectral method approximates the solution using Chebyshev polynomials. The spatial approximation can be written as

```math
u(x) \approx \sum_{k=0}^{N} \tilde{u}_k T_k(x),
\qquad x \in [-1,1].
```

The Chebyshev polynomials are defined by

```math
T_k(x)=\cos\left(k\cos^{-1}(x)\right).
```

The Chebyshev–Gauss–Lobatto collocation points are

```math
x_j=\cos\left(\frac{j\pi}{N}\right),
\qquad j=0,1,\ldots,N.
```

