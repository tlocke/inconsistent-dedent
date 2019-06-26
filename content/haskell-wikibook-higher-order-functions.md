Title: Haskell wikibook: Higher-order functions
Date: 2016-09-27 13:36
Author: Tony
Slug: haskell-wikibook-higher-order-functions
Status: published

> Write `insensitive`, such that `quickSort' insensitive dictionary` gives `["a", "for", "have", "I", "Linux", "thing"]`.

insensitive x y = compare (map toLower x) (map toLower y)  
  

> Exercises  
> *(Challenging)* The following exercise combines what you have learned about higher order functions, recursion and I/O. We are going to recreate what is known in imperative languages as a *for loop*. Implement a function  
>
>     for :: a -> (a -> Bool) -> (a -> a) -> (a -> IO ()) -> IO ()
>     for i p f job = -- ???
>
> An example of how this function would be used might be  
>
>     for 1 (<10) (+1) print
>
> which prints the numbers 1 to 9 on the screen.  
> The desired behaviour of `for` is: starting from an initial value `i`, `for` executes `job i`. It then uses `f` to modify this value and checks to see if the modified value `f i` satisfies some condition `p`. If it doesn't, it stops; otherwise, the for loop continues, using the modified `f i` in place of `i`.  
>
> 1.  Implement the for loop in Haskell.

for :: a -&gt; (a -&gt; Bool) -&gt; (a -&gt; a) -&gt; (a -&gt; IO ()) -&gt; IO ()  
for i p f job  
        | p i       = do  
                                job i  
                                for (f i) p f job  
        | otherwise = return ()  

> 1.  The paragraph just above gives an imperative description of the for loop. Describe your implementation in more functional terms.

The for loop is a recursive function that returns the empty action for the base case if the condition being met. For other cases it executes the action, and then calls itself with the next i, which is found using f i.  

> Some more challenging exercises you could try  
>
> 1.  Consider a task like "print the list of numbers from 1 to 10". Given that `print` is a function, and we can apply it to a list of numbers, using `map` sounds like the natural thing to do. But would it actually work?

No, because the 'print' function returns an action, and so would need to be sequenced with the 'do' command.  
  

> 1.  Implement a function `sequenceIO :: [IO a] -> IO [a]`. Given a list of actions, this function runs each of the actions in order and returns all their results as a list.

sequenceIO :: \[IO a\] -&gt; IO \[a\]  
sequenceIO \[\] = do  
        return \[\]  
sequenceIO (x:xs) = do  
        r &lt;- x  
        rs &lt;- (sequenceIO xs)  
        return (r:rs)  
  
I got most of the way there, but I had the last line as:  
  
return r:rs  
  
I had to look up the answer, and found that of course the parentheses were needed.  
  

> 1.  Implement a function `mapIO :: (a -> IO b) -> [a] -> IO [b]` which given a function of type `a -> IO b` and a list of type `[a]`, runs that action on each item in the list, and returns the results.

mapIO :: (a -&gt; IO b) -&gt; \[a\] -&gt; IO \[b\]  
mapIO \_ \[\] = return \[\]  
mapIO f (x:xs) = do  
        v &lt;- f x  
        vs &lt;- (mapIO f xs)  
        return (v:vs)  
  

> This exercise was inspired from a blog post by osfameron. No peeking!

  

</p>

