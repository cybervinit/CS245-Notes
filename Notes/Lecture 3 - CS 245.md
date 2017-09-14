## CS 245 - Lecture 3

---

### Parse Trees

- A *parse tree* for a WFPF displays the construction of the formula as a tree.
- *Example:* the parse tree for $\phi = ((p $ ^ $(\neg q)) \implies r)$ 

[^ VINIT ]: <Insert Parse Tree Image here>

This parse tree has height 4.

[^ NOTE ]: Another one on *page 34* of the text.

*Typical Parse Tree Question:* given a *parse tree*, write it's formula.

### *Proof:* Unique Readability of Propositional Formulae

[^ Remark ]: The proof in the slides omits the **negation case** from the *Induction Step*.
[^ Remark ]: This proof is hard. A proof like this may show up on assignments, but **never on a test**.

*Theorem:* Every WFPF $\alpha$ is exactly one of an **atom**, $(\neg \beta)$, $(\beta$ ^ $\gamma)$, $(\beta $ v $ \gamma)$, $\beta \implies \gamma)$, or $(\beta \iff \gamma)$, and in each case, $\alpha$ is of that form in exactly one way.

*Proof:* Let $\alpha$, be any WFPF. The proof is by *Structural Induction* on $\alpha$.

Let $R(\alpha)$ hold *if and only if* $\alpha$ satisfies all 3 of the following:

​	A: The first symbol of the formula $\alpha$ is either a '(' or a variable.

​	B: $\alpha$ has equally many '(' as ')', and each <u>proper prefix</u> of $\alpha$ has more '(' than ')' symbols.

[^ NOTE ]: A proper prefix of $\alpha$ is a non-empty expression $x$, such that $\alpha$ is $xy$ for some non-empty expression $y$. *Example:* $\alpha$ is $(\neg p)$, $x$ is $(\neg$, $y$ is $p)$.

​	C: $\alpha$ has a unique construction as a formula.

<u>Base Case:</u> ($\alpha$ is $p$ for some Prop. variable $p$)

​	$R(\alpha)$ holds trivially in this case.

<u>Induction Step:</u> 2 sub-cases

1. $\alpha$ is $(\neg \beta)$ for some WFPF $\beta$.

   Induction Hypothesis: $R(\beta)$, i.e. $\beta$ has A, B, C.

   - By construction, $(\neg \beta)$ starts with '(', so it has A.

   - Since $\beta$ has equally many '(' as ')', therefore, so does $(\neg \beta)$.

   - Since every proper prefix of $\beta$ has more '(' than ')', therefore so does $(\neg \beta)$.

   - Hence, $(\neg \beta)$ has property B.

   - Since $\beta$ has a unique construction formula, so does $(\neg \beta)$.

   - This shows that $(\neg \beta)$ has property C.

     [^ Remark ]: We will see later that $(\neg (\neg p)) \equiv p$, however, these formulae are <u>not equal</u>.

2. $\alpha$ is a $(\beta * \gamma)$ for some WFPF $\beta$ and $\gamma$ and binary connective $*$.

   $I.H. \rightarrow$ $R(\beta)$ and $R(\gamma)$, i.e. $\gamma$ and $\beta$.  i.e. $\gamma$ $\beta$ have A, B, C.

   - By construction, $(\beta * \gamma)$, starts with '(', so has A.
   - Since $\beta$, $\gamma$ have balanced '(' as ')', so does $(\beta * \gamma)$.
   - Since *proper prefixes* of $\beta$ and $\gamma$ have more '(' than ')', so does proper prefix of $(\beta * \gamma)$.
   - Hence, $(\beta * \gamma)$ has property $\beta$
   - C $\rightarrow$ Suppose $(\beta * \gamma)$ is also $(\beta' *' \gamma')$ for some WFPF $\beta'$, $\gamma'$ and binary connective $*'$. We want to prove $\beta = \beta'$, $\gamma' = \gamma$, and $*' = *$.
   - Compare $|\beta|$ and $|\beta'|$.
   - If $|\beta| = |\beta'|$, it follows that $\beta= \beta'$.
   - Then also, it follows that $*'= *$, $\gamma' = \gamma$.
   - So for a contradiction, suppose $|\beta'| < |\beta|$  or $|\beta'| > |\beta|$. Since $\beta$ has B, this says that $\beta'$ has more '(' than ')' symbols. This contradicts the fact that $\beta'$ has $\beta$. (Because then, $\beta'$ must have balanced '(' and ')' symbols)
   - We reach a similar contradiction from assuming $|\beta'| > |\beta|$.

   This shows that $(\beta * \gamma)$ has C.

   This finishes the $2^{nd}$ induction case, and finally the proof.

   ​