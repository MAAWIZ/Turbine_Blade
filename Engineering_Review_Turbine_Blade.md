# Engineering Design & FEA Review: Turbine Blade

**Reference Documents:** 
* `ANSYS_Report_Turbine_Blade.pdf` [cite: 1]
* `GD&T_Turbine_Blade.pdf` [cite: 2]

## 1. Executive Summary
This document reviews the transient structural and thermal finite element analysis (FEA) performed on a Ti-6Al-4V turbine blade [cite: 1, 2]. The review highlights a critical geometry scaling error during import that must be addressed before presenting these results in a professional portfolio.

## 2. Geometry and Scaling Discrepancy (CRITICAL)
* The manufacturing drawing specifies the blade's outer overall dimensions in millimeters, with an overall width of approximately 256.00 mm [cite: 2].
* The ANSYS setup indicates a bounding box length in the X-axis of 12.256 meters [cite: 1].
* Consequently, the calculated mass in the simulation is $1.0022 \times 10^6$ kg ($224.71 \text{ m}^3$ volume) [cite: 1].
* **Recommendation:** This is a standard CAD-to-ANSYS unit conversion error. The geometry must be re-imported ensuring the length unit is set to millimeters rather than meters to ensure load and stress distributions represent the physical part.

## 3. Mesh Quality and Optimization
* The current mesh consists of 14,943 nodes and 7,690 elements [cite: 1].
* For a component with complex aerodynamic curvature and thin sections (4.00 mm thickness) [cite: 2], this mesh density is too coarse to capture accurate stress concentrations.
* **Recommendation:** Operating within the node limits of the ANSYS Student version [cite: 1] requires targeted meshing. Similar to mesh optimization strategies applied to complex rotational components like brake discs, utilize geometry sectioning (e.g., analyzing a periodic sector of the hub) or apply local face sizing to the blade roots.

## 4. Boundary Conditions & Loads
### Thermal Setup
* The initial uniform temperature is set to 20 °C [cite: 1]. 
* Convection is applied across 32 faces with a film coefficient of 1550 W/m²°C and an ambient temperature of 40 °C [cite: 1]. This ambient condition provides a realistic baseline for peak summer operating environments in regions like Dubai.
* The maximum recorded temperature reached over the 5-second transient analysis was 71.747 °C [cite: 1].

### Structural Setup
* The transient structural analysis ramps up pressure from 0 Pa to 1300 Pa over 5 seconds [cite: 1].
* The maximum equivalent (von-Mises) stress reached 14.225 MPa, occurring on the solid body [cite: 1].

## 5. Material Specifications
* The drawing specifies a Titanium Aluminum Nitride Coating applied via physical vapor deposition [cite: 2]. This coating should be considered if surface thermal resistance is added in future iterations.
* The base material is Ti-6Al-4V [cite: 2]. The ANSYS material library is utilizing a generic "Titanium Alloy" with a tensile yield strength of $9.3 \times 10^8$ Pa (930 MPa) and a density of 4460 kg/m³ [cite: 1]. These properties are well-aligned with Ti-6Al-4V, but custom material cards should be defined for absolute precision.
