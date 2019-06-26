Title: Haskell Wikibook: Type declarations
Date: 2016-04-24 07:29
Author: Tony
Slug: haskell-wikibook-type-declarations
Status: published

Here are my answers to the [Haskell Wikibook: Type declarations](https://en.wikibooks.org/wiki/Haskell/Type_declarations) chapter questions:  

> Reread the function definitions above. Then look closer at the `showDate` helper function. We said it was provided "for the sake of code clarity", but there is a certain clumsiness in the way it is used. You have to pass three separate Int arguments to it, but these arguments are always linked to each other as part of a single date. It would make no sense to do things like passing the year, month and day values of the Anniversary in a different order, or to pass the month value twice and omit the day.  
>
> -   Could we use what we've seen in this chapter so far to reduce this clumsiness?  
>       
>     Yes, we can create a Date type.
> -   Declare a `Date` type which is composed of three Int, corresponding to year, month and day. Then, rewrite `showDate` so that it uses the new Date data type. What changes will then be needed in `showAnniversary` and the `Anniversary` for them to make use of Date?.  
>       
>
>         data MyDate = MyDate Int Int Int
>
>         data Anniversary = Birthday String MyDate       -- name, date
>                          | Wedding String String MyDate -- spouse name 1,
>                                                         -- spouse name 2, date
>
>         showDate :: MyDate -> String
>         showDate (MyDate y m d) = show y ++ "-" ++ show m ++ "-" ++ show d
>
>         showAnniversary :: Anniversary -> String
>         showAnniversary (Birthday name date) = name ++ " born " ++ showDate date
>         showAnniversary (Wedding name1 name2 date) = name1 ++ " married " ++ name2 ++ " on " ++ showDate date
>
 

</p>

