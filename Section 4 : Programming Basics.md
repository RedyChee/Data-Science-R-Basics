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






# 4.4 For Loops










