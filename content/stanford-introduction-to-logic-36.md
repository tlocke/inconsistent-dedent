Title: Stanford Introduction To Logic 3.6
Date: 2017-06-24 06:35
Author: Tony
Slug: stanford-introduction-to-logic-36
Status: published

Here are my answers to [Stanford Introduction To Logic 3.6](http://logic.stanford.edu/intrologic/exercises/exercise_03_06.html).  

> Logical equivalence, logical entailment, and logical consistency are related to each other in interesting ways, but they are not identical. Answer the following true or false questions about the relationships between these concepts.

  

> a\. If φ is equivalent to ψ, then φ entails ψ.

If φ is equivalent to ψ, then φ can be written wherever ψ appears so:  
  
φ entails φ  
  
which (by the deduction theorem) is true if:  
  
φ → φ  
  
is valid. It is valid and so a. is true.  
  

> b\. If φ is equivalent to ψ, then φ is consistent with ψ.

If the theory {φ, ψ} is consistent, then:  
  
φ ∧ ψ  
  
is satisfiable. If φ is equivalent to ψ, then φ can be written wherever ψ appears so:  
  
 φ ∧ φ  
  
since φ ∧ φ is equivalent to φ, we can say that the theory is only consistent if φ is satisfiable. So b. is false.  
  

> c\. If φ entails ψ, then φ is equivalent to ψ.

Disprove by counterexample. If φ entails ψ then:  
  
φ → ψ  
  
is valid. If φ is (P ∧ ¬P) and ψ = P then (φ → ψ) is valid and so (φ entails ψ) is true. But (P ∧ ¬P) is not equivalent to P, so φ is not equivalent to ψ, and so c. is false.  

> d\. If φ entails ψ, then φ is consistent with ψ.

Disprove by counterexample. If φ entails ψ then (φ → ψ) is valid, and if φ is consistent with ψ then (φ ∧ ψ) is satisfiable. If φ is (P ∧ ¬P) and ψ is P then (φ → ψ) is valid, but (φ ∧ ψ) is not satisfiable. Therefore d. is false.  

> e\. If φ is consistent with ψ, then φ is equivalent to ψ.

 Disprove by counterexample. If φ is consistent with ψ then (φ ∧ ψ) is satisfiable. Say If φ is (P ∨ ¬P) and ψ is P, then (φ ∧ ψ) is satisfiable, but φ is not equivalent to ψ, so e. is false.  

> f\. If φ is consistent with ψ, then φ entails ψ.

 Disprove by counterexample. If φ is consistent with ψ then (φ ∧ ψ) is satisfiable. If φ entails ψ then (φ → ψ) is valid. But if φ is (P ∨ ¬P) and ψ is P, then (φ ∧ ψ) is satisfiable and (φ → ψ) is not valid, so f. is false.

</p>

