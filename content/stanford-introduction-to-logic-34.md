Title: Stanford Introduction To Logic: 3.4
Date: 2016-12-10 08:30
Author: Tony
Slug: stanford-introduction-to-logic-34
Status: published

I'm learning about logic by going through the excellent [Stanford Introduction to Logic](http://logic.stanford.edu/intrologic/notes/notes.html), as part of writing a [maths tutorial](http://maths.tlocke.org.uk/). Here I'm working through [Exercise 3.4 - Propositional Entailment](http://logic.stanford.edu/intrologic/exercises/exercise_03_04.html). Let me know if you disagree with any of my answers:  
  

> Let Γ and Δ be sets of sentences in Propositional Logic, and let φ and ψ be individual sentences in Propositional Logic. State whether each of the following statements is true or false.

> a\. If Γ ⊨ φ and Δ ⊨ φ, then Γ ∩ Δ ⊨ φ.

I'll show it's false by providing a counterexample. If P is an atomic formula:  
  
Γ = {(P and not P), P}  
Δ = {(φ and not φ), P}  
  
Since Γ and Δ contain an unsatisfiable formula they entail everything, so Γ ⊨ φ and Δ ⊨ φ are both true. Also:  
  
Γ ∩ Δ = {P}  
  
The formula (P implies φ) is not valid, and so it's false that Γ ∩ Δ ⊨ φ.  

> b\. If Γ ⊨ φ and Δ ⊨ φ, then Γ ∪ Δ ⊨ φ.

If Γ = {P1, P2, P3, ...} then:  
  
(P1 and P2 and P3 and ...) implies φ  
  
is valid. If Δ = {Q1, Q2, Q3, ...}  
  
(P1 and P2 and P3 and ...) and (Q1 and Q2 and Q3 and ...) implies φ  
  
must also be valid since for any interpretation, adding more 'and' terms to a formula can never make it true if it was false. If adding the Q terms only introduces false interpretations on the left hand side of the 'implies' then the whole formula will remain valid. So:  
  
Γ ∩ Δ ⊨ φ  
  
is true.  

> c\. If Γ ⊨ φ and Δ ⊭ φ, then Γ ∪ Δ ⊨ φ.

Using the same reasoning as above, if:  
  
Γ = {P1, P2, P3, ...}  
  
then:  
  
(P1 and P2 and P3 and ...) implies φ  
  
is valid. If:  
  
Δ = {Q1, Q2, Q3, ...}  
  
then:  
  
(P1 and P2 and P3 and ...) and (Q1 and Q2 and Q3 and ...) implies φ  
  
must also be valid since for any interpretation, adding more 'and' terms to a formula can never make it true if it was false. If adding the Q terms only introduces false interpretations on the left hand side of the 'implies' then the whole formula will remain valid. So:  
  
Γ ∪ Δ ⊨ φ  
  
is true.  

> d\. If Γ ⊭ ψ, then Γ ⊨ ¬ψ.

If:  
  
Γ = {P1, P2, P3, ...}  
  
then if Γ ⊭ ψ then:  
  
(P1 and P2 and P3 and ...) implies ψ  
  
is not valid.  
  
then by the unsatisfiability theorem:  
  
P1 and P2 and P3 and ... and ψ  
  
is unsatisfiable.  

> e\. If Γ ⊨ ¬ψ, then Γ ⊭ ψ.

  
Using proof by counterexample. If:  
  
Γ = {(ψ and not ψ)} then:  
  
 (ψ and not ψ) implies ¬ψ  
  
is valid, because (ψ and not ψ) is unsatisfiable. So:  
  
(ψ and not ψ) implies ψ  
  
is also valid. And so:  
  
Γ ⊨ ψ  
  
is true, which means:  
  
Γ ⊭ ψ  
  
is false.

</p>

