Title: Haskell Wikibook: Lists III
Date: 2016-04-17 11:32
Author: Tony
Slug: haskell-wikibook-lists-iii
Status: published

Reading the Haskell Wikibook, Lists III chapter, I can't get my head round the idea that since Haskell has lazy evaluation, a foldr can be used on infinite lists. Here's foldr:  
  

    foldr            :: (a -> b -> b) -> b -> [a] -> b
    foldr f acc []     = acc
    foldr f acc (x:xs) = f x (foldr f acc xs)

     

     

    say f is (:) and acc is [] then

     

    foldr (:) [] [1..] is:

     

    (:) 1 (foldr (:) [] [2..])

    (:) 1 ((:) 2 (foldr (:) [] [3..])) 

    (:) 1 ((:) 2 ((:) 3 (foldr (:) [] [4..])))

    Okay, so I can see that since Haskell has lazy evaluation you can write:

    take 10 (foldr (:) [] [1..])

    and it'll come out with:

    [1,2,3,4,5,6,7,8,9,10]

    and foldl is:

    foldl            :: (a -> b -> a) -> a -> [b] -> a
    foldl f acc []     =  acc
    foldl f acc (x:xs) =  foldl f (f acc x) xs

    so if f is (:) and acc is [] then:

    foldl (:) [] [1..]

    foldl (:) [1] [2..]

    foldl (:) [1,2] [3..] 

    so result isn't given element by element, it has to be calculated all in one go. So:

    take 10 (foldl (:) [] [1..])

[will never halt. So I can see all that. What I can't comprehend is that foldr applies f in a right-associative fashion. Now in my mind, right-associative means that in a sequence of terms, the right hand one is evaluated first. So in an infinite list that would mean starting at infinity which is impossible! So:]{.p}  
  
[1 : 2 : 3 : 4 : \[\]]{.p}  
  
[1 : (2 : (3 : (4 : \[\]))]{.p}  
  
[So I think my conception of right-associative is incorrect. It should be that terms are grouped from the right, not necessarily evaluated from the right. In a language with eager evaluation it would be evaluated from the innermost group working outwards, but in a language with lazy evaluation the innermost group is evaluated last.]{.p}  
  
[I've sort of got it. I suppose that even if I don't understand it I'm familiar with it!]{.p}  
  
[Another thing that strikes me is that compared to Python there are loads of functions and variations of functions in Prelude (in comparison to Python's builtin's). Perhaps this is because Haskell is statically types, which makes it harder to have a single function that fits all types.]{.p}  

     

[Here are my answers to Haskell Wikibook: Lists III.]{.p}  

> 1.  Define the following functions recursively (like the definitions for `sum`, `product` and `concat` above), then turn them into a fold:
>     -   `and :: [Bool] -> Bool`, which returns True if a list of Bools are all True, and False otherwise.  
>           
>
>             myAndRec :: [Bool] -> Bool
>             myAndRec [] = True
>             myAndRec (x:xs) = x && myAndRec xs
>
>         And using folds:  
>
>             myAnd :: [Bool] -> Bool
>             myAnd l = foldr (&&) True l
>
>     -   `or :: [Bool] -> Bool`, which returns True if any of a list of Bools are True, and False otherwise.  
>           
>
>             myOrRec :: [Bool] -> Bool
>             myOrRec [] = True
>             myOrRec (x:xs) = x || myOrRec xs
>
>             myOr :: [Bool] -> Bool
>             myOr l = foldr (||) True l
>
>           
>
> 2.  Define the following functions using `foldl1` or `foldr1`:
>     -   `maximum :: Ord a => [a] -> a`, which returns the maximum element of a list (hint: `max :: Ord a => a -> a -> a` returns the maximum of two values).  
>           
>
>             myMaximum :: Ord a => [a] -> a
>             myMaximum xs = foldr1 max xs
>
>           
>
>     -   `minimum :: Ord a => [a] -> a`, which returns the minimum element of a list (hint: `min :: Ord a => a -> a -> a` returns the minimum of two values).  
>           
>
>             myMinimum :: Ord a => [a] -> a
>             myMinimum xs = foldr1 min xs
>
>           
>
> 3.  Use a fold (*which one?*) to define `reverse :: [a] -> [a]`, which returns a list with the elements in reverse order.  
>       
>
>         myReverse :: [a] -> [a]
>         myReverse xs = foldr (\ x y -> y ++ [x]) [] xs
>
> <dl>
> <dd>
> Note that all of these are Prelude functions, so they will be always close at hand when you need them. (Also, that means you must use slightly different names in order to test your answers in GHCi.)
>
> </dd>
> </dl>

  

> 1.  Write your own definition of `scanr`, first using recursion, and then using `foldr`. Do the same for `scanl` first using recursion then `foldl`.  
>       
>
>         myScanrRec :: (a -> b -> b) -> b -> [a] -> [b]
>         myScanrRec f n [] = [n]
>         myScanrRec f n [x:xs] = (f x (head r)) : r
>                 where
>                 r = myScanrRec f n xs
>
>         myScanrFold :: (a -> b -> b) -> b -> [a] -> [b]
>         myScanrFold f n l = foldr (\x y -> (f x (head y)) : y) [n] l
>
>         myScanlRec :: (a -> b -> a) -> a -> [b] -> [a]
>         myScanlRec f n [] = [n]
>         myScanlRec f n l = r ++ [f (last r) (last l)] 
>                 where
>                 r = myScanlRec f n (init l)
>
>         myScanlFold :: (a -> b -> a) -> a -> [b] -> [a] 
>         myScanlFold f n l = foldl (\x y -> x ++ [f (last x) y]) [n] l
>
>       
>
> 2.  Define the following functions:
>     -   `factList :: Integer -> [Integer]`, which returns a list of factorials from 1 up to its argument. For example, `factList 4 = [1,2,6,24]`.  
>           
>
>             factList :: Integer -> [Integer]
>             factList n = scanl1 (*) [1..n]                 
>
  

1.  Write a `returnDivisible :: Int -> [Int] -> [Int]` function which filters a list of integers retaining only the numbers divisible by the integer passed as first argument. For integers x and n, x is divisible by n if `(mod x n) == 0` (note that the test for evenness is a specific case of that).  
     

        returnDivisible :: Int -> [Int] -> [Int] 
        returnDivisible n ns = [x | x <- ns, mod x n == 0]

      

2.  Write a function `choosingTails :: [[Int]] -> [[Int]]` using list comprehension syntax with appropriate guards (filters) for empty lists returning a list of tails following a head bigger than 5:

    <div class="mw-highlight mw-content-ltr" dir="ltr">

        choosingTails  [[7,6,3],[],[6,4,2],[9,4,3],[5,5,5]]
        -- [[6,3],[4,2],[4,3]]

    </div>

      

        choosingTails :: [[Int]] -> [[Int]]
        choosingTails nss = [tail ns | ns &lt- nss, length ns > 0, head ns > 5]

      

3.  Does the order of guards matter? You may find it out by playing with the function of the preceding exercise.  
     
   Yes, the order does matter. In the example above the test for empty lists must come first otherwise the subsequent head function would fail.
4.  Over this section we've seen how list comprehensions are essentially syntactic sugar for `filter` and `map`. Now work in the opposite direction and define alternative versions of the `filter` and `map` using the list comprehension syntax.  
     

        myFilter :: (a -> Bool) -> [a] -> [a]
        myFilter f xs = [x | x <- xs, f x]


        myMap :: (a -> b) -> [a] -> [b]
        myMap f xs = [f x | x <- pre="" xs="">

      

5.  Rewrite `doubleOfFirstForEvenSeconds` using `filter` and `map` instead of list comprehension.  
     

        doubleOfFirstForEvenSeconds :: [(Int, Int)] -> [Int]
        doubleOfFirstForEvenSeconds ps = map (\(i, j) -> 2 * i) (filter (\(x, y) -> (mod y 2) == 0) ps)

</p>

