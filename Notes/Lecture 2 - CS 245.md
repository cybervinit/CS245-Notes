## CS 245 - Lecture 2

----------

### **Starting at Slide 18**

### 1. Translations: English $ \rightarrow{} $ Prop. Logic

Definition: Let P be a set of **Propositional Variables** (e.g. $ P = \{p, q, r\} $). Then the set of <u>Well formed Propositional Formulae over P</u> is defined inductively by

1. An expression consisting of a single system from P is a well-formed **Propositional Formula** 
2. If **$ \alpha $** is a well-formed **Propositional Formula**, then  ($\neg \alpha $) is a well-formed **Propositional Formula**
3. If $ \alpha $, $ \beta $ are well-formed **Propositional Formulae**, then each of ($ \alpha \text{^} \beta $) ,( $ \alpha $ v $ \beta $), ($ \alpha \implies \beta$) , and ($ \alpha \iff \beta$) is a well-formed **Propositional Formula** 
4. Nothing else is a well-formed **Propositional Formula** 

[^note]: 1 is the base case, 2 and 3 are the inductive section
[^ note ]: The above definition for formulae is $ 100\% $ syntactic, $ 0 \% $ semantic. **Syntax** $\rightarrow $ what are the *well-formed* formulae. **Semantic** $\rightarrow$ in some "context," which formulae are **true** and which are **false**.
[^note]: The definition for formulae is out first **recursive (inductive)** definition and lends itself to proofs with <u>Structural Induction</u>

####Problem: Translate English $ \rightarrow $ Well-Form Propositional Formula (WFPF)

*Examples:*

1. She is clever and hard-working.

   *Solution*: Let

   - **C** $ \rightarrow $ She is clever 
   - **h** $ \rightarrow $ She is hard-working

   Then, we get: (c ^ h)

2. He is clever, but not hard-working.

   *Solution*: Let

   - **c** $ \rightarrow $ He is clever
   - **h** $ \rightarrow $ He is hard-working [^handling negations: Remove all negations to make an accurate **atomic** prop.]  

   Then, we get: (c ^ (!h)) [^ NOTE: parentheses required by rule 3]

3. If it rains, he will be at home; otherwise, if it doesn't rain, he will go to the school or the market.

   *Solution*: Let

   - **r** $\rightarrow$ It rains
   - **h** $\rightarrow $ He will be at home
   - **m** $\rightarrow$ He will go to the market
   - **s** $\rightarrow $ He will go to school

   Then: ((r $\implies $ h) ^  (($\neg $ r) $ \implies $ (m v s))) [^NOTE: PARENTHESES REQUIRED BY RULE 2 AND 3]

[^ Remarks ]: From now, "formula" means WFPF

------------

### 2. Intro to Propositional Syntax

Problems: Which of the following expressions are **Well-Formed** Propositional Formulae over $ P = \{ p, q, r\}$ ?

1. is p WFPF? Yes, by Rule 1. 
2. pq? No, Rule 3 (the only thing able to connect two single-systems) requires a binary connector. [^ NOTE: RULE 4 $\rightarrow$ no]
3. ($ \neg p$) ? Yes, by 1) and Rule 2.
4. $ \neg p $ ? No,  because Rule 2 required parentheses.
5. (p v q v r) ? No, because Rule 3 is binary.
6. ((p v q) v r) ? Yes, by Rule 3



What are the lengths of each **expression**?

1. 1 symbol
2. 2 
3. 4
4. 2
5. 7
6. 9

[^ Note ]: Why will we care about lengths? Soon we may have to write a proof which *inducts* on the length of an expression (in particular, a formula)

---------

### 3. Structural Induction

[^ Remark ]: 1$^{st}$ Natural Number is 0. $ \mathbb{N} $ includes 0.
[^ Remark ]: Need proof techniques from Math 135. Especially using **Principle of Mathematical Induction (POMI)** 

Suppose that $P(n)$ denotes some property of $n \in \mathbb{N}$. Suppose we want to prove $P(n)$ for all $ n \ge 0 $.

<u>Base Case:</u> Prove $P(0)$. 

<u>Induction Step:</u> 

- Induction Hypothesis:* Assume $P(k)$ for some $k \ge 0$.
- *Induction Conclusion:* Use $I.H.$ to prove $P(k+1)$.

Then conclude by $POMI$, that $P(n)$ holds for all $n \ge 0$. 

*Question:* How do we modify this template for **Structural Induction**?

###### **Principle of Structural Induction**

Suppose $P(\phi)$ is a property, which might or might not hold for some WFPF $\phi$. Suppose we want to prove $P(\phi)$ for all WFPF $\phi$.

1. <u>Base Case:</u> Prove $P(p)$ for any Propositional variable $p$. 

   [^ NOTE ]: make sure the property holds for **atomics**.

2. <u>Induction Step:</u>

   Rule 2:

   - $I.H.$ Assume $P(\alpha)$, for some WFPF $\alpha$
   - Prove $P((\neg \alpha))$ 

   Rule 3

   - $I.H.$ Assume $P(\alpha)$ and $P(\beta)$, for some WFPF $\alpha, \beta$.
   - Prove $P((\alpha * \beta))$ for any of the binary connective. (i.e. any of $\neg$, ^, v, $\implies, \iff$ )

   $\therefore$ concludes that by $POSI$, that $P(\phi)$ holds for all WFPF, $\phi$.


### *Example:* Structural Induction 

[^ note ]: from *Slide 38-39*

Prove that every WFPF has an equal number of '(' and ')'.

*Solution:* Let $ \phi $  be any *Well-formed Propositional Formula*. Proof is by **Structural Induction** on $ \phi $.

Let $ R(\phi)$ be the property: $\phi$ has an equal number of '(' and ')' symbols. $ \checkmark $ 

*Notation:* For any formula $ \phi $, let $op(\phi)$ be the # of '(' and let $ cl(\phi)$ be the # of ')' in $ \phi $.

Then, we can rewrite $R(\phi) \rightarrow op(\phi) = cl(\phi)$

<u>Base Case:</u> *($\phi$ is $p$, for some propositional variable $p$)* 

Here, $op(\phi) = cl(\phi) \implies R(\phi)​$ holds. $\checkmark​$ 

<u>induction Step:</u> *2 sub-cases*:

1. $\phi$ is $(\neg \alpha)$ for some WFPF $\alpha$  [^ NOTE: OMITTED FROM THE SLIDES ]

   *Induction Hypothesis:* $R(\alpha)$ in other words $op(\alpha) = cl(\alpha)$ (*Hypothesis*) $\checkmark $.  Then, $op(\phi) = 1 + op(\alpha) = 1 + cl(\alpha) = cl(\phi)$  .

   Thus, $R(\phi)$ holds. $\checkmark$ 

2. $\phi​$ is ($\alpha * \beta​$) for some WFPF $\alpha , \beta ​$ and some binary connective $ * ​$ .

   *Induction Hypothesis:* $R(\alpha)$ and $R(\beta)$, in other words, $op(\alpha) = cl(\alpha)$ and $op(\beta) = cl(\beta)$. $\checkmark$

   Then: $op(\phi) = cl(\phi)$ (*need to be proved*).
   $$
   \begin{align} op(\phi) = 1 + op(\alpha) + op(\beta) \\
   = 1 + cl(\alpha) + cl(\beta) \leftarrow (Applying \ the \ I.H.) \\
   = cl(\phi) \end{align}
   $$
   Thus, $R(\phi)$ holds.

   Therefore by the *Principle of Structural Induction*, $R(\phi)$ holds for add formulae $\phi$.

[^ NOTE ]: All the **checkmarks** $ \checkmark $ indicate where the marks are given.


