Title: Learning Haskell from the Wikibook
Date: 2016-04-10 05:05
Author: Tony
Slug: learning-haskell-from-wikibook
Status: published

I thought I should learn Haskell as I'm clueless about functional programming and haven't used a statically types language for ages. Anyway, I'm learning it from the [Haskell Wikibook](https://en.wikibooks.org/wiki/Haskell). Throughout they give exercises and here are my  answers so far:  
  

-   Explain how GHCi evaluates `quadruple 5`.

The quadruple function is defined as:  
  

    double x    = 2 * x

    quadruple x = double (double x)

     

[First, Haskell will substitute definition of double in the quadruple function to give:]{.p}  

    2 * (2 * x)

[Then it will substitute 5 for x:]{.p}  

    2 * (2 * 5)

[Brackets are evaluated first:]{.p}  

    2 * 10

    20

  

-   Define a function that subtracts 12 from half its argument.

`half x = x / 2hmtwelve x = half x - 12`  
  

-   Write a function to calculate the volume of a box.  
     
   `volbox h w l = h * w * l`

<!-- -->

-   Approximately how many stones are the famous pyramids at Giza made up of? Hint: you will need estimates for the volume of the pyramids and the volume of each block.  
     
   Assuming a bottom edge of the pyramid is 100m, and a block is a cube of side 0.5m, the number of stones is:  
   `100 ^ 3 / 2 / 0.5^3`  
   which is 4,000,000 stones. The actual answer is 2.3m, so I don't think my estimate is too bad. 
-   Write a function to calculate the volume of a cylinder. The volume of a cylinder is the area of the base, which is a circle (you already programmed this function in this chapter, so reuse it) multiplied by the height.  
   `areaCirc r = pi * r^2volCyl r h = areaCirc r * h`
-   Try using `:type` on the literal value `"H"` (notice the double quotes). What happens? Why?  
   The interpreter reports: `"H" :: [Char]` because the double quotes mean it's a string of length 1.
-   Try using `:type` on the literal value `'Hello World'` (notice the single quotes). What happens? Why?  
   The interpreter gives an error, because single quotes denote a single character, but we've entered more than one. 
-   What are the types of the following functions? For any functions involving numbers, you can just pretend the numbers are Ints.  
   -   The `negate` function, which takes an Int and returns that Int with its sign swapped. For example, `negate 4 = -4`, and `negate (-2) = 2 `  
       `negate :: Int -> Int`
    -   The `(||)` function, pronounced 'or', that takes two Bools and returns a third Bool which is True if either of the arguments were, and False otherwise.  
       `(||) :: Bool -> Bool -> Bool`
    -   A `monthLength` function which takes a Bool which is True if we are considering a leap year and False otherwise, and an Int which is the number of a month; and returns another Int which is the number of days in that month.  
       `monthLength :: Bool -> Int -> Int`
    -   `f x y = not x && y`  
       `f :: Bool -> Bool -> Bool`
    -   `g x = (2*x - 1)^2`  
       `g :: Int -> Int`
-   Would the following piece of Haskell work: `3:[True,False]`? Why or why not?  
   No it wouldn't work because the resulting list would have a mix of types which isn't allowed.
-   Write a function `cons8` that takes a list as an argument and conses `8` (at the beginning) on to it.  
   `cons8 l = 8:l`  
   Test it out on the following lists by doing:
    1.  `cons8 []`  
       `[8]`
    2.  `cons8 [1,2,3]`  
       `[8, 1, 2, 3]`
    3.  `cons8 [True,False]`  
       Error, lists can't have a mix of types.
    4.  `let foo = cons8 [1,2,3]`  
       `cons8 foo`  
       `[8, 8, 1, 2, 3]`
-   Adapt the above function in a way that `8` is at the end of the list. (Hint: recall the concatenation operator `++` from the previous chapter.)  
   `cat8 l = l ++ [8]`
-   Write a function that takes two arguments, a list and a thing, and conses the thing onto the list. You can start out with:  
   `let myCons list thing = thing:list`

#### Lists And Tuples

1.  Which of these are valid Haskell and which are not? Rewrite in cons notation.
    1.  `[1,2,3,[]]`  
       Not valid, because not of the same type.  
       `1:2:3:[]:[]`  
   2.  `[1,[2,3],4]`  
       Not valid, because not of the same type.  
       1:(2:3:\[\]):4:\[\]
    3.  `[[1,2,3],[]]`  
       Valid, because the empty list could be an empty list of integers! `(1:2:3:[]):[]:[]`
2.  Which of these are valid Haskell, and which are not? Rewrite in comma and bracket notation.
    1.  `[]:[[1,2,3],[4,5,6]]`  
       Valid because the empty list could be an empty list of integers. `[[], [1, 2, 3], [4, 5, 6]]`
    2.  `[]:[]`  
       Valid. Since there's only one inner list, the outer list must contain lists of the same type.  
       `[[]]`
    3.  `[]:[]:[]`  
       Valid because an empty list could be of any type. `[[], []]`
    4.  `[1]:[]:[]`Valid, because an empty list could hold items of any type. `[[1], []]`
    5.  `["hi"]:[1]:[]`  
       Not valid. A list of strings is a different type to a list of integers.  
       `[["hi"], [1]]`
3.  Can Haskell have lists of lists of lists? Why or why not?  
   Yes, as long as each item in a list is of the same type.
4.  Why is the following list invalid in Haskell?  
   1.  `[[1,2],3,[4,5]]`  
       Because the outer list has items of more than one type.

<!-- -->

1.  Write down the 3-tuple whose first element is 4, second element is "hello" and third element is True.  
   `(4, "hello", True)`
2.  Which of the following are valid tuples?
    1.  `(4, 4)`  
       Valid.
    2.  `(4, "hello")`  
       Valid.
    3.  `(True, "Blah", "foo")`  
       Valid.
    4.  `()`  
       Valid.
3.  Lists can be built by consing new elements onto them. Cons a number onto a list of numbers, you will get back a list of numbers. There is no such way to build up tuples.
    1.  Why do you think that is?  
       For any type consed to a list, the returned type will be a list of that type, so the function is general. With adding an element to a tuple, an entirely new type will be created, so it isn't so general.
    2.  For the sake of argument, say that there was such a function. What would you get if you "consed" something on a tuple?  
       You'd get a new type.

<!-- -->

1.  Which of these are valid Haskell, and why?
    -   `1:(2,3)`  
       Invalid; can't cons onto a tuple.
    -   `(2,4):(2,3)`  
       Invalid; can't cons onto a tuple.
    -   `(2,4):[]`  
       Valid. Can cons onto a list.
    -   `[(2,4),(5,5),('a','b')]`  
       Invalid. The elements of a list must all be of the same type.
    -   `([2,4],[2,2])`Valid. The elements of the list are all of the same type. 

<!-- -->

1.  Use a combination of `fst` and `snd` to extract the 4 from the tuple `(("Hello", 4), True)`.  
   snd (fst (("Hello", 4), True))
2.  Normal chess notation is somewhat different to ours: it numbers the rows from 1-8 and the columns a-h; and the column label is customarily given first. Could we label a specific point with a character and a number, like `('a', 4)`? What important difference with lists does this illustrate?  
   Yes, we could represent a square with ('a', 4). A tuple can contain elements of different types.
3.  Write a function which returns the head and the tail of a list as the first and second elements of a tuple.  
   `fTuple list = (head list, tail list)`
4.  Use `head` and `tail` to write a function which gives the fifth element of a list. Then, make a critique of it, pointing out any annoyances and pitfalls you notice.  
   `el5 l = head (tail (tail (tail (tail l))))` It's quite verbose. Also it fails with any list with fewer than 5 elements. 

Give type signatures for the following functions:  

1.  The solution to the third exercise of the previous section ("... a function which returns the head and the tail of a list as the first and second elements of a tuple").  
   `fTuple :: [a] -> (a, a)`
2.  The solution to the fourth exercise of the previous section ("... a function which gives the fifth element of a list").  
   `el5 :: [a] -> a `
3.  `h x y z = chr (x - 2)` (remember we discussed chr in the previous chapter). `h :: a -> b -> c -> char`

  

</p>

