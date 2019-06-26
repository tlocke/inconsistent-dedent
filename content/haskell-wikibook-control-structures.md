Title: Haskell Wikibook: Control Structures
Date: 2016-09-25 05:52
Author: Tony
Slug: haskell-wikibook-control-structures
Status: published

Well I can see that I haven't done any learning of Haskell for ages. Now that I look back at it, it all looks like gobbledigook to me. Well I probably need to get on with doing some questions:  
  

> Exercises  
>
> 1.  Redo the "Haskell greeting" exercise in [Simple input and output/Controlling actions](https://en.wikibooks.org/wiki/Haskell/Simple_input_and_output#Controlling_actions "Haskell/Simple input and output"), this time using a `case` statement.

  
myDoGuessing num = do  
        putStrLn "Enter your guess:"  
        guess &lt;- getLine  
        case compare (read guess) num of  
                LT -&gt; do putStrLn "Too low!"  
                         myDoGuessing num  
                GT -&gt; do putStrLn "Too high!"  
                         myDoGuessing num  
                EQ -&gt; do putStrLn "You Win!"  
  

> 1.  What does the following program print out? And why?
>
> <div class="mw-highlight mw-content-ltr" dir="ltr">
>
>     main =
>      do x <- getX
>         putStrLn x
>
>     getX =
>      do return "My Shangri-La"
>         return "beneath"
>         return "the summer moon"
>         return "I will"
>         return "return"
>         return "again"
>
> </div>

 I thought it would print out 'again'. The reason is that getX executes a series of actions and the last one is what the function evaluates to.  
  

> <div class="mw-highlight mw-content-ltr" dir="ltr">
>
> </div>

</p>

