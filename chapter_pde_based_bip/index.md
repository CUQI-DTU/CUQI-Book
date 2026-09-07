---
numbering:
  equation:
    continue: false
---

(pde-bip)=
# Chapter 13: PDE-based BIP

In this chapter, we discuss solving PDE-based BIPs in CUQIpy. We illustrate this through two examples. The first one uses CUQIpy library to set up and solve a heat equation-based BIP. The second example uses the [CUQIpy-FEniCS plugin](https://github.com/CUQI-DTU/CUQIpy-FEniCS) to interface CUQIpy with [FEniCS](https://fenicsproject.org/) for modeling and solving PDEs using the finite element method. The latter example sets up and solves a 2D Poisson equation-based BIP.