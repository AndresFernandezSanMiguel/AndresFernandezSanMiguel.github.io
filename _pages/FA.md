---
title: "Functional Analysis for Mechanics"
permalink: /FA/
author_profile: true
---

A course on functional analysis with a focus on its application to the Finite Element Method and Density Functional Theory. 

## Contents

1. [References](#references)
2. [Fundamental Properties](#fundamental-properties)

## References

As references, I recommend:

$$\color{yellow}\star$$ [*Analysis*](https://bookstore.ams.org/view?ProductCode=GSM/14.R), EH Lieb $$\&$$ M Loss 

$$\color{yellow}\star$$ [*Applied Functional Analysis*](https://www.taylorfrancis.com/books/mono/10.1201/9781315119489/applied-functional-analysis-tinsley-oden-leszek-demkowicz), JT Oden $$\&$$ L Demkowicz 

$$\color{yellow}\star$$ [*Functional Analysis*](https://www.youtube.com/watch?v=OonaUALrKUk&list=PLo4jXE-LdDTTIIIRwqK35CbFJieSJEcVR), Claudio Landim Landim

## Fundamental properties

In what follows, we will prove certain properties by considering the field of complexes $$\mathbb{C}$$; 
the case for real numbers follows immediately.

**Def 2.1 Inner product**.  Let $$X$$ be a linear space with field $$\mathbb{C}$$, a map $$\langle , \rangle: X \times X \mapsto \mathbb{C}$$
if:

- **Linearity:** $$\langle \alpha x +y,z \rangle=\alpha \langle x,y \rangle+\langle y,z \rangle \forall \alpha \in \mathbb{C}, \forall x,y,z \in \mathbb{X}$$
- **Conjugate symmetry:** $$\langle x,y \rangle=\overline{\langle y,x \rangle} \forall x,y \in \mathbb{X}$$
- **Positivity:** $$\langle x,x \rangle>0 \forall x \neq 0$$
 
**Property 2.2 Schwartz Inequality** $$\vert \langle x,y \rangle \vert \leq \lVert x \rVert \lVert y \rVert$$

<details>
<summary><strong>Proof</strong></summary>

Given the properties of the inner product, the following holds:

$$
\langle \hat{x}+ty,\hat{x}+ty \rangle=t^2 \langle y,y \rangle+2t\text{Re} \langle x,y \rangle+\langle \hat{x},\hat{x} \rangle \geq 0
$$

which holds if the discriminant satisfies:

$$
\text{Re} \langle \hat{x},y \rangle \leq \sqrt{\langle \hat{x},\hat{x} \rangle \langle y,y \rangle}
$$

since it holds for any  $$\hat{x} \in X$$ when taking $$\hat{x}=e^{-i \theta} x $$, we obtain that:

$$
\text{Re} \left[ e^{-i \theta}\langle x,y \rangle \right] \leq \langle x,x \rangle \langle y,y \rangle
$$

But since every complex number has the following property:

$$
\langle x,y \rangle=\lvert \langle x,y \rangle \rvert e^{i \theta}
$$

then the property holds $$\square$$


</details>
