Title: Haskell Wikibook: More on functions
Date: 2016-09-25 07:12
Author: Tony
Slug: haskell-wikibook-more-on-functions
Status: published

The questions for this chapter were:  

> Exercises  
>
> -   Lambdas are a nice way to avoid defining unnecessary separate functions. Convert the following let- or where-bindings to lambdas:
>     -   `map f xs where f x = x * 2 + 3`

 map (\\ x -&gt; x \* 2 + 3) xs  

> -   -   `let f x y = read x + y in foldr f 1 xs`
>
foldr (\\ x y -&gt; read x + y) 1 xs  

> -   -   Sections are just syntactic sugar for lambda operations. I.e. `(+2)` is equivalent to `\x -> x + 2`. What would the following sections 'desugar' to? What would be their types?
>     -   `(4+)`

\\x -&gt; 4 + x  

> -   -   `` (1 `elem`) ``
>
\\x -&gt; elem 1 x  

> -   -   `` (`notElem` "abc") ``
>
 \\x -&gt; notElem x "abc"  

</p>

