Applied Data Science
========================================================
author: Statistical Programming with R
date: 18.03.2019
autosize: false
width: 1920
height: 1080
font-family: 'Rockwell'
css: mySlideTemplate.css


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 50px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 25px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="320">
</div>
</footer>

R Syntax
========================================================
* Lightweight, script-oriented syntax
* No line ends (e.g., “;” in JAVA)
* Common mathematical operators are used:
* Whitespace typically without meaning
* Round brackets: Function arguments, e.g., `mean(x)`
* Square brackets: Array locations, e.g., `playerList[1]`
* Curly brackets: Code blocks (e.g., around loops or logical structures)
* Values are assigned using `<-` or `=`
* Comments initalized by `#`

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>





Package Management
========================================================
* Packages are collections of R functions, data, and compiled code
* Numerous packages are available for download and installation
* Installing and loading is done via the GUI or the console (script)
* Example for installing and loading the `tidyverse` package
    * With root privileges
        * `install.packages(“tidyverse")`
        * `library(tidyverse)`
    * Without root privileges
        * `install.packages("tidyverse", lib="/data/Rpackages/")`
        * `library(tidyverse, lib.loc="/data/Rpackages/")`
        
<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


R Objects and Data Types
========================================================
* Everything in R is an object
* No strict but dynamic typing
* Basic data types available in R:
    * Numeric: decimal numbers `2.3`
    * Integer: integer numbers `2`
    * Logical: true / false values `TRUE`
    * Character: single or multiple characters `"TWO"`
    * (Ordered) Factor: discrete values from a pre-defined scale `"good", "medium", "bad"`

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Vectors
========================================================
* A vector is a sequence of data elements of the same basic type
    * Members of a vector are called components
    * Vectors are initialized using the `c()` command
    

```r
numericVector <- c(1.2, 1.3, 1.4)
```

* The number of members in a vector is given by the length function:

```r
length(numericVector)
```

```
[1] 3
```

Some vector creation helpers: Sequences
========================================================
The `seq` function has three arguments:
* `from`: starting point
* `to`: end point
* `by`: increment

```r
seq(10, 100, by=10)
```

```
 [1]  10  20  30  40  50  60  70  80  90 100
```
The colon operator `1:10` is a shorthand for `by=1`



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Some vector creation helpers: Repetitions / Replications
========================================================
The `rep` function has two arguments:
* `x`: object to be replicated
* `times`: how often


```r
rep(10, 10) 
```

```
 [1] 10 10 10 10 10 10 10 10 10 10
```
Note: The first argument can be again a vector (e.g., sequences)



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Vector Recycling
========================================================
* If a vector is of insufficient length for an operation, R will recycle previous values
* If longer length is not a mutltiple it will raise a warning



```r
x = c(10,11,12,13)
x + c(0,1)
```

```
[1] 10 12 12 14
```

```r
x + c(0,1,2)
```

```
Warning in x + c(0, 1, 2): Länge des längeren Objektes
 	 ist kein Vielfaches der Länge des kürzeren Objektes
```

```
[1] 10 12 14 13
```




<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Subsetting Vectors
========================================================
* Vector subsetting is done via the `[]` operator
* Positive integers return elements at the specified positions (whitelisting), identical indexes will yield duplicates

```r
x=LETTERS
x[1:3]
```

```
[1] "A" "B" "C"
```

```r
x[c(1,1)]
```

```
[1] "A" "A"
```




<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Subsetting Vectors (2)
========================================================
* Negative integers suppress elements at the specified positions (blacklisting)
You cannot mix positive and negative integers in subsetting!


```r
x[-seq(1,26,2)]
```

```
 [1] "B" "D" "F" "H" "J" "L" "N" "P" "R" "T" "V" "X" "Z"
```

* Logical vectors will return all positions where the vector is TRUE, This is clearly the most useful approach if we master logical expressions

```r
x[x<"D"]
```

```
[1] "A" "B" "C"
```




<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Sorting Vectors
========================================================

```r
x = c(4, 3, 6, 2, 1, 10, 5, 8, 9, 7)
sort(x)
```

```
 [1]  1  2  3  4  5  6  7  8  9 10
```

```r
sort(x, decreasing = T)
```

```
 [1] 10  9  8  7  6  5  4  3  2  1
```

```r
order(x)
```

```
 [1]  5  4  2  1  7  3 10  8  9  6
```




<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Sampling from Vectors
========================================================

```r
sample(1:6, 5) #sample from a vector (no replacement)
```

```
[1] 4 2 1 6 5
```

```r
sample(1:6, 5, replace = T) #sample from a vector (replacement)
```

```
[1] 5 3 2 4 1
```



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>





NA Values
========================================================
* Oftentimes we will have missing or corrupt data
* These will often pop up as NA entries
* Running analyses on these values can cause problems

```r
set.seed(1)
v = sample(c(NA,1,2,3),8,replace = T)
mean(v)
```

```
[1] NA
```
<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

NA Handling
========================================================
* Identify and remove NA values

```r
is.na(v)
```

```
[1] FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE
```

```r
mean(v[!is.na(v)])
```

```
[1] 2.142857
```


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


***

* Replace NA values

```r
v.na.replaced <- v
v.na.replaced[is.na(v)] <- 0
mean(v.na.replaced)
```

```
[1] 1.875
```



Logical Expressions
========================================================
* A AND B: `A & B`
* A OR B: `A | B`
* IF-THEN-ELSE: `ifelse(v>=0, "+", "-")`


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


***

* Conditions may include the following:
    * `==` equal
    * `!=` not equal to
    * `> (>=)` greater (or equal) than
    * `< (<=)` less (or equal) than
    * `%in%` left element in vector on right



Standard statistical expressions
========================================================

```r
v = sample(1:6, 5, T)
mean(v)
```

```
[1] 2.8
```

```r
max(v)
```

```
[1] 5
```

```r
min(v)
```

```
[1] 1
```

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


***

```r
length(v)
```

```
[1] 5
```

```r
length(v[v>3])
```

```
[1] 2
```

```r
quantile(v)
```

```
  0%  25%  50%  75% 100% 
   1    2    2    4    5 
```



Extracting Information from Objects
========================================================

```r
str(v) #structure
```

```
 int [1:5] 4 1 2 2 5
```

```r
summary(v) #summary
```

```
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    1.0     2.0     2.0     2.8     4.0     5.0 
```

```r
class(v) #class
```

```
[1] "integer"
```

```r
head(v, 5) #first 5 elements
```

```
[1] 4 1 2 2 5
```


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


***


```r
length(v) #number of elements
```

```
[1] 5
```

```r
dim(v) #dimensionality
```

```
NULL
```

```r
unique(v) #unique value
```

```
[1] 4 1 2 5
```



Character vector manipulation
========================================================
* The command `paste` creates a single string from the argument vectors’ character representations, sep specifies the separator

```r
paste(LETTERS[1:8], 1:4, sep="!") 
```

```
[1] "A!1" "B!2" "C!3" "D!4" "E!1" "F!2" "G!3" "H!4"
```


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


***
* `paste0` offers a shortcut

```r
paste(rep("A", 5), 1:4, sep="")
```

```
[1] "A1" "A2" "A3" "A4" "A1"
```

```r
paste0(rep("A", 5), 1:4)
```

```
[1] "A1" "A2" "A3" "A4" "A1"
```






String operations (1)
========================================================

* Extracting substrings

```r
substr("ABCDEFG",
       start=2, stop=3)
```

```
[1] "BC"
```

* Constructing compound strings with `sprintf()`

```r
sprintf("%s is %f feet tall", "Sven", 7.1)
```

```
[1] "Sven is 7.100000 feet tall"
```


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


***

* Splitting string on characters

```r
x <- "Split words."
strsplit(x, " ") # Result is a list – use unlist as needed
```

```
[[1]]
[1] "Split"  "words."
```

* String length

```r
nchar("ABC")
```

```
[1] 3
```



String operations (2)
========================================================

* Check if string `x` contains expression `pattern`

```r
grepl(pattern = "aus",
      x = "Nikolaus")
```

```
[1] TRUE
```

```r
grepl(pattern = "haus",
      x = "Nikolaus")
```

```
[1] FALSE
```

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

***

* Replacement

```r
gsub(pattern = "aus",
     replacement = "aushaus",
     x = "Nikolaus")
```

```
[1] "Nikolaushaus"
```



lubridate – temporal data made easy
========================================================


* Parsing time strings

```r
a = ymd("20110720")
c = dmy("31/08/2011")
arrive <- ymd_hms("2011-06-04 12:00:00")
leave <- ymd_hms("2011-08-10 14:00:00")
```

* Extracting time details

```r
wday(arrive) #also second / hour ...
```

```
[1] 7
```

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

***

```r
wday(arrive, label = TRUE)
```

```
[1] Sa
Levels: So < Mo < Di < Mi < Do < Fr < Sa
```

* Time intervals

```r
A <- interval(arrive, leave)
B <- interval(a, c)
int_overlaps(A,B)
```

```
[1] TRUE
```




Programming task 1 (Dices.R)
========================================================
* Create two vectors which reflecting 100 throws of two standard dices by sampling from 1:6.
    * How often did dice 1 show the higher number?
    * How often did dice 1 show a number which was at least 3 larger than dice 2?
    * Compare the ten highest throws of the two dices

* Create a third vector reflecting the sum of the two other throws
    * Determine the five highest and the five lowest combined scores



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Matrices
========================================================
* A matrix is a collection of data elements arranged in a two-dimensional rectangular layout
* Matrices are created in R with the matrix function


```r
A = matrix(c(2,4,3,1,5,7), nrow=2, ncol=3, byrow = TRUE)
A
```

```
     [,1] [,2] [,3]
[1,]    2    4    3
[2,]    1    5    7
```




<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


Data frames
========================================================
* A data frame is used for storing data tables
* It is a collection of vectors of equal length
* For example, here is a built-in data frame in R, called `mtcars`.

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
```

* The top line of the table, called the header, contains the column names
* Each horizontal line afterward denotes a data row, which begins with the name of the row, and then followed by the actual data Each data member of a row is called a cell

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Adressing Data frames
========================================================
* To retrieve data in a cell, we would enter its row and column coordinates in the single square bracket `[]` operator

```r
mtcars[1, 2]
```

```
[1] 6
```

```r
mtcars["Mazda RX4", "cyl"]
```

```
[1] 6
```
* Subsetting of data frames in base R relies on addressing using vectors instead of single values

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

***
* Individual columns are accessed and created using the $ operator

```r
head(mtcars$mpg, 5)
```

```
[1] 21.0 21.0 22.8 21.4 18.7
```

```r
mtcars$l100km = 282.48 / mtcars$mpg
head(mtcars$l100km, 5)
```

```
[1] 13.45143 13.45143 12.38947 13.20000 15.10588
```

* Going forward, data frames will be our most important object
* Base R is fairly clunky in operating on data frames. Soon we will explore the `tidyverse` which features very elegant and efficient ways for data frame manipulation


Programming task 2 (Cars.R)
========================================================
* What is the mean / max / min mpg of the cars?

* Create a new column which states the ratio of power vs. weight
    * Which is the best car according to this dimension?





<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>


Creating Data Frames
========================================================

* Manual specification of data frame df

```r
n = c(2, 3, 5)
s = c("aa", "bb", "cc")
b = c(TRUE, FALSE, TRUE)
df = data.frame(n, s, b)
df
```

```
  n  s     b
1 2 aa  TRUE
2 3 bb FALSE
3 5 cc  TRUE
```

* Reading external data from text files `df = read.csv2("pathToData", header=TRUE, sep =";")`
* `read.csv2` will also work on URL to remote files, e.g.,

```r
hsb2 <- read.csv2('https://raw.githubusercontent.com/rpruim/OpenIntro/master/data/hsb2.csv', header=T, sep=",")
head(hsb2,2)
```

```
   id gender  race    ses schtyp       prog read write math science socst
1  70   male white    low public    general   57    52   41      47    57
2 121 female white middle public vocational   68    59   53      63    61
```

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Extending Data Frames
========================================================

* Extra rows: `rbind`

```r
df1 = data.frame(numbers=c(1, 2, 3), letters=c("a", "b", "c"))
df2 = data.frame(numbers=c(4), letters=c("d"))
rbind(df1, df2)
```

```
  numbers letters
1       1       a
2       2       b
3       3       c
4       4       d
```


* Extra columns: `cbind`

```r
df1 = data.frame(numbers=c(1, 2, 3, 4))
df2 = data.frame(letters=c("a", "b", "c", "d"))
cbind(df1, df2)
```

```
  numbers letters
1       1       a
2       2       b
3       3       c
4       4       d
```


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Extending Data Frames
========================================================

* A list is a generic vector containing different objects.
* We will typically avoid using this unstructured format but may often face it when obtaining data through web services


```r
n = c(2, 3, 5)
s = c("aa", "bb", "cc", "dd", "ee")
b = c(TRUE, FALSE, TRUE, FALSE, FALSE)
x = list(n, s, b, 3)   # x contains copies of n, s, b
x
```

```
[[1]]
[1] 2 3 5

[[2]]
[1] "aa" "bb" "cc" "dd" "ee"

[[3]]
[1]  TRUE FALSE  TRUE FALSE FALSE

[[4]]
[1] 3
```



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>
*** 
* Sublists: We retrieve a sublist (or slice) with the single square bracket `[]` operator – result is still a list

```r
typeof(x[1])
```

```
[1] "list"
```

* List elements: We retrieve list elements with the double square bracket `[[]]` operator – result is the original type

```r
typeof(x[[1]])
```

```
[1] "double"
```

* Named elements: Similar to data frame columns the list elements can be named and referenced using these names
* `unlist(x)` converts (flattens) a list of vectors into a single vector

Webservice example
========================================================
* JSON call from google API - Retrieve bars within 500 meters of Sanderring 2


```r
URL <- "https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=49.7881799,9.93524&radius=500&types=bar&key=AIzaSyA-ffYLtUhHqRdmKfCDVZQt4mxokjS6h80"
library(RCurl)
library(RJSONIO)
response_parsed <- fromJSON(getURL(URL,ssl.verifyhost = 0L, ssl.verifypeer = 0L))
```

* The google webservice returns an XML file which is parsed by R into a list
* Parsed response is a list of three lists – results are stored in the list results


```r
names(response_parsed)
```

```
[1] "html_attributions" "results"           "status"           
```


<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Webservice example (2)
========================================================


```r
names(response_parsed$results[[1]])
```

```
 [1] "geometry"           "icon"               "id"                
 [4] "name"               "opening_hours"      "photos"            
 [7] "place_id"           "plus_code"          "price_level"       
[10] "rating"             "reference"          "scope"             
[13] "types"              "user_ratings_total" "vicinity"          
```

```r
response_parsed$results[[1]]$name
```

```
[1] "Nachtwächter"
```

```r
response_parsed$results[[1]]$geometry$location
```

```
      lat       lng 
49.788248  9.929879 
```

```r
response_parsed$results[[1]]$rating
```

```
[1] 4.4
```



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Another API
========================================================


```r
URL = "https://www.anapioficeandfire.com/api/characters?page=1&pageSize=200"
response_parsed_got <- fromJSON(getURL(URL,ssl.verifyhost = 0L, ssl.verifypeer = 0L))
names(response_parsed_got[[27]])
```

```
 [1] "url"         "name"        "gender"      "culture"     "born"       
 [6] "died"        "titles"      "aliases"     "father"      "mother"     
[11] "spouse"      "allegiances" "books"       "povBooks"    "tvSeries"   
[16] "playedBy"   
```

```r
response_parsed_got[[27]]$name
```

```
[1] "Tywin Lannister"
```

```r
response_parsed_got[[27]]$title
```

```
[1] "Lord of Casterly Rock"                 
[2] "Shield of Lannisport"                  
[3] "Warden of the West"                    
[4] "Hand of the King"                      
[5] "Savior of the City (of King's Landing)"
```

```r
response_parsed_got[[27]]$died
```

```
[1] "In 300 AC, at King's Landing"
```


R Functions
========================================================
* R allows us to easily and elegantly write virtually any function that we want to implement
* Basic setup for functions:
`fun <- function(arguments) {code}`
* Multiple calculation steps are separated by line breaks
* Without return statement the last evaluation result is returned, if multiple calculations should be returned use `return()`
* For multiple return values use vector or list

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

***

```r
fun <- function(x, y) {x+y}
fun(1,5)
```

```
[1] 6
```

```r
fun2 <- function(x, y) {
  z1 <- 2*x + y
  z2 <- x + 2*y
  return(c(z1, z2))}
fun2(1,5)
```

```
[1]  7 11
```

Programming task 3 (Ratings.R)
========================================================
* Create a function getNameAndRating(listing) that returns name and rating for a Google Places Listing (from our earlier API call) as a data frame

* NB: If there is no rating available return -1 using ifelse



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Applying functions to vectors / data frames / lists
========================================================

* Very often we may be interested in performing the same operation on multiple entries
* While looping is possible in R it should typically avoided
* In base R the `apply` scheme covers this approach, in this course we use the more versatile and performant map function from the `purrr` package

`library(purrr)`

`map(.x, .f) for every element of .x apply .f`

* The base map function returns a list, there are special versions returning typed vectors or data frames: e.g., `map_chr`, `map_dbl`, `map_df`, ...
* For functions with two arguments use `map2(.x, .y, .f)`



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

@JennyBryan Lego illustrations
========================================================
![optional caption text](figures/minis1.png)

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

@JennyBryan Lego illustrations - map
========================================================
![optional caption text](figures/minis2.png)

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

@JennyBryan Lego illustrations - map2
========================================================
![optional caption text](figures/minis3.png)

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

@JennyBryan Lego illustrations - map2
========================================================
![optional caption text](figures/minis4.png)

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

@JennyBryan Lego illustrations
========================================================
![](figures/minis5.png)

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

@JennyBryan Lego illustrations - map2
========================================================
![](figures/minis6.png)

<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>

Programming task 4 (Ratings.R)
========================================================
* Leveraging our function, get names and ratings of all bars from our API call in a nice data frame



<footer class = 'footnote'>
<div style="position: absolute; left: 0px; bottom: 0px; z-index:100; background-color:white">
Prof. Dr. Christoph Flath | ADS 2019</div>
</footer>
<footer class = 'logo'>
<div style="position: absolute; left: 1100px; bottom: 0px; z-index:100; background-color:white">
<img src = "uni-wuerzburg-logo.svg" width="160">
</div>
</footer>