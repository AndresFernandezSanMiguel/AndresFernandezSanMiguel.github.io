---
title: "Molecular Element Method"
permalink: /MEM/
author_profile: true
---

Some tutorials on the Molecular Element Method (MEM) and its application to the elastic analysis of atomic structures.

The theoretical details and recommended references are:

$$\color{yellow}\star$$ [*The Molecular Element Method (MEM): A FEM-based Formulation for Linear and Non-Linear Molecular Elasticity*](https://ruc.udc.es/entities/publication/d0df64f6-4666-431f-9fbd-0e0f903c5b06)
A. Fernández-San Miguel, I. Couceiro $$\&$$ L. Ramírez

$$\color{yellow}\star$$ [*A first order FEM-based formulation for the analysis of molecular structures with bonded interactions*](https://link.springer.com/article/10.1007/s00366-024-02085-w)
A. Fernández-San Miguel, I. Couceiro, L. Ramírez $$\&$$ F. Navarrina

## Linear Analysis

In the case of linear elasticity, given the positions of $$N$$ nuclei and the potential energy $$V: \mathbb{R}^{3N}  \mapsto \mathbb{R}$$ associated with the user's preferred classical force field, the method allows for the exact and rigorous assembly and solution of: 

$$\color{BlueGreen}\triangle$$ $$\mathbf{K} \boldsymbol{u}=\boldsymbol{f} \Leftarrow$$ Static Analysis 

$$\color{BlueGreen}\triangle$$ $$\mathbf{K} \boldsymbol{\phi}_i=\lambda_i \mathbf{M} \boldsymbol{\phi}_i \Leftarrow$$ Molecular Vibrations

where $$\mathbf{K}$$ refers to the stiffness matrix or Hessian of the system, $$\mathbf{M}$$ to the mass matrix, $$\boldsymbol{f}$$ to the vector of external forces, $$\boldsymbol{u}$$ to the global displacement vector and $$\lambda_i$$ to the eigenvalue with eigenvector $$\boldsymbol{\phi}_i$$. 

<img src="AndresFernandezSanMiguel.github.io/images/logo_sao_mod_gris.pdf">

**Tutorial 1 $$\Rightarrow$$ Theoretical background**

We present the theoretical basis for using our SAOAS code for the linear static and vibrational analysis of molecular structures.

{% include video.html id="qQOGj-ai0HU" provider="youtube" %}




