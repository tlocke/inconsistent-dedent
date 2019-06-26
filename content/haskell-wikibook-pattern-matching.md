Title: Haskell Wikibook: Pattern Matching
Date: 2016-04-24 08:33
Author: Tony
Slug: haskell-wikibook-pattern-matching
Status: published

Here are my answers to the exercises in the [Haskell Wikibook: Pattern Matching](https://en.wikibooks.org/wiki/Haskell/Pattern_matching) chapter:  
  

> 1.  Test the flawed `h` function above in GHCi, with arguments equal to and different from 1. Then, explain what goes wrong.  
>       
>     The following code:  
>       
>
>         k = 1
>
>         h :: Int -> Bool
>         h k = True
>         h _ = False
>
>       
>     won't compile because the `k` that's defined to equal 1 is different from the `k` in the pattern. The two patterns for `h` overlap, they both match everything, one is anonymous and one is bound to `k`.  
>       
>
> 2.  In this section about pattern matching with literal values, we made no mention of the boolean values `True` and `False`, but we can do pattern matching with them as well, as demonstrated in the [Next steps](https://en.wikibooks.org/wiki/Haskell/Next_steps#Introducing_pattern_matching "Haskell/Next steps") chapter. Can you guess why we omitted them? (Hint: is there anything distinctive about the way we write boolean values?)  
>       
>     The literal values True and False begin with capital letters, and so could be confused with Types or Constructors.

  

> Implement `scanr`, as in the exercise in [Lists III](https://en.wikibooks.org/wiki/Haskell/Lists_III#Scans "Haskell/Lists III"), but this time using an as-pattern.  
>   
>
>     myScanr :: (a -> b -> b) -> b -> [a] -> [b]
>     myScanr f n l = foldr g [n] l
>             where
>             g x list@(y:ys) = (f x y) : list

</p>

