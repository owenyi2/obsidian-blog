---
title: Rings, Ideals and Quotient Rings
author: Owen Yi
tags:
  - "#mathematics/abstract-algebra"
---
In this blog, I will show how the intuition about Integers carries surprisingly far when learning about Rings, Ideals and Quotient Rings.

Rings generalise Integers, Ideals generalise sets of integer multiples, and the process of creating a Quotient Ring generalises the relation between Integer arithmetic and modulo arithmetic. 

# Pre-requisites

- Basic Logic symbols
- Equivalence Relation
- Definition of a Group (in particular an Abelian group)

# Multiplication and Addition of Integers $\cong$ Rings

Let $\mathbb{Z}$ denote the set of Integers. 
- We can add integers together and expect an integer $2 + 3 = 5$ 
- We can multiply integers together and expect an integer result $4 \times 7 = 28$

While there is a notion of integer division with remainder, e.g. $7 = 2\times 3 + 1$, in general, we cannot arbitrarily divide two integers and expect an integer. [^1]

In defining a *Ring*, we try to generalise these two operations. When generalising, we'd like some nice properties to remain such as associativity, commutativity, distributivity etc.

> [!Info] Definition
> A *Ring* is a set $R$ with two operations $+, \times$ that satisfy the following conditions
> - $R$ is an abelian group under the $+$ operation
> - $\times$ is an associative operation: $a\times(b\times c) = (a\times b) \times c$
> - $\times$ distributes over $+$: $a\times (b+c) = a\times b + a \times c$ and $(a + b) \times c = a\times c + b \times c$

Note: The tuple $(R, +, \times)$ is the bona fide ring but often for convenience, we just call $R$ the ring and the operations are implied by some previous context.

One thing that appears lacking in this definition is the commutativity of multiplication. *Rings* with the additional requirement that $\times$ is commutative are called *Commutative Rings*. 

# Congruence of Integers modulo n $\cong$ Equivalence Relation using Subgroups

The prototypical example of modulo arithmetic is a 12-hour clock. Starting at $00:00$, passing forward $3$ hours puts the clock at $3:00$. Passing over $15$ hours puts the clock on $3:00$ again. Passing over $27$ hours puts the clock on $3:00$ again...

To reduce a number $k$ modulo $n$ means to take the remainder after dividing $k$ by $n$. Since $27 = 2\times 12 + 3$ we say $27$ is $3$ modulo $12$. We write this as $27 \equiv 3 \pmod {12}$.

While $27$ is not literally $3$ we can identify the two as equivalent in some regards. (Here that equivalence is sharing the same remainder when divided by 12). 

We can phrase the congruence of integers modulo $n$ in terms of equivalence relations. 

> [!tip]+ Recall
> An equivalence relation $\sim$ is a relation on $X \times X$ satisfying
> - Reflexivity: $a \sim a$, $\forall a \in X$
> - Symmetry: $a \sim b \iff b \sim a$, $\forall a, b \in X$
> - Transitivity: $a \sim b \wedge b \sim c \implies a \sim c$, $\forall a, b, c \in X$

**Definition**: For $a, b \in \mathbb{Z}$, we say $a \sim b$ if $n \mid a - b$.

Notice that two numbers have the same remainder when divided by $n$ if and only if their difference is divisible by $n$. 
- Suppose $a = q_1n + r_1$ and $b = q_2n +r_2$ with $0 \leq r_1, r_2 < n$
- Then their difference $a-b = q_1n + r_1 -q_2n -r_2 = n(q_1-q_2) + (r_1 - r_2)$
- $\implies$ 
	- If $r_1 = r_2$ then $n \mid n(q_1 - q_2) = a-b$
- $\impliedby$ 
	- If $n \mid a - b = n(q_1 -q_2) + (r_1-r_2)$ then $n \mid r_1 - r_2$ and since $-n < r_1 -r_2 < n$ it follows $r_1 = r_2$

> [!tip] Claim 
> This is indeed an equivalence relation.
> 
> **Proof**
> 
> Reflexivity
> - $n \mid 0 \implies n \mid a -a \implies a \sim a$ 
> 
> Symmetry
> - $a \sim b \iff n \mid a - b \iff n \mid -1 \times (b-a) \iff n \mid b-a \iff b \sim a$
> 
> Transitivity
> - $a \sim b \wedge b \sim a \implies n \mid a - b \wedge n \mid b - c \implies n \mid (a-b) + (b-c) \implies n \mid a-c \implies a \sim c$
### move WIP 2 here

# Residue Classes $\cong$ Cosets

### move WIP 3 here

### move WIP 1 here

Proof that residue classes are disjoint or identical

### WIP 1 

Recall that given a ring $(R, +, \times)$, the structure $(R, +)$ is an abelian group. From Group Theory, there is a concept called a *Coset* which mirrors modulo congruence.[^2]

> [!Info] Definition
> Suppose we have a subgroup $(H, +) \leq (G, +)$. For each element $g \in G$, we can define a *Left Coset* as $g+H := \{g+h: h \in H\}$. 
> 
> The set of *Left Cosets* is the set $\{g+H: g \in G\}$

It may appear that the set of *Left Cosets* are as numerous as $G$ however this is misleading because it is possible that distinct $g \neq g' \in G$ form identical *Cosets* $g + H = g' + H$.

*Cosets* allows us to create an equivalence relation analogous to congruences of integers. 

### WIP 2

**Definition**: For $a, b \in G$, we say $a \sim b$ if $a - b \in H$.

> [!tip] Proposition
> This is indeed an equivalence relation.
> 
> **Proof**
> 
> Reflexivity
> - We use the existence of identity in a Group
> - $0 \in H \implies a - a \in H \implies a \sim a$ 
> 
> Symmetry
> - We use the existence of unique inverse in a Group
> - $a \sim b \iff a - b \in H \iff -(b-a) \in H \iff b-a \in H \iff b \sim a$
> 
> Transitivity
> - We use closure and associativity of the operator in a Group 
> - $a \sim b \wedge b \sim a \implies a - b \in H \wedge b - c \in H \implies (a-b) + (b-c)\in H \implies a-c \in H \implies a \sim c$

As an aside, the fact that we can define an equivalence relation using *Cosets* means that we can define a partition of $G$ using the equivalence classes produced by $H$. This can be used to prove [Lagrange's Theorem](https://en.wikipedia.org/wiki/Lagrange%27s_theorem_(group_theory)) if we note that all the *Cosets* are the same size (as least in the case of finite groups).

The verification that these are both equivalence relations are essentially the same. In fact, if every time I wrote $g \in H$ and replaced it with $n \mid g$ then the proofs would be written exactly the same. 

### WIP 3

Actually, we can rephrase $n \mid g$ in terms of groups and then directly apply the more general statement about *Cosets*.

- Consider the group $(\mathbb{Z}, +)$ and the subgroup $(n\mathbb{Z}, +)$. The notation $n \mathbb{Z}$ means $\{nq \mid q \in \mathbb{Z}\}$, in other words, the integer multiples of $n$
	- Therefore $n \mid a$ can be equivalently stated as $a \in n \mathbb{Z}$
- The cosets are $r + n\mathbb{Z}$, $r  \in \mathbb{Z}$. For example $a \in r + n\mathbb{Z}$ means that $a$ is of the form $a = nq + r$ for some $q \in \mathbb{Z}$
- The relation $a \sim b$ defined by $a - b \in n\mathbb{Z}$ is equivalent to the statement 

insert _this_

This gives the first step for constructing Quotient Rings because we have a Quotient Group, we just need to ensure the $\times$ operation works after quotient.

Even though we have introduced notation with residual classes for the integers, I will still use the old $\mid$ notation for the remainder of this blog to be closer to a proof you'd find in a textbook on elementary number theory 
# Integer Multiples $\cong$ Ideals



# Quotient Rings

$$\mathbb{Z} / n\mathbb{Z} = \mathbb{Z}_n$$

$$R \text{ is a Ring } \wedge I \subseteq R \text{ is an Ideal} \implies R/I \text{ is a Quotient Ring}$$
# Generalisation: First Isomorphism Theorem for Rings


# Appendix

## Crash Course for Pre-requisites
## Index of Notation Used

- $\mathbb{Z}$

[^1]: This lack is what makes ideals possible. In a field, we have multiplicative inverses. If we tried to make an ideal $I$ on a field $K$, then $a \in I$ implies $1 = a^{-1}a \in I$ rendering our ideal useless. Consider why we don't bother talking about multiples of a number in $\mathbb{Q}$. Because any number $p \in \mathbb{Q}$ is a multiple of $q \in {Q}$. Simply multiply by $pq^{-1}$

[^2]: Typically cosets are written with multiplication however to better mirror integer congruence, I have elected to use the notation for additive groups


<!-- Replace \cong with "is a" because they aren't isomorphic. The integer version is an instance of -->


---

Addition modulo $n$ is well defined

Multiplication modulo $n$ is well defined

Proof

Suppose $a \equiv a' \pmod n$ and $b \equiv b' \pmod n$. We need to prove that $a + b \equiv a' + b' \pmod n$. Using 1st and 2nd condition of Ideal

$a - a' \in n\mathbb{Z}$ and $b - b' \in n\mathbb{Z}$. Therefore $(a + b) - (a' + b') \in n\mathbb{Z}$. Moreover, $ab -a'b' = ab - a'b + a'b -a'b'= b(a-a') + a'(b-b') \in n\mathbb{Z}$. Using the 1st and 2nd condition of Ideal

Suppose $
