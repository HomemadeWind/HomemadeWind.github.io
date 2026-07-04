---
title: "An Introduction to Group Theory Part 2"
date: 2026-07-03 14:50:00 +0700
categories: [Cryptography, Seminar]
tags: [group-theory, abstract-algebra, seminar]
math: true
---

This is Part 2 of my Group Theory seminar summary. Now that we have covered the foundational definitions, we will dive into how different groups interact with each other and how they can be partitioned. As a reminder, you can check out the [original slides](/assets/pdf/Part_2_Group_Theory.pdf) for the full context.

## 1. Homomorphisms

After learning what groups are, a natural question is:

> Can two different groups behave in essentially the same way?

To answer this, we introduce **homomorphisms**.

### Definition

A **homomorphism** is a map

$$
f:G\rightarrow H
$$

between two groups that preserves the group operation.

In other words,

$$
f(a\circ b)=f(a)\star f(b)
$$

for every $a,b\in G$, where $\circ$ and $\star$ are the operations on $G$ and $H$, respectively.

Notice that the operations do not have to be the same.

---

### Examples

Consider

$$
f:(\mathbb Z,+)\rightarrow(\mathbb Z_6,+)
$$

defined by

$$
f(x)=x\bmod6.
$$

Then

$$
f(a+b)
=(a+b)\bmod6
=f(a)+f(b),
$$

so $f$ is a homomorphism.

On the other hand,

$$
f(x)=x+1
$$

is **not** a homomorphism because

$$
f(a+b)=a+b+1
$$

while

$$
f(a)+f(b)=a+b+2.
$$

---

### Properties

Homomorphisms preserve many important structures.

If $f:G\to H$ is a homomorphism, then

- $f(e_G)=e_H$.
- $f(a^{-1})=f(a)^{-1}$.
- $f(a^n)=f(a)^n$ for every integer $n$.

These properties make homomorphisms extremely useful throughout algebra and cryptography.

## 2. Isomorphisms

Sometimes a homomorphism preserves **everything** about the group.

### Definition

An **isomorphism** is a bijective homomorphism.

If there exists an isomorphism

$$
f:G\rightarrow H,
$$

we write

$$
G\cong H.
$$

Although the elements may look different, the two groups have exactly the same algebraic structure.

---

### Example

Consider

$$
(\mathbb Z_4,+)
$$

and

$$
(\lbrace1,i,-1,-i\rbrace,\times).
$$

Define

$$
\begin{aligned}
0&\mapsto1,\\
1&\mapsto i,\\
2&\mapsto-1,\\
3&\mapsto-i.
\end{aligned}
$$

Addition modulo $4$ corresponds exactly to multiplication of the fourth roots of unity.

Therefore,

$$
\mathbb Z_4\cong
\lbrace1,i,-1,-i\rbrace.
$$

Even though these groups look completely different, they are algebraically identical.

## 3. Cosets

Suppose $H$ is a subgroup of $G$.

Instead of looking only at $H$, we can "shift" it by an element of $G$.

### Definition

For $g\in G$,

the **left coset** of $H$ is

$$
gH=\lbrace gh:h\in H\rbrace,
$$

while the **right coset** is

$$
Hg=\lbrace hg:h\in H\rbrace.
$$

If the group is Abelian, these are always equal.

---

### Example

Let

$$
G=\mathbb Z,
\qquad
H=2\mathbb Z.
$$

Then

$$
0+H
=
\lbrace\ldots,-4,-2,0,2,4,\ldots\rbrace,
$$

while

$$
1+H
=
\lbrace\ldots,-3,-1,1,3,5,\ldots\rbrace.
$$

Notice that every integer belongs to exactly one coset.

Cosets partition a group into disjoint pieces.

---

### Lagrange's Theorem

One of the most important consequences of cosets is **Lagrange's Theorem**.

If $H\le G$ and $G$ is finite,

$$
|H|\mid|G|.
$$

In other words, the order of every subgroup divides the order of the group.

This theorem appears everywhere in group theory and plays an important role in modern cryptography.

## 4. Quotient Groups

Cosets naturally lead to the idea of a **quotient group**.

Instead of treating each element separately, we treat each coset as a single object.

However, this only works when the subgroup is **normal**.

### Definition

If $N\trianglelefteq G$ is a normal subgroup, then the quotient group is

$$
G/N
=
\lbrace gN:g\in G\rbrace.
$$

The group operation is

$$
(gN)(hN)
=
(gh)N.
$$

---

### Example

Let

$$
G=\mathbb Z,
\qquad
N=3\mathbb Z.
$$

Then

$$
\mathbb Z/3\mathbb Z
=
\lbrace
0+N,\,
1+N,\,
2+N
\rbrace,
$$

which behaves exactly like

$$
\mathbb Z_3.
$$

In fact,

$$
\mathbb Z/3\mathbb Z
\cong
\mathbb Z_3.
$$

Quotient groups allow us to simplify complicated groups while preserving their essential structure.