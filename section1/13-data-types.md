# 1.3 Data Types

## 相關操作

* Class

```
> a <- 2
> class(a)
[1] "numeric"
> class(ls)
[1] "function"
```

* Data Frame

```
> library(dslabs)
> data("murders")
> class(murders)
[1] "data.frame"
```

* str \(structure of an object\)

```
> str(murders)
'data.frame':    51 obs. of  5 variables:
 $ state     : chr  "Alabama" "Alaska" "Arizona" "Arkansas" ...
 $ abb       : chr  "AL" "AK" "AZ" "AR" ...
 $ region    : Factor w/ 4 levels "Northeast","South",..: 2 4 4 2 4 4 1 2 2 2 ...
 $ population: num  4779736 710231 6392017 2915918 37253956 ...
 $ total     : num  135 19 232 93 1257 ...
```

* head

```
> head(murders)
       state abb region population total
1    Alabama  AL  South    4779736   135
2     Alaska  AK   West     710231    19
3    Arizona  AZ   West    6392017   232
4   Arkansas  AR  South    2915918    93
5 California  CA   West   37253956  1257
6   Colorado  CO   West    5029196    65
```

* $ \(The Accessor\)

```
> murders$population
 [1]  4779736   710231  6392017  2915918 37253956  5029196
 [7]  3574097   897934   601723 19687653  9920000  1360301
[13]  1567582 12830632  6483802  3046355  2853118  4339367
[19]  4533372  1328361  5773552  6547629  9883640  5303925
[25]  2967297  5988927   989415  1826341  2700551  1316470
[31]  8791894  2059179 19378102  9535483   672591 11536504
[37]  3751351  3831074 12702379  1052567  4625364   814180
[43]  6346105 25145561  2763885   625741  8001024  6724540
[49]  1852994  5686986   563626
```

* names

```
> names(murders)
[1] "state"      "abb"        "region"     "population"
[5] "total"
```

* length

```
> pop <- murders$population
> length(pop)
[1] 51
> class(pop)
[1] "numeric"
```

* Character Vectors

```
> a <- 1
> a
[1] 1
> "a"
[1] "a"
```

* Logical Vectors

```
> z <- 3 == 2
> z
[1] FALSE
> class(z)
[1] "logical"
```

```
 Note: == is a relational operator , different from =
```

* Factor
  * factors are useful for storing what is called categorical data

```
> class(murders$region)
[1] "factor"
> levels(murders$region)
[1] "Northeast"     "South"         "North Central"
[4] "West"
```

---

# Assessment

## str

We're going to be using the following dataset for this module. Run this code in the console.

```
library(dslabs)
data(murders)
```

Next, use the function`str`to examine the structure of the`murders`object. We can see that this object is a data frame with 51 rows and five columns.

Which of the following best describes the variables represented in this data frame:

##### Possible Answers

* [ ] The 51 states
* [ ] The murder rates for all 50 states and DC
* [x] The state name, the abbreviation of the state name, the state's region, and the state's population and the total number of murders for 2010.
* [ ] `str`shows no relevant information

## Variable names

In the previous question, we saw the different variables that are a part of this dataset from the output of the`str()`function. The function`names()`is specifically designed to extract the column names from a data frame.

```
> # Load package and data
> 
> library(dslabs)
> data(murders)
> 
> # Use the function names to extract the variable names
> names(murders)
[1] "state"      "abb"        "region"     "population" "total"
```

## Examining Variables

In this module we have learned that every variable has a class. For example, the class can be a_character_,_numeric\_or\_logical_. The function`class()`can be used to determine the class of an object.

Here we are going to determine the class of one of the variables in the`murders`data frame. To extract variables from a data frame we use`$`, referred to as the accessor.

In the editor we show an example of how to do this. Let\`s try it out for ourselves.

```R
> # To access the population variable from the murders dataset use this code:
> p <- murders$population
> 
> # To determine the class of object `p` we use this code:
> class(p)
[1] "numeric"
> 
> # Use the accessor to extract state abbreviations and assign it to a
> a <- murders$abb
> # Determine the class of a
> class(a)
[1] "character"
```

# Multiple ways to access variables

An important lesson you should learn early on is that there are multiple ways of doing things in R. For example, to generate the first five integers we note that`1:5`, and`seq(1,5)`return the same result.

There are also other ways to variables from a data frame. For example we can use the square brackets`[[`instead of the accessor`$`. Example code is included in the editor.

Now, if you instead try to access a columns with just one bracket

```
murders["population"]
```

R returns a subset of the original data frame containing just this column. This new object will be of class`data.frame`rather than a vector. To access the column itself you need to use either the`$`accessor or the double square brackets`[[`.

This is an examaple of how R can be a bit idiosyncratic sometimes. It is very common to find it confusing at first.

    # We extract the population like this:
    > p <- murders$population
    > p
     [1]  4779736   710231  6392017  2915918 37253956  5029196  3574097   897934
     [9]   601723 19687653  9920000  1360301  1567582 12830632  6483802  3046355
    [17]  2853118  4339367  4533372  1328361  5773552  6547629  9883640  5303925
    [25]  2967297  5988927   989415  1826341  2700551  1316470  8791894  2059179
    [33] 19378102  9535483   672591 11536504  3751351  3831074 12702379  1052567
    [41]  4625364   814180  6346105 25145561  2763885   625741  8001024  6724540
    [49]  1852994  5686986   563626
    > # This is how we do the same with the square brackets:
    > o <- murders[["population"]]
    > o
     [1]  4779736   710231  6392017  2915918 37253956  5029196  3574097   897934
     [9]   601723 19687653  9920000  1360301  1567582 12830632  6483802  3046355
    [17]  2853118  4339367  4533372  1328361  5773552  6547629  9883640  5303925
    [25]  2967297  5988927   989415  1826341  2700551  1316470  8791894  2059179
    [33] 19378102  9535483   672591 11536504  3751351  3831074 12702379  1052567
    [41]  4625364   814180  6346105 25145561  2763885   625741  8001024  6724540
    [49]  1852994  5686986   563626
    > # We can confirm these two are the same
    > identical(o, p)
    [1] TRUE

    > # Use square brackets to extract `abb` from `murders` and assign it to b
    > b <- murders[["abb"]]
    b
     [1] "AL" "AK" "AZ" "AR" "CA" "CO" "CT" "DE" "DC" "FL" "GA" "HI" "ID" "IL" "IN"
    [16] "IA" "KS" "KY" "LA" "ME" "MD" "MA" "MI" "MN" "MS" "MO" "MT" "NE" "NV" "NH"
    [31] "NJ" "NM" "NY" "NC" "ND" "OH" "OK" "OR" "PA" "RI" "SC" "SD" "TN" "TX" "UT"
    [46] "VT" "VA" "WA" "WV" "WI" "WY"
    > # Check if `a` and `b` are identical
    > identical(a, b)
    [1] TRUE

# Factors

Using the`str()`command, we saw that the\_region\_column stores a factor. You can corroborate this by using the`class`command on the\_region\_column.

The function`levels`shows us the categories for the factor.

```
> # We can see the class of the region variable using class
> class(murders$region)
[1] "factor"
> murders$region
 [1] South         West          West          South         West         
 [6] West          Northeast     South         South         South        
[11] South         West          West          North Central North Central
[16] North Central North Central South         South         Northeast    
[21] South         Northeast     North Central North Central South        
[26] North Central West          North Central West          Northeast    
[31] Northeast     West          Northeast     South         North Central
[36] North Central South         West          Northeast     Northeast    
[41] South         North Central South         South         West         
[46] Northeast     South         West          South         North Central
[51] West         
Levels: Northeast South North Central West
> # Determine the number of regions included in this variable
> levels(murders$region)
[1] "Northeast"     "South"         "North Central" "West"
> length(levels(murders$region))
[1] 4
```

# Tables

The function`table`takes a vector as input and returns the frequency of each unique element in the vector.

```
> # Here is an example of what the table function does
> x <- c("a", "a", "b", "b", "b", "c")
> table(x)
x
a b c 
2 3 1
> 
> # Write one line of code to show the number of states per region
> murders$region
 [1] South         West          West          South         West         
 [6] West          Northeast     South         South         South        
[11] South         West          West          North Central North Central
[16] North Central North Central South         South         Northeast    
[21] South         Northeast     North Central North Central South        
[26] North Central West          North Central West          Northeast    
[31] Northeast     West          Northeast     South         North Central
[36] North Central South         West          Northeast     Northeast    
[41] South         North Central South         South         West         
[46] Northeast     South         West          South         North Central
[51] West         
Levels: Northeast South North Central West
> table(murders$region)

    Northeast         South North Central          West 
            9            17            12            13
```



