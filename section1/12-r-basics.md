# 1.2 R Basics

基本操作:

```R
> a <- 1
> b <- 1
> c <- 1
> a
[1] 1
> print(a)
[1] 1
```

## 常用操作與函式:

* ls\(\) : 顯示所有你儲存的物件 \(see object in the workspace\)

```
 [1] "a"              "b"              "beta1"          "c"              "father.son"    
 [6] "galton"         "galton_heights" "GaltonFamilies" "res"            "results"       
[11] "rss"
```

如果想了解ls的原始碼，可以透過ls來呼叫它的code

```
> ls
function (name, pos = -1L, envir = as.environment(pos), all.names = FALSE, 
    pattern, sorted = TRUE) 
{
    if (!missing(name)) {
        pos <- tryCatch(name, error = function(e) e)
        if (inherits(pos, "error")) {
            name <- substitute(name)
            if (!is.character(name)) 
                name <- deparse(name)
            warning(gettextf("%s converted to character string", 
                sQuote(name)), domain = NA)
            pos <- name
        }
    }
    all.names <- .Internal(ls(envir, all.names, sorted))
    if (!missing(pattern)) {
        if ((ll <- length(grep("[", pattern, fixed = TRUE))) && 
            ll != length(grep("]", pattern, fixed = TRUE))) {
            if (pattern == "[") {
                pattern <- "\\["
                warning("replaced regular expression pattern '[' by  '\\\\['")
            }
            else if (length(grep("[^\\\\]\\[<-", pattern))) {
                pattern <- sub("\\[<-", "\\\\\\[<-", pattern)
                warning("replaced '[<-' by '\\\\[<-' in regular expression pattern")
            }
        }
        grep(pattern, all.names, value = TRUE)
    }
    else all.names
}
<bytecode: 0x000000000dc85d18>
<environment: namespace:base>
```

* log\(\)

```
> log(8)
[1] 2.079442
```

* Nested Functions

```
> exp(1)
[1] 2.718282
> log(2.718)
[1] 0.9998963
> log(exp(1))
[1] 1
```

* Help

```
> help("log")
```

![](/assets/RhelpCom.png)

* Arguments

```
> args(log)
function (x, base = exp(1)) 
NULL
> log(8,base=2)
[1] 3
> log(8,2)
[1] 3
```

* DataSet

```
> data()
```

![](/assets/RDataSet.png)

* Comments

註解 : \#\#

```
## Testing!!!
```

---

# Assessment

## Using variables 1

What is the sum of the firstnnpositive integers?

We can use the formulan$$n(n+1)/2 $$to quickly compute this quantity.

```R
> # Here is how you compute the sum for the first 20 integers
> 20*(20+1)/2
[1] 210
> 
> # However, we can define a variable to use the formula for other values of n
> n <- 20
> n*(n+1)/2
[1] 210
> 
> n <- 25
> n*(n+1)/2
[1] 325
> 
> # Below, write code to calculate the sum of the first 100 integers
> n <- 100
> n*(n+1)/2
[1] 5050
```

## Using variables 2

What is the sum of the first 1000 positive integers?

We can use the formula$$n(n+1)/2 $$to quickly compute this quantity.

```
# Below, write code to calculate the sum of the first 1000 integers 
n <- 1000
n*(n+1)/2
```

## Functions

Run the following code in the R console:

```R
n <- 1000
x <- seq(1,n)
sum(x)
```

Based on the result, what do you think the functions`seq`and`sum`do? You can use the help system.

##### Possible Answers

* [ ] sum creates a list of numbers and seq adds them up.
* [x] seq creates a list of numbers and sum adds them up.
* [ ] seq computes the difference between two arguments and sum computes the sum of 1 through 1000.
* [ ] sum always returns the same number

## Nested function calls 1

In math and programming we say we evaluate a function when we replace arguments with specific values. So if we type`log2(16)`we evaluate the`log2`function to get the log to the base 2 of`16`which is`4`.

In R it is often useful to evaluate a function inside another function. For example,`sqrt(log2(16))`will calculate the log to the base 2 of 16 and then compute the square root of that value. So the first evaluation gives a 4 and this gets evaluated by`sqrt`to give the final answer of 2.

```R
> # log to the base 2
> log2(16)
[1] 4
> 
> # sqrt of the log to the base 2 of 16:
> sqrt(log2(16))
[1] 2
> 
> # Compute log to the base 10 (log10) of the sqrt of 100. Do not use variables.
> log10(sqrt(100))
[1] 1
```

# Nested functions call 2

Which of the following will always return the numeric value stored in`x`? You can try out examples and use the help system in the R console.

##### Possible Answers

* [ ] `log(10^x)`
* [ ] `log10(x^10)`
* [x] `log(exp(x))`
* [ ] `exp(log(x, base = 2))`



