Title: Stanford Introduction To Logic: 3.5
Date: 2017-01-02 07:16
Author: Tony
Slug: stanford-introduction-to-logic-35
Status: published

Here are my answers to [Stanford Introduction To Logic: 3.5](http://logic.stanford.edu/intrologic/exercises/exercise_03_05.html).  

> In each of the following cases, determine whether the given individual sentence is consistent with the given set of sentences.

> a\. {*p* ∨ *q*, *p* ∨ ¬*q*, ¬*p* ∨ *q*} and (¬*p* ∨ ¬*q*)

Using a truth table:  
  

  p   q   p ∨ q   p ∨ ¬q   ¬p ∨ q   ¬p ∨ ¬q
  --- --- ------- -------- -------- ---------
  T   T   T       T        T        F
  F   T   T       F        T        T
  T   F   T       T        F        T
  F   F   F       T        T        T

  
So no, the sentence isn't consistent.  

> b\. {*p* ⇒ *r*, *q* ⇒ *r*, *p* ∨ *q*} and *r*

  p   q   r   p ⇒ r   q ⇒ r   p ∨ q   r
  --- --- --- ------- ------- ------- ---
  T   T   T   T       T       T       T
  F   T   T   T       T       T       T
  T   F   T   T       T       T       T
  F   F   T   T       T       F       T
  T   T   F   F       F       T       F
  F   T   F   T       F       T       F
  T   F   F   F       T       T       F
  F   F   F   T       T       F       F

  
The first interpretation satisfies the formula, so yes it is consistent  

> c\. {*p* ⇒ *r*, *q* ⇒ *r*, *p* ∨ *q*} and ¬*r*

  p   q   r   p ⇒ r   q ⇒ r   p ∨ q   ¬r
  --- --- --- ------- ------- ------- ----
  T   T   T   T       T       T       F
  F   T   T   T       T       T       F
  T   F   T   T       T       T       F
  F   F   T   T       T       F       F
  T   T   F   F       F       T       T
  F   T   F   T       F       T       T
  T   F   F   F       T       T       T
  F   F   F   T       T       F       T

  
The formula is unsatisfiable, so not consistent.  

> d\. {*p* ⇒ *q* ∨ *r*, *q* ⇒ *r*} and *p* ∧ *q*

  p   q   r   p ⇒ q ∨ r   q ⇒ r   p ∧ q
  --- --- --- ----------- ------- -------
  T   T   T   T           T       T
  F   T   T   T           T       F
  T   F   T   T           T       F
  F   F   T   T           T       F
  T   T   F   T           F       T
  F   T   F   T           T       F
  T   F   F   F           F       F
  F   F   F   T           T       F

  
The formula is satisfiable, so consistent.  

> e\. {*p* ⇒ *q* ∨ *r*, *q* ⇒ *r*} and *q* ∧ *r*

  p   q   r   p ⇒ q ∨ r   q ⇒ r   p ∧ q
  --- --- --- ----------- ------- -------
  T   T   T   T           T       T
  F   T   T   T           T       F
  T   F   T   T           T       F
  F   F   T   T           T       F
  T   T   F   T           F       T
  F   T   F   T           T       F
  T   F   F   F           F       F
  F   F   F   T           T       F

  
The formula is satisfiable, so consistent.

</p>

