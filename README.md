# Heat-equation-numerical-methods
Numerical solution of the heat equation using Crank-Nicolson and Spectral methods, with accuracy, convergence, and computational performance analysis


## Overview

This repository provides a modern Python reimplementation of the numerical experiments presented in our 2020 publication, "On the Numerical Solutions of a One-Dimensional Heat Equation: Spectral and Crank-Nicolson Method."

The project compares the Chebyshev spectral method and the Crank-Nicolson method for solving the one-dimensional heat equation, focusing on numerical accuracy, convergence behavior, and computational performance.


## Problem Formulation

We consider the one-dimensional heat equation

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

