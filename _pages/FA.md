---
title: "Functional Analysis for Mechanics"
permalink: /FA/
author_profile: true
---

A course on Functional Analysis with a focus on its application to the Finite Element Method and Density Functional Theory.

## Contents

1. [References](#references)
2. [Fundamental properties](#fundamental-properties)
3. [Hilbert Spaces](#hilbert-spaces)

## References

As references, I recommend:

$\color{yellow}{\star}$ [*Analysis*](https://bookstore.ams.org/view?ProductCode=GSM/14.R), EH Lieb & M Loss

$\color{yellow}{\star}$ [*Applied Functional Analysis*](https://www.taylorfrancis.com/books/mono/10.1201/9781315119489/applied-functional-analysis-tinsley-oden-leszek-demkowicz), JT Oden & L Demkowicz

$\color{yellow}{\star}$ [*Functional Analysis*](https://www.youtube.com/watch?v=OonaUALrKUk&list=PLo4jXE-LdDTTIIIRwqK35CbFJieSJEcVR), Claudio Landim Landim

<details markdown="1" id="fundamental-properties">
<summary><strong>Fundamental properties</strong></summary>

In what follows, we will prove certain properties by considering the field of complexes $\mathbb{C}$; the case for real numbers follows immediately.

$\color{Teal}{\textbf{Def 2.1}}$ **Inner product**. Let $X$ be a linear space with field $\mathbb{C}$, a map $\langle \cdot , \cdot \rangle: X \times X \mapsto \mathbb{C}$ is an inner product if:

- **Linearity:** $\langle \alpha x +y,z \rangle=\alpha \langle x,z \rangle+\langle y,z \rangle \quad \forall \alpha \in \mathbb{C}, \forall x,y,z \in X$
- **Conjugate symmetry:** $\langle x,y \rangle=\overline{\langle y,x \rangle} \quad \forall x,y \in X$
- **Positivity:** $\langle x,x \rangle>0 \quad \forall x \neq 0$

---

$\color{Teal}{\textbf{Property 2.2}}$ **Schwarz Inequality** $\vert \langle x,y \rangle \vert \leq \lVert x \rVert \lVert y \rVert$

<details markdown="1">
<summary><strong>Proof</strong></summary>

For any $t \in \mathbb{R}$ and $\hat{x} \in X$, positivity of the inner product gives:

$$\langle \hat{x}+ty, \hat{x}+ty \rangle = t^2 \langle y,y \rangle + 2t\,\text{Re}\langle \hat{x},y \rangle + \langle \hat{x},\hat{x} \rangle \geq 0$$

This is a quadratic in $t$ that is non-negative for all $t \in \mathbb{R}$, so its discriminant must satisfy:

$$\left(\text{Re}\langle \hat{x},y \rangle\right)^2 \leq \langle \hat{x},\hat{x} \rangle \langle y,y \rangle$$

hence:

$$\text{Re}\langle \hat{x},y \rangle \leq \sqrt{\langle \hat{x},\hat{x} \rangle \langle y,y \rangle}$$

Since this holds for any $\hat{x} \in X$, we take $\hat{x} = e^{-i\theta}x$ where $\theta = \arg\langle x,y \rangle$. Then:

$$\text{Re}\left[e^{-i\theta}\langle x,y \rangle\right] = \text{Re}\left[\lvert \langle x,y \rangle \rvert e^{i\theta} e^{-i\theta}\right] = \lvert \langle x,y \rangle \rvert$$

and $\langle \hat{x},\hat{x} \rangle = \langle e^{-i\theta}x, e^{-i\theta}x \rangle = \langle x,x \rangle$, so substituting:

$$\lvert \langle x,y \rangle \rvert \leq \sqrt{\langle x,x \rangle \langle y,y \rangle} = \lVert x \rVert \lVert y \rVert \qquad \square$$

</details>

---

$\color{Teal}{\textbf{Property 2.3}}$ **Triangle Inequality** $\lVert x+y \rVert \leq \lVert x \rVert + \lVert y \rVert$

<details markdown="1">
<summary><strong>Proof</strong></summary>

We start from:

$$\lVert x+y \rVert = \sqrt{\lVert x \rVert^2 + 2\,\text{Re}\langle x,y \rangle + \lVert y \rVert^2} \leq \sqrt{\lVert x \rVert^2 + 2\lvert \langle x,y \rangle \rvert + \lVert y \rVert^2}$$

Applying the Schwarz Inequality $\lvert \langle x,y \rangle \rvert \leq \lVert x \rVert \lVert y \rVert$:

$$\leq \sqrt{\lVert x \rVert^2 + 2\lVert x \rVert \lVert y \rVert + \lVert y \rVert^2} = \sqrt{(\lVert x \rVert + \lVert y \rVert)^2} = \lVert x \rVert + \lVert y \rVert \qquad \square$$

</details>

---

$\color{Teal}{\textbf{Property 2.4}}$ **The inner product induces a norm** $\lVert x \rVert = \sqrt{\langle x,x \rangle}$

<details markdown="1">
<summary><strong>Proof</strong></summary>

We need to verify the three axioms of a norm:

1. **Positivity:** By the positivity of the inner product, $\langle x,x \rangle > 0$ for all $x \neq 0$, hence $\lVert x \rVert = \sqrt{\langle x,x \rangle} \geq 0$, with equality if and only if $x = 0$.

2. **Homogeneity:** For any $\alpha \in \mathbb{C}$:

$$\lVert \alpha x \rVert = \sqrt{\langle \alpha x, \alpha x \rangle} = \sqrt{\alpha \bar{\alpha} \langle x,x \rangle} = \lvert \alpha \rvert \lVert x \rVert$$

3. **Triangle inequality:** By Property 2.3:

$$\lVert x+y \rVert \leq \lVert x \rVert + \lVert y \rVert \qquad \square$$

</details>

---

$\color{Teal}{\textbf{Property 2.5}}$ **Parallelogram Identity**. $\lVert x+y \rVert^2 + \lVert x-y \rVert^2 = 2(\lVert x \rVert^2 + \lVert y \rVert^2)$

<details markdown="1">
<summary><strong>Proof</strong></summary>

Expanding both terms using the inner product:

$$\lVert x+y \rVert^2 = \langle x+y, x+y \rangle = \lVert x \rVert^2 + 2\,\text{Re}\langle x,y \rangle + \lVert y \rVert^2$$

$$\lVert x-y \rVert^2 = \langle x-y, x-y \rangle = \lVert x \rVert^2 - 2\,\text{Re}\langle x,y \rangle + \lVert y \rVert^2$$

Adding both expressions the cross terms cancel:

$$\lVert x+y \rVert^2 + \lVert x-y \rVert^2 = 2\lVert x \rVert^2 + 2\lVert y \rVert^2 = 2(\lVert x \rVert^2 + \lVert y \rVert^2) \qquad \square$$

</details>

</details>
---

<details markdown="1" id="hilbert-spaces">
<summary><strong>Hilbert Spaces</strong></summary>

$\color{Teal}{\textbf{Definition 3.1}}$ **Hilbert space**. Linear space $X$ endowed with an inner product $\langle , \rangle \mapsto \lVert \rVert$ wich is complete on its norm.

$\color{Teal}{\textbf{Definition 3.2}}$ **Ortogonal space**. Let $Y \subseteq X$ be a linear subset; the orthogonal space is represented as $Y^\perp=\left\lbrace x \in X: \langle x,y \rangle=0 \forall y \in Y \right\rbrace$

$\color{Teal}{\textbf{Properties 3.3}}$ If $X$ is a Hilbert space over $\mathbb{C}$ and $Y \subseteq X$ is a closed subspace, the following properties are verified:

1. $Y^\perp$ is also a closed linear subspace.
2. $X=Y \oplus Y^\perp$, which means that for every $x \in X$ there exist unique elements $y \in Y$ and $y^\perp \in Y^\perp$ such that $x=y+y^\perp$, with $Y \cap Y^\perp=\left\lbrace 0 \right\rbrace$.
3. $\left( Y^\perp \right)^\perp=Y$.

<details markdown="1">
<summary><strong>Proof</strong></summary>

1) To show that $Y^\perp$ is closed, consider a sequence $(x_n) \subset Y^\perp$ that converges to $x \in X$. For any fixed $y \in Y$, we have $\langle x_n, y \rangle = 0$ for all $n$. By continuity of the inner product, it follows that:
  $$ \langle x,y \rangle = \lim_{n \to \infty} \langle x_n, y \rangle = 0. $$
Since $y \in Y$ was arbitrary, we get $x \in Y^\perp$. Hence $Y^\perp$ is closed.

2) First, note that $Y \cap Y^\perp = \{0\}$, since if $z \in Y \cap Y^\perp$, then $\langle z, z \rangle = 0$, so $z=0$.

Now, let $x \in X$ be fixed. Since $Y$ is closed and convex, there exists $y_0 \in Y$ such that $\|x - y_0\| = \operatorname{dist}(x, Y)$ (the infimum is attained). We claim that $x - y_0 \in Y^\perp$. Define $v := x - y_0$. Take any $z \in Y$ and any real $t \in \mathbb{R}$. Since $Y$ is a linear subspace, $y_0 + tz \in Y$, and by the minimality of $y_0$,
  $$ \|v\|^2 \le \|v - tz\|^2 = \|v\|^2 - 2t \,\operatorname{Re}\langle v, z \rangle + t^2 \|z\|^2. $$
Hence, for all $t \in \mathbb{R}$,
  $$ 0 \le -2t \,\operatorname{Re}\langle v, z \rangle + t^2 \|z\|^2. $$
If $t > 0$, dividing by $t$ and letting $t \to 0^+$ yields $\operatorname{Re}\langle v, z \rangle \le 0$. If $t < 0$, dividing by $t$ (which reverses the inequality) and letting $t \to 0^-$ yields $\operatorname{Re}\langle v, z \rangle \ge 0$. Therefore $\operatorname{Re}\langle v, z \rangle = 0$.

Since $z \in Y$ was arbitrary and $Y$ is a complex subspace, we also have $i z \in Y$. Applying the previous result to $i z$ gives:
  $$ \operatorname{Re}\langle v, i z \rangle = 0. $$
Using the linearity in the first argument of the inner product, $\langle v, i z \rangle = i \langle v, z \rangle$, so:
  $$ \operatorname{Re}(i \langle v, z \rangle) = 0 \implies -\operatorname{Im}\langle v, z \rangle = 0 \implies \operatorname{Im}\langle v, z \rangle = 0. $$
Thus both the real and imaginary parts of $\langle v, z \rangle$ are zero, which means $\langle v, z \rangle = 0$ for all $z \in Y$. Hence $v = x - y_0 \in Y^\perp$.

Define $y^\perp := v$. Then $y^\perp \in Y^\perp$ and $x = y_0 + y^\perp$, proving the existence of the decomposition.

To prove uniqueness, suppose $x = y_1 + y_1^\perp = y_2 + y_2^\perp$ with $y_1, y_2 \in Y$ and $y_1^\perp, y_2^\perp \in Y^\perp$. Then $y_1 - y_2 = y_2^\perp - y_1^\perp$. The left-hand side belongs to $Y$, while the right-hand side belongs to $Y^\perp$. Hence both sides lie in $Y \cap Y^\perp = \{0\}$. Thus $y_1 = y_2$ and $y_1^\perp = y_2^\perp$.

3) First, $Y \subseteq (Y^\perp)^\perp$ is immediate from the definition. Conversely, let $x \in (Y^\perp)^\perp$. By (2), write uniquely $x = y + y^\perp$ with $y \in Y$ and $y^\perp \in Y^\perp$. Since $x \in (Y^\perp)^\perp$ and $y^\perp \in Y^\perp$, we have:
  $$ 0 = \langle x, y^\perp \rangle = \langle y + y^\perp, y^\perp \rangle = \langle y, y^\perp \rangle + \langle y^\perp, y^\perp \rangle = 0 + \|y^\perp\|^2. $$
Hence $y^\perp = 0$, so $x = y \in Y$. Therefore $(Y^\perp)^\perp \subseteq Y$, and we conclude $(Y^\perp)^\perp = Y$.

</details>
</details>



