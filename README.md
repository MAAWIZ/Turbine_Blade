# Turbine Blade: Coupled Structural & Thermal FEA

## Project Overview
This repository contains the manufacturing drawings, CAD models, and Finite Element Analysis (FEA) reports for a high-performance Ti-6Al-4V turbine blade [cite: 1, 2]. The project demonstrates the application of geometric dimensioning and tolerancing (GD&T) [cite: 2] alongside multi-physics simulation using ANSYS [cite: 1].

## Engineering Specifications
* **Component:** Ti-Turbine Blade [cite: 2]
* **Material:** Ti-6Al-4V (Titanium Alloy) [cite: 1, 2]
* **Surface Finish:** Titanium Aluminum Nitride (TiAlN) Coating via PVD [cite: 2]
* **Drafting Standard:** ASME Y14.5-2018 [cite: 2]

## Simulation Setup (ANSYS 2025 R2 Student)
The analysis consists of a 5-second transient simulation [cite: 1], broken into two coupled systems:
1.  **Transient Thermal:** Evaluates the blade's thermal response to a $40^{\circ}\text{C}$ ambient environment with a convective film coefficient of $1550 \text{ W/m}^2\text{C}$ [cite: 1]. 
2.  **Transient Structural:** Applies a transient pressure load ramping to $1300 \text{ Pa}$ over 5 seconds, mapping the thermal body temperatures directly into the structural solver [cite: 1].

## Key Results
* **Maximum Equivalent Stress:** $14.22 \text{ MPa}$ [cite: 1]
* **Maximum Total Deformation:** $0.785 \text{ mm}$ [cite: 1]
* **Maximum Temperature:** $71.747^{\circ}\text{C}$ [cite: 1]

## Current Status & Future Work
* **Mesh Refinement:** The current global mesh (7,690 elements) [cite: 1] will be optimized using symmetry sectioning to remain within Student edition node limits while increasing local accuracy at the blade roots.
* **Unit Scaling Revision:** The initial geometry import experienced a scale translation error (mm to meters), resulting in an artificially inflated bounding box [cite: 1, 2]. Future commits will correct the base scale factor to resolve mass matrix discrepancies.
