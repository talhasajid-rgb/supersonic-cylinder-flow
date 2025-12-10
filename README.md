# Supersonic Flow Around a Circular Cylinder  
### Numerical Study Using OpenFOAM & ANSYS Fluent

This repository presents a computational fluid dynamics (CFD) investigation of **2D inviscid supersonic flow** around a circular cylinder at freestream Mach numbers **1.7** and **3.0**. Both a commercial solver (**ANSYS Fluent**) and an open-source solver (**OpenFOAM**) are used to analyze bow shock formation, shock standoff distance, and wake development. Numerical predictions are compared with the theoretical model of **Sinclair & Cui (2017)**.


##  Project Overview

This work was completed as part of the *Modeling with Open Source Software* course at Skoltech. The study focuses on:

- **Dual-Solver Implementation**: ANSYS Fluent (commercial) and OpenFOAM (open-source)
- **Supersonic Flow Regimes**: Mach 1.7 and Mach 3.0
- **Governing Equations**: 2D inviscid **Euler equations**
- **Validation Goal**: Compare CFD results with the theoretical model of Sinclair & Cui (2017)

The simulations capture key high-speed aerodynamic features including the detached bow shock, stagnation region, subsonic pocket, and compressible wake.


##  Objectives

1. Reproduce the numerical setup described in Sinclair & Cui (2017)  
2. Solve the 2D compressible inviscid Euler equations using two independent solvers  
3. Predict the **shock standoff distance** for M = 1.7 and M = 3.0  
4. Compare ANSYS Fluent and OpenFOAM numerical performance  
5. Validate CFD predictions against theoretical and analytical results  


## 📁 Repository Structure
Supersonic-Cylinder-Flow/
│
├── OpenFOAM/
│ ├── 0/ → Initial conditions (U, p, T, rho, etc.)
│ ├── constant/ → Mesh + physical properties
│ │ └── polyMesh/ → boundary, faces, points, owner, neighbour
│ └── system/ → controlDict, fvSchemes, fvSolution
│
├── Report_Talha.pdf → Full technical report
├── figures/ (optional) → Contours of velocity, pressure, density, etc.
└── README.md → Project documentation


---

## ANSYS Fluent Numerical Setup

Although Fluent case/data files are not included, the complete simulation setup is documented for reproducibility.

### **Solver Settings**
| Setting | Value |
|--------|--------|
| Solver type | Density-based |
| Temporal scheme | Implicit |
| Flux scheme | Roe Flux-Difference Splitting (Roe–FDS) |
| Spatial discretization | Second-order upwind |
| CFL number | 0.5 |
| Time-step size | 1×10⁻⁵ s |
| Iterations per time step | 20 |
| Total iterations | 1000 |

---

### **Boundary Conditions**
| Patch | Type | Description |
|-------|------|-------------|
| **Inlet** | Velocity-Inlet | Mach = 1.7 or 3.0 |
| **Cylinder Wall** | Slip Wall | Inviscid, no penetration |
| **Outlet** | Pressure-Outlet | Back pressure = p∞ |
| **Farfield** | Pressure Far-Field | Freestream Mach, T∞, p∞ |

---

### **Computational Mesh**

- Fully **structured** grid  
- Domain size: **40 cm × 20 cm**  
- Cylinder diameter: **3 cm**  
- Mesh refined near the cylinder to resolve shock curvature  
- Smooth stretching toward outer boundaries  

---

##  OpenFOAM Case Setup

The OpenFOAM solver configuration mirrors the Fluent setup:

- **Inviscid Euler solver (`shockFluid`)**
- **van Leer limiter reconstruction**
- **Least-squares gradients**
- **Explicit Euler time stepping**
- **Courant number control**

All files needed to run the OpenFOAM case are available in:
OpenFOAM/0/
OpenFOAM/constant/
OpenFOAM/system/

---

##  Technical Report

A full report describing the methodology, theory, numerical implementation, and results is included:

📎 **Report_Talha.pdf**

It contains:

- Governing equations  
- Numerical scheme details  
- Mesh/time-step sensitivity  
- Velocity, pressure, temperature, and density contours  
- Shock standoff-distance calculations  
- Comparison with theoretical predictions  

---

##  Author

**Talha Sajid**  
MSc Applied Computational Mechanics  
Skolkovo Institute of Science and Technology (Skoltech)

---


