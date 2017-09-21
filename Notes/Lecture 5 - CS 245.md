## Lecture 5

---

### Equivalence of Formulae

[^ remark ]: Equality of formulae is often *too strong* for our purposes in CS 245
[^ remark ]: we want **Logical Equivalence**. It's often more useful

*Definition:* Two *Well-Formed* Propositional Formulae $\alpha, \beta$ are called **(Logically) equivalent** (denoted $\alpha \equiv \beta$ ) if $\alpha ^t = \beta ^t$ holds for all truth valuations $t$. 

(Equivalently, if $\alpha, \beta$ have the same *truth table*)

[^ remark ]: *From Clicker question:* An equivalence relation ($\equiv$) is <u>Reflexive, symmetric</u> and <u>transitive</u>

#### Problems

Prove or disprove the following each of the following equivalences from the slides. (using equivalence rules from Slides 66-67)

1. <insert picture here>
2. <insert picture here>

[^ remark ]: As in these examples, it is fine to do multiple changes using the **same rule** (e.g. Commutativity) on one line.
[^ NOTE ]: To prove an equivalence <u>does not hold</u>, we exhibit a *truth valuation* $t$ such that $\alpha^t \neq \beta^t$ 

---

### Simplifying Code

Problem: Consider the following 2 code fragments:

```
if (a && b) {P1}
else if (a) {P2}
else {P3}
```

```
if (!a) {P3}
else if (!b) {P2}
else {P1}
```

a) For each fragment, express in Prop. Logic the conditions under which eeach of P1, P2, P3 will be executed. *DO NOT SIMPLIFY* 

*Soln:* 

\#1

P1 $\rightarrow$ $(a$ ^ $b)$ 

P2 $\rightarrow$ $((\neg(a$ ^ $b))$ ^ $a)$ 

P3 $\rightarrow$ $(( \neg(a$ ^ $b))$ ^ $(\neg a))$

\#2

P3 $\rightarrow$ $(\neg a)$

P2 $\rightarrow$ $((\neg (\neg a))$ ^ $(\neg b))$ 

P1 $\rightarrow$  $((\neg (\neg a))$ ^ $(\neg (\neg b)))$

b) Give equivalence proofs to show that Fragments #1 and #2 have the same behaviour.

*Sol$^n$:* <insert picture here>

---

### Adequate Sets of Connectives

*Definition:* The **arity** of a function $f$ is the number $ n \geq 0$ of inputs the function takes

[^ remark ]: 0-ary functions are called <u>nullary</u>
[^ remark ]: 1-ary functions are called <u>unary</u>
[^ remark ]: 2-nary functions are called <u>binary</u>
[^ remark ]: a *propositional connective* $f * f$ arity $n$ is a function $f: \{FT\}^n \rightarrow \{F, T\}$ 

*Definition:* A set, $S$, of Propositional connectives is **adequate for Prop. Logic** if every Prop. connective (of any arity) can be implemented using the connectives form $S$.

*Theorem:* The set {^, v, $\neg$} is adequate for propositional logic

*Proof (sketch):* 

i) For each row of the truth table having $T$ output. ^-together $p$ if $p$'s col has $T$, $(\neg p)$ if $p$'s column has $F$. This ^- is $T$ on this row, false elsewhere

ii) Assemble the abocce using v's (or). The resulting v formlua has the required truth table, and is contradicted using {^, v, $\neg$}.

Lemma: Each of {^, $\neg$}, {v, $\neg$}, {$\implies$, $\neg$} is adequate for propositional logic

*Proof (Sketch):* Implement {^, v, $\neg$} using {^, $\neg$}. This shows {^, $\neg$} is adequate. Repeat for other two (full proofs in notes).