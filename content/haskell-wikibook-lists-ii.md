Title: Haskell Wikibook: Lists II
Date: 2016-04-16 06:25
Author: Tony
Slug: haskell-wikibook-lists-ii
Status: published

Here are my answers to the Haskell Wikibook: Lists II questions:  
  

> Write the following functions and test them out. Don't forget the type signatures.  
>
> 1.  takeInt returns the first *n* items in a list. So, `takeInt 4 [11,21,31,41,51,61]` returns `[11,21,31,41]`.  
>       
>
>         takeInt :: Integer -> [Integer] -> [Integer]
>         takeInt 1 l = [head l]
>         takeInt n (x:xs) = x : (takeInt (n - 1) xs)
>
>       
>
> 2.  dropInt drops the first *n* items in a list and returns the rest. So, `dropInt 3 [11,21,31,41,51]` returns `[41,51]`.  
>       
>
>         dropInt :: Integer -> [Integer] -> [Integer]
>         dropInt 0 l = l
>         dropInt n (_:xs) = dropInt (n - 1) xs
>
>       
>
> 3.  sumInt returns the sum of the items in a list.  
>       
>
>         sumInt :: [Integer] -> Integer
>         sumInt [] = 0
>         sumInt (x:xs) = x + sumInt xs
>
>       
>
> 4.  scanSum adds the items in a list and returns a list of the running totals. So, `scanSum [2,3,4,5]` returns `[2,5,9,14]`.  
>       
>
>         scanSum :: [Integer] -> [Integer]
>         scanSum (n:ns) = sSum [n] ns
>                 where
>                 sSum r [] = reverse r 
>                 sSum r (x:xs) = sSum ((head r + x):r) xs
>
>       
>
> 5.  diffs returns a list of the differences between adjacent items. So, `diffs [3,5,6,8]` returns `[2,1,2]`. (Hints: one solution involves writing an auxiliary function which takes two lists and calculates the difference between corresponding elements. Alternatively, you might explore the fact that lists with at least two elements can be matched to a `(x:y:ys)` pattern.)  
>       
>
>         diffs :: [Integer] -> [Integer]
>         diffs (x:y:[]) = [y - x] 
>         diffs (x:y:xs) = (y - x) : diffs (y:xs)
>
> The first three functions are in Prelude under the names `take`, `drop`, and `sum`.

  

1.  Use `map` to build functions that, given a list xs of Ints, return:
    -   A list that is the element-wise negation of xs.  
         

            neg :: [Integer] -> [Integer]
            neg [] = [] 
            neg (x:xs) = ((-1) * x) : (neg xs)

          

    -   A list of lists of Ints xss that, for each element of xs, contains the divisors of xs. You can use the following function to get the divisors:

            divisors p = [ f | f <- [1..p], p `mod` f == 0 ]

          
         

            divisors :: Integer -> [Integer]
            divisors p = [ f | f <- -="" 0="" ::="" divs="" f="=" mod="" nteger="" p=""> [[Integer]]
            divs xs = map divisors xs

          

    -   The element-wise negation of xss.  
         

            neg :: [Integer] -> [Integer]
            neg xs = map ((*) (-1)) xs

          

2.  Implement a Run Length Encoding (RLE) encoder and decoder.
    -   The idea of RLE is simple; given some input:

            "aaaabbaaa"

        compress it by taking the length of each run of characters:`(4,'a'), (2, 'b'), (3, 'a')`

    -   The `concat` and `group` functions might be helpful. In order to use `group`, import the Data.List module by typing `:m Data.List` at the ghci prompt or by adding `import Data.List` to your Haskell source code file.  
         

            rleEnc :: String -> [(Int, Char)]
            rleEnc s = map mt (group s)
                    where
                    mt :: [Char] -> (Int, Char)
                    mt xs = (length xs, head xs)


            rleDec :: [(Int, Char)] -> String
            rleDec xs = concat (map expand xs)
                    where 
                    expand (1, c) = [c]
                    expand (n, c) = c : expand ((n - 1), c)

    -   What is the type of your `encode` and `decode` functions?  
         
       See type declarations above.
    -   How would you convert the list of tuples (e.g. `[(4,'a'), (6,'b')]`) into a string (e.g. "4a6b")?  

            rleEnc :: String -> String
            rleEnc s = concat(map tc (rleEncTup s))
                    where
                    tc (n, c) = show n ++ [c]

          

    -   (bonus) Assuming numeric characters are forbidden in the original string, how would you parse that string back into a list of tuples?  
         

            rleDec :: [Char] -> [Char]
            rleDec s = rleDecTup (tuplefy (groupBy gb s))
                    where
                    gb :: Char -> Char -> Bool
                    gb c1 c2 = isDigit c1 == isDigit c2
                    tuplefy :: [[Char]] -> [(Int, Char)]
                    tuplefy [] = []
                    tuplefy (ds:[c]:xs) = (read ds, c) : (tuplefy xs) 

             

<!-- -->

1.  With respect to your solutions to the first set of exercises in this chapter, is there any difference between `scanSum (takeInt 10 [1..])` and `takeInt 10 (scanSum [1..])`?  
     
   Yes, the second one will take forever because it tries to complete the whole list, the first will halt.
2.  Write functions that, when applied to lists, give the *last* element of the list and the list with the last element dropped.  
   This functionality is provided by Prelude through the `last` and `init` functions. Like `head` and `tail`, they blow up when given empty lists.  
     

        myLast :: [a] -> a
        myLast [x] = x
        myLast (x:xs) = myLast xs

        myInit :: [a] -> [a]
        myInit [_] = []
        myInit (x:xs) = x : myInit xs

</p>

