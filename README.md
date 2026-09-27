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

### 1. Chebyshev Spectral Method

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
#### Spectral Differentiation

The spatial derivatives are approximated using Chebyshev differentiation matrices. At the collocation points, the first and second derivatives can be written as

```math
u'(x_i) \approx \sum_{j=0}^{N}(D_x)_{i,j}u(x_j),
```

and

```math
u''(x_i) \approx \sum_{j=0}^{N}(D_{xx})_{i,j}u(x_j),
```

where $(D_x)$ and $(D_{xx})$ denote the first- and second-order Chebyshev differentiation matrices, respectively.

#### Domain Transformation

Since the spatial domain is already defined on $(-1,1)$, while the time domain is not, a linear transformation is introduced to map the time interval onto the spectral domain:

```math
\tau(t)=at+b.
```

For a time interval $(t_s \leq t \leq t_e)$, the transformation satisfies

```math
\tau(t_s)=-1,
\qquad
\tau(t_e)=1.
```

Therefore,

```math
at_s+b=-1,
\qquad
at_e+b=1.
```

This transformation allows the Chebyshev spectral approximation to be applied in both the spatial and transformed time domains.


### 2. Crank–Nicolson Method

The Crank–Nicolson method discretizes both the spatial and temporal domains. Let $(h)$ denote the spatial step size and $(k)$ the time step size. The grid points are defined by

```math
x_i = ih, \qquad t_j = jk.
```

The Crank–Nicolson discretization of the one-dimensional heat equation is obtained by averaging the spatial second derivative at two consecutive time levels:

```math
\frac{u_i^{j+1}-u_i^j}{k}
-
\frac{1}{2}
\left[
\frac{u_{i+1}^{j}-2u_i^j+u_{i-1}^{j}}{h^2}
+
\frac{u_{i+1}^{j+1}-2u_i^{j+1}+u_{i-1}^{j+1}}{h^2}
\right]
=0.
```

At each time step, this formulation leads to a tridiagonal system of linear equations that is solved to obtain the numerical solution at the next time level.

## Numerical Evaluation

The numerical solutions are evaluated by comparing them with the exact solution. The maximum error is defined as

```math
E_{\max}
=
\max_{x,t}
\left|
U_{\mathrm{exact}}(x,t)
-
U_{\mathrm{numerical}}(x,t)
\right|.
```

The performance of the two numerical methods is evaluated using:

- **Maximum error** to measure numerical accuracy.
- **Convergence behavior** as the numerical resolution is increased.
- **Computation time** to evaluate computational efficiency.

For the spectral method, the numerical resolution is controlled by $N_x$ and $N_{\tau}$. For the Crank–Nicolson method, the spatial and temporal resolutions are controlled by $h$ and $k$, respectively.
