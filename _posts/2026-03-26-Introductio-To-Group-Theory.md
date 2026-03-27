---
title: "Seminar: An Introduction to Group Theory"
date: 2026-03-27 19:25:00 +0700
categories: [Seminar, Cryptography]
tags: [group-theory, abstract-algebra, seminar]
math: true
---

Recently, I presented a seminar about Group Theory. I'd recommend you read the full original slides for more context but since it's long so I'll just summarize the contents here.

## 1. What is a Group?

### Definition of a Group
A Group is some set $G$, along with a binary operation $\circ$ that conforms to some Axioms. We write a Group as $(G, \circ)$ to explicitly specify both the set $G$ and the operation.

This system must satisfy the following 4 Axioms:

* **Closure:** For all $a, b \in G$, the result $a \circ b$ is also in $G$.
* **Associativity:** For all $a, b, c \in G$:
  $$(a \circ b) \circ c = a \circ (b \circ c)$$
* **Identity Element:** There exists an element $e \in G$ such that:
  $$a \circ e = a = e \circ a$$
* **Inverse Element:** For every $a \in G$, there exists $a^{-1} \in G$ such that:
  $$a \circ a^{-1} = e = a^{-1} \circ a$$