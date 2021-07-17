# 4.1 Introduction to Programming in R

# 4.2 Conditionals

## if-else 
```
if (condition){
	expression
} else{
	alternative expression
}

# Example

library(dslabs)
data(murders)
murder_rate <- murders$total / murders$population*100000
ind <- which.min(murder_rate)
if(murder_rate[ind] < 0.5){
  print(murders$state[ind]) 
} else{
  print("No state has murder rate that low")
}
```

## ifelse()
- works on vectors by examining each element of the vector and returning a corresponding answer accordingly
```
a <- c(0,1,2,-4,5)
result <- ifelse(a > 0, 1/a, NA)


data(na_example)
no_nas <- ifelse(is.na(na_example), 0, na_example) 
sum(is.na(no_nas))

# Assign the state abbreviation when the state name is longer than 8 characters 
new_names <- ifelse(nchar(murders$state) > 8, murders$abb, murders$state)
```

## any()
- takes a vector of logicals and returns true if any of the entries are true
```
z <- c(TRUE, TRUE, FALSE)
any(z)
```

## all()
- takes a vector of logicals and returns true if all of the entries are true
` all(z) `

# 4.3 Functions
- functions are objects
- must be assigned a variable name with arrow operator

## the general form of a function
```
my_function <- function(VARIABLE_NAME){
  perform operations on VARIABLE_NAME and calculate VALUE
  VALUE
}
```

## example of defining a function to compute the average of a vector x
```
avg <- function(x){
  s <- sum(x)
  n <- length(x)
  s/n
}
```

## we see that the above function and the pre-built R mean() function are identical
```
x <- 1:100
identical(mean(x), avg(x))
```

## variables inside a function 
- not defined in the workspace
```
s <- 3
avg(1:10)
s
```

## functions can have multiple arguments as well as default values
```
avg <- function(x, arithmetic = TRUE){
  n <- length(x)
  ifelse(arithmetic, sum(x)/n, prod(x)^(1/n))
}
```

# 4.4 For Loops
- perform the same task over and over while changing the variable
- general form: 
```
for(i in some_range){
	do operations
}"
```
- At the end of the loop, the value of i is the last value of the range

## creating a function that computes the sum of integers 1 through n
```
compute_s_n <- function(n){
  x <- 1:n
  sum(x)
}
```

## a very simple for-loop
```
for(i in 1:5){
  print(i)
}
```

## a for-loop for our summation
```
m <- 25
s_n <- vector(length = m) # create an empty vector
for(n in 1:m){
  s_n[n] <- compute_s_n(n)
}
```

## creating a plot for our summation function
```
n <- 1:m
plot(n, s_n)
```

## a table of values comparing our function to the summation formula
` head(data.frame(s_n = s_n, formula = n*(n+1)/2)) `

## overlaying our function with the summation formula
```
plot(n, s_n)
lines(n, n*(n+1)/2)
```

# 4.5 Other Functions
- apply
- sapply
- tapply
- mapply
- split
- cut
- quantile 
- reduce
- identical
- unique











