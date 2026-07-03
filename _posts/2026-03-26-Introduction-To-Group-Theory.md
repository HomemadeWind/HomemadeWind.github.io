---
title: "An Introduction to Group Theory"
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
* Hours on a clock form the set $H=\lbrace0,1,2,\ldots,11\rbrace$
* The integers: $\mathbb{Z}=\lbrace\ldots,-2,-1,0,1,2,\ldots\rbrace$
* The rational, natural, real, and complex numbers: $\mathbb{Q},\mathbb{N},\mathbb{R},\mathbb{C}$
* The even integers: $2\mathbb{Z}=\lbrace\ldots,-2,0,2,\ldots\rbrace$

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

### Examples of Groups (and Non-Groups)

**Example 1: Integers under Addition $(\mathbb{Z}, +)$**
Let's test if Integers $\mathbb{Z}=\lbrace\ldots,-1,0,1,\ldots\rbrace$ under Addition ($+$) follow the rules.

* **1. Closure:** Does the sum of 2 integers still stay inside the set? 
  * *Check:* $5+(-3)=2$. Is 2 an integer? Yes. You can't add two whole numbers and suddenly get a fraction (like 2.5).
* **2. Associativity:** Does the order of addition matter? 
  * *Check:* $(2+3)+4=5+4=9$ and $2+(3+4)=2+7=9$. The sums are identical.
* **3. Identity Element:** Is there an Identity element? We need an $e$ such that $a+e=a$. 
  * *Check 0:* $5+0=5$ and $(-7)+0=-7$. Yes, $e=0$ is the identity.
* **4. Inverse Element:** Can we "undo" an addition? For any integer $a$, can we get back to the identity (0)? 
  * If we have 5, we need -5 to reach 0. If we have -100, we need 100 to reach 0. Yes, for every $a$, the inverse is $-a$.

**Conclusion:** $(\mathbb{Z},+)$ is indeed a group.

**Example 2: Natural Numbers under Addition $(\mathbb{N}, +)$**
We proved $(\mathbb{Z},+)$ is a group. What about $(\mathbb{N}=\lbrace0,1,2,\ldots\rbrace,+)$? Let's check it out:

* **Closure, Associativity, Identity:** Similar to $(\mathbb{Z}, +)$.
* **Inverse:** Are there inverses for every $a \in \mathbb{N}$? Unfortunately no, there's no number in $\mathbb{N}$ that satisfies: $1+x=0$.

**Conclusion:** $(\mathbb{N}, +)$ is **not** a group.

**Example 3: Finite Sets - Integers Modulo** $n$ $(\mathbb{Z}_{n}, +)$

What about finite sets? Consider the set Integer modulo $n$ ($\mathbb{Z}_{n}$) under the addition operator. Let's test if it is a group:

* **Closure, Associativity, Identity:** Similar to ($$\mathbb{Z}, +$$).
* **Inverse:** For any $$a \in \mathbb{Z}_{n}$$, we want $$b \in \mathbb{Z}_{n}$$ such that $$a+b \equiv 0 \pmod{n}$$. Choose $$b=n-a$$. Then: $$a + (n - a) = n \equiv 0 \pmod{n}$$. So every element has an inverse.

**Conclusion:** ($$\mathbb{Z}_{n}, +$$) is a group.

---

### Properties of a Group
Groups share several core properties. We'll prove the first two and leave the rest as exercises.

* **Uniqueness:** The Identity element ($e$) and Inverses ($a^{-1}$) are unique.
* **Cancellation Law:** For all $a, b, c \in G$: If $a \circ b = a \circ c$, then $b = c$.
* **Solvability:** The equation $a \circ x = b$ always has a unique solution $x \in G$.

**Proof: The identity element is unique**

Suppose $e$ and $e'$ are both identity elements in $G$.
* $e \circ e' = e'$ (treating $e$ as the identity)
* $e \circ e' = e$ (treating $e'$ as the identity)
Combine the two results: $e' = e \circ e' = e$. Therefore, $e = e'$, so the identity is unique.

**Proof: The inverses are unique**

Suppose $g'$ and $g''$ are both inverses of element $g$ in $G$. We need to show that $g' = g''$.
We have:
* $g \circ g' = e = g' \circ g$
* $g \circ g'' = e = g'' \circ g$

$$\rightarrow g' = g' \circ e = g' \circ (g \circ g'') = (g' \circ g) \circ g'' = e \circ g'' = g''$$

Therefore, $g' = g''$, so every inverse for all $g \in G$ is unique.

---

### Exercises

I think after all these definitions and examples, you can try proving these yourself! (Really easy, trust)

* **Exercise 1:** Show that for all $a, b, c \in G$: If $a \circ b = a \circ c$, then $b = c$.
* **Exercise 2:** Show that the equation $a \circ x = b$ always has a unique solution $x \in G$.

---

## 2. Abelian Groups

### Definition
A group $(G, \circ)$ is called **Abelian** (or commutative) if it satisfies one extra axiom:

5. **Commutativity:** For all $a, b \in G$:
   $$a \circ b = b \circ a$$

### Examples
**Examples:**
* **Abelian:** Integers $(\mathbb{Z}, +)$ because $1+2=2+1$. The same applies to $(\mathbb{R}, +)$, $(\mathbb{Q}, +)$, and $(\mathbb{C}, +)$. The Multiplicative Group modulo $p$, denoted as $(\mathbb{Z}_{p},\times)$, is also Abelian because multiplication is commutative.
* **Non-Abelian:** Matrix Multiplication, because usually $A \times B \neq B \times A$.

* Ye that's it, we don't have much things to talk about abelian's own *properties* but it's **commutativity** appears **alot** for later *groups* and *theorems*.


---

## 3. Subgroups

A **Subgroup** is a subset $H \subseteq G$ that forms a group in its own right under the same binary operation as $G$. In simpler terms, it's a group within a group. We write $H \le G$ to denote that $H$ is a subgroup of $G$.

### The Subgroup Test
Instead of checking all 4 group axioms again, we only need to verify two conditions for a non-empty subset $H$:
1. **Closure:** $\forall a,b \in H \Rightarrow a \circ b \in H$
2. **Inverses:** $\forall a \in H \Rightarrow a^{-1} \in H$

*(Note: Properties like Associativity and Commutativity are automatically inherited from the parent group $G$.)*

### Examples of Subgroups
* **Even Integers:** Consider the set $2\mathbb{Z} = \lbrace\ldots,-4,-2,0,2,4,\ldots\rbrace$. This set forms a group under addition, denoted as $(2\mathbb{Z}, +)$. Since every even integer is also an integer ($2\mathbb{Z} \subseteq \mathbb{Z}$), we say that $(2\mathbb{Z}, +)$ is a subgroup of $(\mathbb{Z}, +)$.
* **Integers Modulo 6:** Let $G = \mathbb{Z}_{6} = \lbrace0,1,2,3,4,5\rbrace$ under addition. The subsets $H=\lbrace0,3\rbrace$ and $K=\lbrace0\rbrace$ are both subgroups of $G$. 
  * Notice that the subset $K=\lbrace e_G\rbrace$ is always a subgroup of $G$. We call this a **trivial subgroup**, while a proper subset $H$ is called a **proper subgroup**.

### Properties of Subgroups
**Proposition 1:** The identity of $G$ ($e_G$) is in $H$ ($e_H$).

**Proof:**
It is quite easy to verify that the identity of $G$ is in $H$.
Assume that $a \in H$ where $a \neq e_G$. Since $H$ is a group, $a$ must be in $H$ and so is $a^{-1}$. Their operation results in the identity of $H$:
$$a \circ a^{-1} = e_H$$
Looking from the group $G$ perspective, $a \circ a^{-1}$ is also equal to $e_G$.
Therefore:
$$e_H = e_G \in H$$

*(Note: A subset $H \subseteq G$ could be a group without being a subgroup of $G$).*

---

## 4. Cyclic Groups

Knowing every element of a group can be difficult, especially when the group is large.

A natural question is:

> Can we generate every element of a group starting from just a single element?

Surprisingly, the answer is **yes** for many groups.

### Cyclic Subgroups

Let $G$ be an Abelian group and let $a \in G$.

The **cyclic subgroup generated by** $a$ is denoted by $\langle a \rangle$.

In multiplicative notation,

$$
\langle a\rangle=\{a^k:k\in\mathbb Z\}
=\lbrace\ldots,a^{-1},e,a,a^2,\ldots\rbrace.
$$

In additive notation,

$$
\langle a\rangle=\{ka:k\in\mathbb Z\}
=\lbrace\ldots,-a,0,a,2a,\ldots\rbrace.
$$

For example, in $(\mathbb Z,+)$,

$$
\langle1\rangle=\mathbb Z,\qquad
\langle3\rangle=3\mathbb Z,\qquad
\langle7\rangle=7\mathbb Z.
$$

Notice that different elements may generate different subgroups.

---

### Definition

A group $G$ is called **cyclic** if there exists an element $a\in G$ such that

$$
G=\langle a\rangle.
$$

Such an element is called a **generator** of $G$.

For example,

- $(\mathbb Z,+)$ is cyclic because $\langle1\rangle=\mathbb Z$.
- $(\mathbb Z_n,+)$ is cyclic because $\langle1\rangle=\mathbb Z_n$.

Not every element has to be a generator.

For instance, in $(\mathbb Z_6,+)$,

- $\langle1\rangle=\mathbb Z_6$
- $\langle5\rangle=\mathbb Z_6$
- $\langle2\rangle=\lbrace0,2,4\rbrace$
- $\langle3\rangle=\lbrace0,3\rbrace$

Only $1$ and $5$ generate the entire group.

---

### Order of an Element

The **order** of an element $a$, denoted $\operatorname{ord}(a)$, is the smallest positive integer $k$ satisfying

$$
a^k=e.
$$

If no such integer exists, we write

$$
\operatorname{ord}(a)=\infty.
$$

For example,

- In $(\mathbb Z,+)$, the element $1$ has infinite order.
- In $(\mathbb Z_6,+)$,
  - $\operatorname{ord}(1)=6$
  - $\operatorname{ord}(2)=3$
  - $\operatorname{ord}(3)=2$

Notice that the order of an element is exactly the number of distinct elements in the cyclic subgroup it generates.

---

### Properties of Cyclic Groups

Two important properties of cyclic groups are:

- Every cyclic group is **Abelian**.
- Every subgroup of a cyclic group is itself **cyclic**.

**Proof: Every cyclic group is Abelian**

Suppose $a,b \in G$ and $G = \langle g\rangle$.

Then there exist integers $m,n$ such that $a=g^m$ and $b=g^n$. Therefore,

* $ab=g^mg^n=g^{m+n}=g^{n+m}=g^ng^m=ba$.

Therefore, $ab=ba$ for all $a,b\in G$. Hence, $G$ is Abelian.

**Proof idea: Every subgroup of a cyclic group is itself cyclic**

The complete proof is slightly beyond the scope of this post, so I'll only present the main idea.

Let $H \le G$. If $H=\lbrace e\rbrace$, then it is cyclic. Otherwise, choose the smallest positive integer $k$ such that $a^k \in H$.

One can then show that every element of $H$ is a power of $a^k$. Hence,

$$
H=\langle a^k\rangle.
$$

These properties are fundamental in abstract algebra and appear frequently throughout modern cryptography.

If you're interested in a complete proof, see:

> Thomas W. Judson, *Abstract Algebra: Theory and Applications*, Theorem 4.10 (p. 48).

