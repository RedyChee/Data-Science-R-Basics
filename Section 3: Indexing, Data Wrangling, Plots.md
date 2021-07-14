# 3.1 Indexing
- use logicals to index vectors

## defining murder rate as before
` murder_rate <- murders$total / murders$population * 100000 `

## creating a logical vector that specifies if the murder rate in that state is less than or equal to 0.71
` index <- murder_rate <= 0.71 `

## determining which states have murder rates less than or equal to 0.71
` murders$state[index] `

## calculating how many states have a murder rate less than or equal to 0.71
` sum(index) `
- returns the number of entries that are true

## creating the two logical vectors representing our conditions
```
west <- murders$region == "West"
safe <- murder_rate <= 1
```

## defining an index and identifying states with both conditions true
```
index <- safe & west
murders$state[index]
```

| Logical Operators        | Description        | 
|:-------------:|:-------------:|
| < | less than |
| <= | less than or equal to |
| > | greater than |
| >= | greater than or equal to |
| == | exactly equal to |
| != | not equal to |
| ! | NOT |
| | | OR |
| & | AND |

## function which()
- gives the entries of a logical vector that are true
```
x <- c(FALSE, TRUE, FALSE, TRUE, TRUE, FALSE)
which(x)   # returns indices that are TRUE

index <- which(murders$state == "Massachusetts")
index
murder_rate[index]
```

## function match()
- looks for entries in a vector and returns the index needed to access them
```
index <- match(c("New York", "Florida", "Texas"), murders$state)
index
murders$state[index]
murder_rate[index]
```

## function %in%
- want to know whether or not each element of a first vector is in a second vector
```
x <- c("a", "b", "c", "d", "e")
y <- c("a", "d", "f")
y %in% x
[1] TRUE, TRUE, FALSE

# to see if Boston, Dakota, and Washington are states
c("Boston", "Dakota", "Washington") %in% murders$state
```







