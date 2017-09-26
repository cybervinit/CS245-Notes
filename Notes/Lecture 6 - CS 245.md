## Lecture 6 (Slide 80-98)

---

### Satisfaciton of a Set of Formulae

*Definition:* Let $\sum$ (**note:** sigma not sum) be a set of WFPF. Let $t$ be a truth valuation.

We say that $t$ satisfies $\sum$ (Notation: $\sum^t = T$) if for all $\phi \in \sum, \phi^t = T$

*Problems (from the slides)* 

1. Verify that $\sum = \{ ((p \rightarrow q)$ v $r), ((p$ v $q)$ v $s)\}$ is satisfiable

*Solution:* Let $t$ be a truth valuation with $t(q) = T, t(p), t(r)$ are anything

Then $(p \rightarrow q)^t = T$, so that $((p \rightarrow q)$ v $r)^t = T$

Also, $(p$ v $q)^t = T$, hence $((p$ v $q)$ v $s)^t = T$ 

Hence, this shows that $\sum^t = T$ (It is satisfiable)

2. Is the set $\sum = \{ (p \rightarrow (p$ ^ $q)), ((\neg p)$ v $(\neg q)), ((\neg p) \rightarrow p) \}$

*Solution:* Claim is that the set is not satisfiable. [One way to show is *truth table* for all involved formula. Make sure that no row makes all 3 formulae **true** at once].

For a contradiction, suppose we have a truth valuation $t$ such that $\sum = T$.

In particular, $(p \rightarrow (p$ ^ $q))^t = T$. 

Cases: (*These are cases to make the implication true*)

- $p^t = F$ 

  Then, $((\neg p) \rightarrow p)^t = F$. This contradicts $\sum^t = T$

- $(p$ ^ $q)^t = T$. Then, $p^t = T = q^t$. But then, $((\neg p)$ v $(\neg q))^t = F$. This contradicts $\sum^t = T$.

$\therefore$ all possibilities lead ot a contradiction. So we are done (set is not satisfiable).

---

### Semantic Entailment

*Definition:* let $\sum$ be a set of WFPF. Let $\phi$ be a WFPF. Then, we say that <u>$\sum$ (semantically) entails $\phi$</u> if:

​	If whenever $\sum^t = T$ (for some truth valuation $t$), it follows that $\phi^t = T$. (Notation: $\sum$ |= $\phi$ ) 

[^ remark ]: The notion of semantic entailment will be a key ingredient in defining the soundness and completeness of our proof system
[^ remark ]: It is crucial to understand that the definition made assers nothing for $\sum^t = F$.
[^ remark ]: To prove an entailment does **not** hold, we must exhibit a truth valuation that satisfies $\sum$, but doesn't satisfy $\phi$. i.e. $\sum^t = T$ but $\phi^t = F$



*Problems:* 

1. Is it true that $\{ (p$ ^ $q)\}$  |= $p$?

   *Answer:* yes, any truth valuation $t$ satisfying $(p$ ^ $q)$ must have $t(p) = T = t(q)$. In particular $p^t = T$. 

   *Sub-question:* Does $\{ (p$ ^ $q)\}$ |= $r$ hold?

   *Answer:* No. Consider $t$ such that $t(p) = T = t(q)$, but $t(r) = F$. So the entailment fails

2. Is it true that $\{(p$ v $q)\}$ |= $p$ ?

   *Answer:* No. Consider $t$ with $t(q) = T, t(p)=F$. Then, $(p$ v $q)^t = T$, but $p^t = F$. The entailment does not hold.

3. Prove or disprove this entailment: $\{ (p \rightarrow q), (q \rightarrow (\neg r)) \}$ |= $(p \rightarrow (\neg q))$ 

   *solution:* we write a joint truth table for all formulae involved:

   ​

| $p$  | $q$  | $r$  | $(p \rightarrow r)$ | $(q \rightarrow (\neg r))$ | $(p \rightarrow (\neg q))$ |
| :--: | :--: | :--: | :-----------------: | :------------------------: | :------------------------: |
|  F   |  F   |  F   |          T          |             T              |           **T**            |
|  F   |  F   |  T   |          T          |             T              |           **T**            |
|  F   |  T   |  F   |          T          |             T              |           **T**            |
|  F   |  T   |  T   |          T          |             F              |             T              |
|  T   |  F   |  F   |          F          |             T              |             T              |
|  T   |  F   |  T   |          T          |             T              |           **T**            |
|  T   |  T   |  F   |          F          |             T              |             F              |
|  T   |  T   |  T   |          T          |             F              |             F              |

[^ NOTE ]: the rows that are bolded are the only rows where the set is saitsfied. Hence, they're the only ones that matter for verifying the entailment. Since all the **bold** rows also have $T$ for $(p \rightarrow (\neg q))$, the entailment holds.

#### Subtleties about Entailment

[^ remark ]: Any statement lie "For all $x \in \emptyset, x < 6$" is true. The empty set $\emptyset$, provides no counter-example $x \in \emptyset$, such that $x < 6$ is not true.
[^ remark ]: By the same token "For all $\phi \in \emptyset$ , $\phi^t = T$ is true. (for any truth valuation $t$).
[^remark]: Moral: <u>The empty set, $\emptyset$ is satisfied under any truth valuation</u>
[^remark]: Moral: If $\emptyset$ |= $\phi$, then $\phi$ is a **tautology**.
[^remark]: If $\phi$ is a tautology, then $\sum$ |= $\phi$, for any $\sum$. 
[^ remark ]: if $\sum$ is not satisfiable, then $\sum$ |= $\phi$, <u>for any $\phi$.</u>
[^ remark ]: An equivalence of $\equiv$ using |= is:

​	$\alpha \equiv \beta \iff (\{ \alpha\}$ |= $\beta$ and $\{ \beta \}$ |= $\alpha)$ 

---

### Intro to Proof Systems

<<<DEFERRED TO THURS LECTURE>>>

---

### Intro to Natural Deduction for Prop. Logic

*Example:* Prove that the following set $\{ (p$ ^ $q), (r$ ^ $s) \}$ |— $(p$ ^ $s)$    [ |— is a symbol for *"Proves*"]

*Solution:* 

1. $(p$ ^ $q)$ [*Premise*]
2. $(r$ ^ $s)$ [*Premise*]
3. $p$         \[^e : 1]
4. $s$         \[^e : 2]
5. $(p$ ^ $s)$ \[^i: 3, 4]

[^ remark ]: Every line of a proof is a WFPF
[^ remark ]: Every line is justified, either by *Premise* or by some inference rule, referring to previous line(s).
[^remark ]: The proof starts from the given *Premises* and ends at the given *Conclusion*.