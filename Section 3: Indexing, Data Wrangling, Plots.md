# 3.1 Indexing
- use logicals to index vectors

## defining murder rate as before
` murder_rate <- murders$total / murders$population * 100000 `

## creating a logical vector that specifies if the murder rate in that state is less than or equal to 0.71
` index <- murder_rate <= 0.71 `

## determining which states have murder rates less than or equal to 0.71
` murders$state[inde x] `

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

# 3.2 Basic Data Wrangling

## installing and loading the dplyr package
```
install.packages("dplyr")
library(dplyr)
```

## adding a new column, or changing an existing one
```
library(dslabs)
data("murders")
murders <- mutate(murders, rate = total / population * 100000)
```

## subsetting with filter
` filter(murders, rate <= 0.71) `

## selecting columns with select
` new_table <- select(murders, state, region, rate) `

## using the pipe
- sending the results of one function to another function
- select() and filter() no longer has data frame as first argument 
` murders %>% select(state, region, rate) %>% filter(rate <= 0.71) `

# creating a data frame with stringAsFactors = FALSE
- data.frame() turned characters into factors by default. 
- As of R 4.0, it is no longer necessary to include the stringsAsFactors argument, because R no longer turns characters into factors by default.
```
grades <- data.frame(names = c("John", "Juan", "Jean", "Yao"), 
                     exam_1 = c(95, 80, 90, 85), 
                     exam_2 = c(90, 85, 85, 90),
                     stringsAsFactors = FALSE)
```

## remove rows
` no_florida <- filter(murders, state != "Florida") `

## calculate number of rows
```
# Create a new data frame called murders_nw with only the states from the northeast and the west

murders_nw <- filter(murders, region %in% c("Northeast", "West"))
nrow(murders_nw)
```

# 3.3 Bsaic Plots













