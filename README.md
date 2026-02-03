# Structural Validation of Composite Materials for Formula Student Applications

**Mohamed Becha**  
Engineering Project — EPFL Racing Team  
École Polytechnique Fédérale de Lausanne  

---

## Overview

This project focuses on the **structural validation of composite materials** used in Formula Student aerodynamic components.

The objective was to verify the mechanical properties of carbon fiber laminates (Twill 200 gsm) through:

- Finite Element simulations (Abaqus)
- Mechanical testing (traction, bending, shear)
- Comparison between numerical and experimental results

Full report available in `report.pdf`.

---

# 1. Finite Element Method (FEM) Formulation

The structural problem is governed by the equilibrium equation:

$$
divergence(\sigma(\mathbf{x})) + \mathbf{f}(\mathbf{x}) = 0
$$

Using generalized Hooke’s law:

$$
\sigma(\mathbf{x}) = \mathbf{C}(\mathbf{x}) \varepsilon(\mathbf{x})
$$

The weak form leads to the linear system:

$$
\mathbf{K}\mathbf{q} = \mathbf{r}
$$

where:

- $\mathbf{K} = \int_\Omega \mathbf{B}^T \mathbf{C} \mathbf{B}\, d\Omega$  
- $\mathbf{r} = \int_\Omega \mathbf{H}^T \mathbf{f}\, d\Omega + \int_{\partial \Omega_\sigma} \mathbf{H}^T \mathbf{t}\, dS$  

Shell composite elements were used to model thin laminate specimens.

---

# 2. Composite Material Modeling

Material: **Carbon Fiber Twill 200 gsm**

Orthotropic elastic properties:

| Property | Value |
|----------|-------|
| $E_x$ | 60.4 GPa |
| $E_y$ | 60.4 GPa |
| $G_{xy}$ | 4.27 GPa |
| $\nu_{xy}$ | 0.35 |

The laminate was modeled with layered shell elements and appropriate fiber orientations.

---

## Rule of Mixtures (Longitudinal Loading)

$$
E_{\text{long}} = E_f V_f + E_m V_m
$$

## Transverse Loading

$$
E_{\text{trans}} =
\frac{E_f E_m}{V_m E_f + V_f E_m}
$$

---

# 3. Failure Criterion — Tsai–Hill

Since composite laminates are anisotropic, the Tsai–Hill failure criterion was used:

$$ I = \left(\frac{\sigma_L}{X}\right)^2 +
\left(\frac{\sigma_T}{Y}\right)^2 +
\left(\frac{\tau}{S}\right)^2 -
\frac{\sigma_L \sigma_T}{X^2}
$$

Failure occurs when:

$$
I \ge 1
$$

---

# 4. Mechanical Tests Modeled

## 4.1 Tensile Test (ASTM D3039)

Specimen modeled as a composite shell.

Stress in bending:

$$
\sigma = \frac{3 P L}{2 b h^2}
$$

Flexural modulus:

$$
E_F = \frac{P L^3}{4 b h^3 \delta}
$$

---

## 4.2 Three-Point Bending

Maximum stress:

$$
\sigma = \frac{3 P L}{2 b h^2}
$$

Deflection:

$$
\delta = \frac{P L^3}{48 E I}
$$

---

## 4.3 Four-Point Bending

Maximum stress:

$$
\sigma = \frac{3 P L}{4 b h^2}
$$

---

## 4.4 Shear Testing

Two methods evaluated:

- ±45° tensile laminate
- V-notched rail shear test (ASTM D7078)

---

# 5. Mesh Convergence Study

A convergence analysis was conducted by varying element size.

The Tsai–Hill index converged toward approximately:

$$
I \approx 0.86
$$

The selected mesh provided stable stress and strain predictions while remaining computationally efficient.

---

# 6. Results

- Longitudinal tensile failure predicted at ≈ 24 kN
- Previous dataset overestimated the Twill 200 gsm properties

---

# Engineering Takeaways

- Importance of validating supplier data for infusion-based laminates
- Sensitivity of composite behavior to fiber orientation
- Necessity of mesh convergence for nonlinear failure criteria
- Difference between idealized FEM assumptions and real experimental constraints

---

# Repository Contents

- `report.pdf` — Complete technical report
- `figures/` — Key FEM and experimental visualizations

---

# Tools Used

- Abaqus (FEM simulation)
- ASTM D3039, D7264, D7078 standards
- Composite laminate theory
- Tsai–Hill failure modeling

---

For academic or engineering inquiries, feel free to contact me.
