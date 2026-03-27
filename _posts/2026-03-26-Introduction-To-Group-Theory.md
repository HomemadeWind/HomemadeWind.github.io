---
title: "Seminar: An Introduction to Group Theory"
date: 2026-03-27 19:25:00 +0700
categories: [Cryptography, Seminar]
tags: [group-theory, abstract-algebra, seminar]
math: true
---

Recently, I presented a seminar about Group Theory. I'd recommend you read the full [original slides](/assets/pdf/Part_1_Group_Theory.pdf) for more context but since it's long so I'll just summarize the contents here.

## 1. What is a Group?

### Definition of a Group
A **Group** is some set $G$, along with a binary operation $\circ$ that conforms to some Axioms. 

**Notation:** We write a Group as $(G, \circ)$ to explicitly specify both the set $G$ and the operation, or simply $G$ with any operation.

**So what kind of set G could be here? and what exactly is a binary operation?**
### The Set $G$
The set $G$ can be any set as long as it is **non-empty**. Examples include:
* Hours in a clock form a set $H=\{0,1,2,...,11\}$
* Integer set: $\mathbb{Z}=\{...,-2,-1,0,1,2,...\}$
* Rational, Natural, Real, and Complex numbers: $\mathbb{R}, \mathbb{N}, \mathbb{Q}, \mathbb{C}$
* Even numbers $2\mathbb{Z}=\{...,-2,0,2,...\}$

### The Binary Operation
The binary operation can be any function as long as it takes 2 inputs and produces 1 output, e.g., $f(a,b)=c$ (from which the name "binary"). Examples include:
* **Arithmetic:** Addition ($+$), Multiplication ($\times$),...
* **Boolean Algebra:** XOR ($\oplus$), AND ($\land$), OR ($\lor$)
* **Others:** $a\circ b=a^{b}$, or $a\circ b=a\times b+2a-3$

The *reason* behind we use $\circ$ to denote the operation is that **we** don't actually *know* what operation yet.
So what about **Axioms**?

---

### The 4 Axioms
To be a valid group, this system must satisfy the following 4 Axioms:

1. **Closure:** For all $a, b \in G$, the result $a \circ b$ is also in $G$.
2. **Associativity:** For all $a, b, c \in G$:
   $$(a \circ b) \circ c = a \circ (b \circ c)$$
3. **Identity Element:** There exists an element $e \in G$ such that:
   $$a \circ e = a = e \circ a$$
4. **Inverse Element:** For every $a \in G$, there exists an element $a^{-1} \in G$ such that:
   $$a \circ a^{-1} = e = a^{-1} \circ a$$

---

## 2. Examples of Groups (and Non-Groups)

### Example 1: Integers under Addition $(\mathbb{Z}, +)$
Let's test if Integers $\mathbb{Z}=\{...,-1,0,1,...\}$ under Addition ($+$) follow the rules.

* **1. Closure:** Does the sum of 2 integers still stay inside the set? 
  * *Check:* $5+(-3)=2$. Is 2 an integer? Yes. You can't add two whole numbers and suddenly get a fraction (like 2.5).
* **2. Associativity:** Does the order of addition matter? 
  * *Check:* $(2+3)+4=5+4=9$ and $2+(3+4)=2+7=9$. The sums are identical.
* **3. Identity Element:** Is there an Identity element? We need an $e$ such that $a+e=a$. 
  * *Check 0:* $5+0=5$ and $(-7)+0=-7$. Yes, $e=0$ is the identity.
* **4. Inverse Element:** Can we "undo" an addition? For any integer $a$, can we get back to the identity (0)? 
  * If we have 5, we need -5 to reach 0. If we have -100, we need 100 to reach 0. Yes, for every $a$, the inverse is $-a$.

**Conclusion:** $(\mathbb{Z},+)$ is indeed a group.

### Example 2: Natural Numbers under Addition $(\mathbb{N}, +)$
We proved $(\mathbb{Z},+)$ is a group. What about $(\mathbb{N}=\{0,1,2,...\},+)$? Let's check it out:

* **Closure, Associativity, Identity:** Similar to $(\mathbb{Z}, +)$.
* **Inverse:** Are there inverses for every $a \in \mathbb{N}$? Unfortunately no, there's no number in $\mathbb{N}$ that satisfies: $1+x=0$.

**Conclusion:** $(\mathbb{N}, +)$ is **not** a group.

### Example 3: Finite Sets - Integers Modulo $n$ $(\mathbb{Z}_{n}, +)$
What about finite sets? Consider the set Integer modulo $n$ ($\mathbb{Z}_{n}$) under the addition operator. Let's test if it is a group:

* **Closure, Associativity, Identity:** Similar to $(\mathbb{Z}, +)$.
* **Inverse:** For any $a \in \mathbb{Z}_{n}$, we want $b \in \mathbb{Z}_{n}$ such that $a+b \equiv 0 \pmod{n}$. Choose $b=n-a$. Then:
  $$a+(n-a)=n \equiv 0 \pmod{n}$$
  So every element has an inverse.

**Conclusion:** $(\mathbb{Z}_{n},+)$ is a group.

---

## 3. Properties of a Group

Groups share several core properties. We'll prove the first two and leave the rest as exercises.

* **Uniqueness:** The Identity element ($e$) and Inverses ($a^{-1}$) are unique.
* **Cancellation Law:** For all $a, b, c \in G$: If $a \circ b = a \circ c$, then $b = c$.
* **Solvability:** The equation $a \circ x = b$ always has a unique solution $x \in G$.

### Proof: The identity element is unique
**Proposition 1:** The identity element of a group is unique.

**Proof:** Suppose $e$ and $e'$ are both identity elements in $G$.
* $e \circ e' = e'$ (treating $e$ as the identity)
* $e \circ e' = e$ (treating $e'$ as the identity)

Combine the two results: $e' = e \circ e' = e$. Therefore, $e = e'$, so the identity is unique.

### Proof: The inverses are unique
**Proposition 2:** The inverses in a group are unique.

**Proof:** Suppose $g'$ and $g''$ are both inverses of element $g$ in $G$. We need to show that $g' = g''$.

We have:
* $g \circ g' = e = g' \circ g$
* $g \circ g'' = e = g'' \circ g$

$$\rightarrow g' = g' \circ e = g' \circ (g \circ g'') = (g' \circ g) \circ g'' = e \circ g'' = g''$$

Therefore, $g' = g''$, so every inverse for all $g \in G$ is unique.

---

## 4. Exercises

I think after all these definitions and examples, you can try proving these yourself! (Really easy, trust)

* **Exercise 1:** Show that for all $a, b, c \in G$: If $a \circ b = a \circ c$, then $b = c$.
* **Exercise 2:** Show that the equation $a \circ x = b$ always has a unique solution $x \in G$.
