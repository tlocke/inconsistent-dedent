Title: Haskell wikibook: Type basics II
Date: 2016-04-10 08:13
Author: Tony
Slug: haskell-wikibook-type-basics-ii
Status: published

Here are my answers for the chapter called Next Steps:  

> We cheated a little when moving from the second version of `pts` to the third one: they do not do exactly the same thing. Can you spot what the difference is?

>     pts :: Int -> Int
>     pts 1 = 10
>     pts 2 = 6
>     pts 3 = 4
>     pts 4 = 3
>     pts 5 = 2
>     pts 6 = 1
>     pts _ = 0

  

<div>

<div class="mw-highlight mw-content-ltr" dir="ltr">

>     pts :: Int -> Int
>     pts 1 = 10
>     pts 2 = 6
>     pts x
>         | x <= 6    = 7 - x
>         | otherwise = 0

        Gives different answers if the parameter to the function is negative.  
  
And the chapter Simple Input and Output:  
  
> Write a program which asks the user for the base and height of a right angled triangle, calculates its area, and prints it to the screen. The interaction should look something like:  
>
>     The base?
>     3.3
>     The height?
>     5.4
>     The area of that triangle is 8.91
>
> You will need to use the function `read` to convert user strings like "3.3" into numbers like 3.3 and the function `show` to convert a number into string.

  
<samp>main = do  
        putStrLn "The base?"  
        b &lt;- getLine  
        putStrLn "The height?"  
        h &lt;- getLine  
        let m = "The area of that triangle is "  
        putStrLn (m ++ (show (area (read b) (read h))))  
  
area b h = b \* h / 2 </samp>

</div>

</div>

  

     

     

> Write a program that asks the user for his or her name. If the name is one of Simon, John or Phil, tell the user that you think Haskell is a great programming language. If the name is Koen, tell them that you think debugging Haskell is fun (Koen Classen is one of the people who works on Haskell debugging); otherwise, tell the user that you don't know who he or she is.  
> (As far as syntax goes there are a few different ways to do it; write at least a version using `if` / `then` / `else`.)

  
<samp>main = do  
        putStrLn "What's your name?"  
        n &lt;- getLine  
        putStrLn (resp n)  
  
{-  
resp :: String -&gt; String  
resp n   
        | elem n \["Simon", "John", "Phil"\] = "Haskell is marvelous!"  
        | n == "Koen" = "Debugging Haskell is fun."  
        | otherwise = "Name not recognized."  
-}  
  
resp n = if elem n \["Simon", "John", "Phil"\]  
        then "Haskell is marvelous!"  
        else if n == "Koen"  
                then  
                        "Debugging Haskell is fun."  
                else  
                        "Name not recognized."  
  </samp>  

+-----------------------------------+-----------------------------------+
| sweet                             | unsweet                           |
+===================================+===================================+
| <div                              | <div                              |
| class="mw-highlight mw-content-lt | class="mw-highlight mw-content-lt |
| r"                                | r"                                |
| dir="ltr">                        | dir="ltr">                        |
|                                   |                                   |
|      do name <- getLine           |      do name <- getLine           |
|         let loudName = makeLoud n |         let loudName = makeLoud n |
| ame                               | ame                               |
|         putStrLn ("Hello " ++ lou |         in  do putStrLn ("Hello " |
| dName ++ "!")                     |  ++ loudName ++ "!")              |
|         putStrLn (                |                putStrLn (         |
|             "Oh boy! Am I excited |                    "Oh boy! Am I  |
|  to meet you, "                   | excited to meet you, "            |
|                 ++ loudName)      |                        ++ loudNam |
|                                   | e)                                |
| </div>                            |                                   |
|                                   | </div>                            |
+-----------------------------------+-----------------------------------+

+-----------------------------------------------------------------------+
| Exercises                                                             |
+=======================================================================+
| 1.  Why does the unsweet version of the let binding require an extra  |
|     `do` keyword?\                                                    |
|     Because an 'in' clause can contain any Haskell, so we have to use |
|     the 'do' keyword to say that we're going to execute actions.      |
| 2.  Do you always need the extra `do`?\                               |
|     Only if you're doing actions.                                     |
| 3.  (extra credit) Curiously, `let` without `in` is exactly how we    |
|     wrote things when we were playing with the interpreter in the     |
|     beginning of this book. Why is it ok to omit the `in` keyword in  |
|     the interpreter but needed (outside of *do* blocks) in a source   |
|     file?\                                                            |
|     Perhaps because lines entered in the interpreter are implicitly   |
|     within a 'do' block.                                              |
+-----------------------------------------------------------------------+

  

</p>

