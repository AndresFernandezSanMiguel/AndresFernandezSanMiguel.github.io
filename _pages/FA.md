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
4. [Riesz Representation and Lax‑Milgram Theorems](#riesz-lax-milgram)

## References

[... el contenido existente ...]

<details markdown="1" id="fundamental-properties">
[...]
</details>

<details markdown="1" id="hilbert-spaces">
[...]
</details>

<details markdown="1" id="riesz-lax-milgram">
<summary><strong>Riesz Representation and Lax‑Milgram Theorems</strong></summary>

$\color{Teal}{\textbf{Definition 4.1}}$ **Bounded linear functional**. Let $X$ be a normed space over $\mathbb{C}$ (or $\mathbb{R}$). A linear map $\ell : X \to \mathbb{C}$ is called a **linear functional**. It is bounded if there exists a constant $C \geq 0$ such that
$$ |\ell(x)| \le C \|x\| \quad \forall x \in X. $$
The space of all bounded linear functionals on $X$ is denoted by $X^*$ and is called the **dual space** of $X$. It is a Banach space with the norm
$$ \|\ell\|_{X^*} := \sup_{x \neq 0} \frac{|\ell(x)|}{\|x\|}. $$

---

$\color{Teal}{\textbf{Theorem 4.2 (Riesz Representation Theorem)}}$ Let $H$ be a Hilbert space over $\mathbb{C}$ (or $\mathbb{R}$) with inner product $\langle \cdot, \cdot \rangle$. For every bounded linear functional $\ell \in H^*$, there exists a unique vector $y_\ell \in H$ such that
$$ \ell(x) = \langle x, y_\ell \rangle \quad \forall x \in H. $$
Moreover, $\|y_\ell\| = \|\ell\|_{H^*}$.

<details markdown="1">
<summary><strong>Proof</strong></summary>

If $\ell \equiv 0$, take $y_\ell = 0$. Assume $\ell \not\equiv 0$. Let $N = \ker \ell = \{ x \in H : \ell(x) = 0 \}$. Since $\ell$ is continuous (bounded), $N$ is a closed subspace of $H$. By the orthogonal decomposition theorem (Property 3.3), we have
$$ H = N \oplus N^\perp, \quad \text{with } N^\perp \neq \{0\}. $$
Choose $z \in N^\perp$ such that $\ell(z) = 1$ (possible because $\ell$ is not zero on $N^\perp$). For any $x \in H$, write
$$ x = \left( x - \ell(x) z \right) + \ell(x) z. $$
The first term is in $N$ since $\ell(x - \ell(x) z) = \ell(x) - \ell(x)\ell(z) = 0$. Hence,
$$ \langle x, z \rangle = \langle x - \ell(x) z, z \rangle + \ell(x) \langle z, z \rangle = \ell(x) \|z\|^2. $$
Thus
$$ \ell(x) = \left\langle x, \frac{z}{\|z\|^2} \right\rangle. $$
So $y_\ell = z / \|z\|^2$ works.

Uniqueness: if $y_1, y_2 \in H$ both represent $\ell$, then $\langle x, y_1 - y_2 \rangle = 0$ for all $x \in H$; taking $x = y_1 - y_2$ gives $y_1 = y_2$.

For the norm equality, we have
$$ \|\ell\| = \sup_{\|x\|=1} |\langle x, y_\ell \rangle| \le \|y_\ell\|, $$
and taking $x = y_\ell/\|y_\ell\|$ gives equality. $\square$

</details>

---

$\color{Teal}{\textbf{Definition 4.3}}$ **Bilinear forms and coercivity**. Let $H$ be a Hilbert space. A map $a: H \times H \to \mathbb{C}$ is a **sesquilinear form** (or bilinear if real) if it is linear in the first argument and conjugate‑linear in the second. It is:

- **bounded** if there exists $M > 0$ such that
  $$ |a(u,v)| \le M \|u\| \|v\| \quad \forall u,v \in H; $$
- **coercive** (or **elliptic**) if there exists $\alpha > 0$ such that
  $$ \operatorname{Re} a(u,u) \ge \alpha \|u\|^2 \quad \forall u \in H. $$

---

$\color{Teal}{\textbf{Theorem 4.4 (Lax‑Milgram Theorem)}}$ Let $H$ be a Hilbert space and let $a: H \times H \to \mathbb{C}$ be a bounded, coercive sesquilinear form. Then for every bounded linear functional $\ell \in H^*$, there exists a unique $u \in H$ such that
$$ a(u,v) = \ell(v) \quad \forall v \in H. $$
Moreover, the solution satisfies $\|u\| \le \frac{1}{\alpha} \|\ell\|_{H^*}$.

<details markdown="1">
<summary><strong>Proof</strong></summary>

For each fixed $u \in H$, the map $v \mapsto a(u,v)$ is a bounded linear functional on $H$. By the Riesz Representation Theorem, there exists a unique vector $T u \in H$ such that
$$ a(u,v) = \langle v, T u \rangle \quad \forall v \in H. $$
This defines an operator $T: H \to H$. We check its properties:

- **Boundedness**: for all $u \in H$,
  $$ \|T u\|^2 = |\langle T u, T u \rangle| = |a(u, T u)| \le M \|u\| \|T u\| \quad \Rightarrow \quad \|T u\| \le M \|u\|. $$
- **Coercivity**: for all $u \in H$,
  $$ \alpha \|u\|^2 \le \operatorname{Re} a(u,u) = \operatorname{Re} \langle u, T u \rangle \le \|u\| \|T u\| \quad \Rightarrow \quad \alpha \|u\| \le \|T u\|. $$

Thus $T$ is bounded below and injective. Moreover, its range $R(T)$ is closed: if $T u_n \to w$, then $(T u_n)$ is Cauchy, and from $\alpha \|u_n - u_m\| \le \|T u_n - T u_m\|$, we get $(u_n)$ Cauchy, so $u_n \to u$, and by continuity $T u_n \to T u = w$. Hence $R(T)$ is closed.

We show $R(T) = H$. If not, there exists $w \in R(T)^\perp$, $w \neq 0$. Then
$$ 0 = \langle w, T w \rangle = a(w,w) \quad \Rightarrow \quad \alpha \|w\|^2 \le \operatorname{Re} a(w,w) = 0, $$
which forces $w = 0$, a contradiction. Therefore $T$ is surjective.

Now, for a given $\ell \in H^*$, Riesz gives $f \in H$ such that $\ell(v) = \langle v, f \rangle$ for all $v$. Since $T$ is bijective, there exists a unique $u \in H$ with $T u = f$. Hence
$$ a(u,v) = \langle v, T u \rangle = \langle v, f \rangle = \ell(v) \quad \forall v \in H. $$

Finally, taking $v = u$ in the equation:
$$ \alpha \|u\|^2 \le \operatorname{Re} a(u,u) = \operatorname{Re} \ell(u) \le \|\ell\| \|u\|, $$
so $\|u\| \le \frac{1}{\alpha} \|\ell\|$. Uniqueness follows from coercivity. $\square$

</details>

---

$\color{Teal}{\textbf{Remark 4.5}}$ The Lax‑Milgram theorem is the cornerstone of the analysis of variational problems arising in partial differential equations. In the context of the Finite Element Method, it guarantees the well‑posedness (existence, uniqueness, and stability) of the weak formulation of elliptic boundary value problems. The coercivity constant $\alpha$ directly affects the condition number of the discrete system, and the boundedness constant $M$ appears in error estimates (Céa's lemma). In Density Functional Theory, similar variational structures appear in the Kohn–Sham equations, where the theorem supports the analysis of the associated nonlinear eigenvalue problems.

</details>
