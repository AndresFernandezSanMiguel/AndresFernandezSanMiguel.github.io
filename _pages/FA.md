---
title: "Functional Analysis for Mechanics"
permalink: /FA/
author_profile: true
mathjax: true
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

---
title: "Functional Analysis for Mechanics"
permalink: /FA/
author_profile: true
mathjax: true
---

**Def 2.1 Inner product**. Let $$X$$ be a linear space with field $$\mathbb{C}$$,
a map $$\langle \cdot , \cdot \rangle: X \times X \mapsto \mathbb{C}$$ is an inner product if:

- **Linearity:** $$\langle \alpha x +y,z \rangle=\alpha \langle x,z \rangle+\langle y,z \rangle \quad \forall \alpha \in \mathbb{C}, \forall x,y,z \in X$$
- **Conjugate symmetry:** $$\langle x,y \rangle=\overline{\langle y,x \rangle} \quad \forall x,y \in X$$
- **Positivity:** $$\langle x,x \rangle>0 \quad \forall x \neq 0$$

---

**Property 2.2 Schwarz Inequality** $$\vert \langle x,y \rangle \vert \leq \lVert x \rVert \lVert y \rVert$$

<details>
<summary><strong>Proof</strong></summary>

For any $$t \in \mathbb{R}$$ and $$\hat{x} \in X$$, positivity of the inner product gives:

$$\langle \hat{x}+ty, \hat{x}+ty \rangle = t^2 \langle y,y \rangle + 2t\,\text{Re}\langle \hat{x},y \rangle + \langle \hat{x},\hat{x} \rangle \geq 0$$

This is a quadratic in $$t$$ that is non-negative for all $$t \in \mathbb{R}$$, so its discriminant must satisfy:

$$\left(\text{Re}\langle \hat{x},y \rangle\right)^2 \leq \langle \hat{x},\hat{x} \rangle \langle y,y \rangle$$

hence:

$$\text{Re}\langle \hat{x},y \rangle \leq \sqrt{\langle \hat{x},\hat{x} \rangle \langle y,y \rangle}$$

Since this holds for any $$\hat{x} \in X$$, we take $$\hat{x} = e^{-i\theta}x$$ where $$\theta = \arg\langle x,y \rangle$$. Then:

$$\text{Re}\left[e^{-i\theta}\langle x,y \rangle\right] = \text{Re}\left[\lvert \langle x,y \rangle \rvert e^{i\theta} e^{-i\theta}\right] = \lvert \langle x,y \rangle \rvert$$

and $$\langle \hat{x},\hat{x} \rangle = \langle e^{-i\theta}x, e^{-i\theta}x \rangle = \langle x,x \rangle$$, so substituting:

$$\lvert \langle x,y \rangle \rvert \leq \sqrt{\langle x,x \rangle \langle y,y \rangle} = \lVert x \rVert \lVert y \rVert \qquad \square$$

</details>
