Title: Haskell Wikibook: Recursion
Date: 2016-04-10 14:00
Author: Tony
Slug: haskell-wikibook-recursion
Status: published

Here are my answers for the Recursion chapter of the Haskell Wikibook:  

> 1.  Type the factorial function into a Haskell source file and load it into GHCi.
> 2.  Try examples like `factorial 5` and `factorial 1000`.^[\[3\]](https://en.wikibooks.org/wiki/Haskell/Recursion#cite_note-3)^
>     -   What about `factorial (-1)`? Why does this happen?

Calling factorial (-1) will never stop because the argument to the factorial function always decreases which means it never gets to zero, the stopping condition.  

> 1.  The *double factorial* of a number n is the product of *every other* number from 1 (or 2) up to n. For example, the double factorial of 8 is 8 × 6 × 4 × 2 = 384, and the double factorial of 7 is 7 × 5 × 3 × 1 = 105. Define a `doublefactorial` function in Haskell.

<samp>doubleFactorial 0 = 1  
doubleFactorial 1 = 1  
doubleFactorial n = n \* doubleFactorial (n - 2) </samp>  
<samp>  
</samp>  

> 1.  Expand out the multiplication 5 × 4 similarly to the expansion we used above for `factorial 3`.  
>     -   4 isn't 0 or 1 so calculate (mult 5 3) + 5
>         -   3 isn't 0 or 1 so calculate (mult 5 2) + 5
>             -   2 isn't 0 or 1 so calculate (mult 5 1) + 5
>                 -   For 1, return 5
>
>                 Continue the calculation for 2, which gives 10.
>
>             Continue the calculation for 3 which gives 15.
>
>         Continue the calculation for 4 which gives 20.

> 1.  Define a recursive function `power` such that `power x y` raises `x` to the `y` power.  
>
>         power _ 0 = 1
>         power x 1 = x
>         power x y = power x (y - 1) * x
>
> 1.  You are given a function `plusOne x = x + 1`. Without using any other `(+)`s, define a recursive function `addition` such that `addition x y` adds `x` and `y` together.

<samp>addition x 0 = x  
addition x y = addition (plusOne x) (y - 1)</samp>  

> 1.  (Harder) Implement the function `log2`, which computes the integer log (base 2) of its argument. That is, `log2` computes the exponent of the largest power of 2 which is less than or equal to its argument. For example, `log2 16 = 4`, `log2 11 = 3`, and `log2 1 = 0`. (Small hint: read the last phrase of the paragraph immediately preceding these exercises.)  
>       
>
>         log2 x = higher x 0
>                 where
>                 higher x n
>                         | power 2 n > x = n - 1
>                         | otherwise     = higher x (n + 1)
>
  
Give recursive definitions for the following list-based functions. In each case, think what the base case would be, then think what the general case would look like, in terms of everything smaller than it. (Note that all of these functions are available in Prelude, so you will want to give them different names when testing your definitions in GHCi.)  

1.  `replicate :: Int -> a -> [a]`, which takes a count and an element and returns the list which is that element repeated that many times. E.g. `replicate 3 'a' = "aaa"`. (Hint: think about what replicate of anything with a count of 0 should be; a count of 0 is your 'base case'.)  
     

        myReplicate 0 _ = []
        myReplicate n a = a : myReplicate (n - 1) a

      

2.  `(!!) :: [a] -> Int -> a`, which returns the element at the given 'index'. The first element is at index 0, the second at index 1, and so on. Note that with this function, you're recursing *both* numerically and down a list^[\[5\]](https://en.wikibooks.org/wiki/Haskell/Recursion#cite_note-5)^.  
     

        myIndex l 0 = head l
        myIndex l i = myIndex (tail l) (i - 1)

      

3.  (A bit harder.) `zip :: [a] -> [b] -> [(a, b)]`, which takes two lists and 'zips' them together, so that the first pair in the resulting list is the first two elements of the two lists, and so on. E.g. `zip [1,2,3] "abc" = [(1, 'a'), (2, 'b'), (3, 'c')]`. If either of the lists is shorter than the other, you can stop once either list runs out. E.g. `zip [1,2] "abc" = [(1, 'a'), (2, 'b')]`.

    <dl>
    <dd>
      

    </dd>
    </dl>
        myZip [] l2 = []
        myZip l1 [] = []
        myZip l1 l2 = (head l1, head l2) : myZip (tail l1) (tail l2)

      

4.  Define `length` using an auxiliary function and an accumulating parameter, as in the loop-like alternate version of `factorial`.  

        myLength l = len l 0
                where
                len [] n = n
                len l n = len (tail l) (n + 1)

  
  
  
  

</p>

