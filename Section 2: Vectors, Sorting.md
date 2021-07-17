# 2.1 Vectors

## Create vectors of class numeric or character with concatenate function
```
codes <- c(380, 124, 818)
country <- c("italy", "canada", "egypt")
```

## name the elements of a numeric vector
## Note that the two lines of code below have the same result
```
codes <- c(italy = 380, canada = 124, egypt = 818)
codes <- c("italy" = 380, "canada" = 124, "egypt" = 818)
```

## name the elements of a numeric vector using the names() function
```
codes <- c(380, 124, 818)
country <- c("italy","canada","egypt")
names(codes) <- country
```
## Subsetting
## Using square brackets to access specific elements of a vector
` codes[2] `      => 2nd element
` codes[c(1,3)] ` => 1st and 3rd element
` codes[1:2] `    => 1st and 2nd element

## If the entries of a vector are named, they may be accessed by referring to their name
```
codes["canada"]
codes[c("egypt","italy")]
```
## Coercion
- guess what was meant when an entry does not match the expected
` x <- c(1, "canada", 3) `
- R coerced the data into characters

## turn numbers into characters
` as.character() `

## turn characters into numbers
` as.numeric() `

## return length of character vector
` nchar(x) `

## missing data
- missing data is assigned the value NA
```
> x <- c("1", "b", "3")
> as.numeric(x)
[1] 1 NA 3
```

## is.na
- returns a logical vector that tells us which entries are NA
` is.na(na_example) `

## return number of NA
` sum(x) `

## ! operator
- True becomes False and vice versa

-----
# example
## Create the ind vector
library(dslabs)
data(na_example)
ind <- is.na(na_example)

## We saw that this gives an NA
mean(na_example)

## Compute the average, for entries of na_example that are not NA 
mean(na_example[!ind])
-----

# 2.2 Sorting

## sort a vector in increasing order
```
x <- c(31, 4, 15, 92, 65)
x
sort(x)
```

## produces the indices to obtain the sorted vector
```
index <- order(x)
x[index]    # rearranging by this index puts elements in order
order(x)
```

## returns the largest/smallest value
` max(murders$total) ` 
` min(murders$total) ` 

## returns the index of the largest/smallest value
```
i_max <- which.max(murders$total)
i_min <- which.min(murders$total)
murders$state[i_max]    # state name with highest number of total murders
```

## provide the ranks of the items in the original vector.
```
x <- c(31, 4, 15, 92, 65)
x
rank(x)  #lowest to highest
rank(-x) #higest to lowest
```

-----
# example
## Define a variable states to be the state names from the murders data frame
states <- murders$state

## Define a variable ranks to determine the population size ranks 
ranks <- rank(murders$population)

## Define a variable ind to store the indexes needed to order the population values
ind <- order(ranks)

## Create a data frame my_df with the state name and its rank and ordered from least populous to most 
my_df <- data.frame(states = states[ind], ranks = ranks[ind])
my_df
-----

# 2.3 Vector Arithmetics
- In R, arithmetic operations on vectors occur element-wise.
- The name of the state with the maximum population is found by doing the following
` murders$state[which.max(murders$population)] `
- to obtain the murder rate
` murder_rate <- murders$total / murders$population * 100000 `
- ordering the states by murder rate, in decreasing order
` murders$state[order(murder_rate, decreasing=TRUE)] `





