# Section 1: R Basics, Functions, and Data Types

# 1.1 Motivation and Geting Started

## To install a single package
` install.packages("dslabs") `

## To install two packages at the same time (character vector)
` install.packages(c("tidyverse", "dslabs")） `

## To see the list of all installed packages
` installed.packages() `

## Toading the dslabs package into the R session
` library(dslabs) `

## To import dataset into script
```
data("dataset_name")
data(dataset_name)
```

## Save a script: 
- Ctrl+S

## Run an entire script:  
- Ctrl+Shift+Enter, or click "Source" on the editor pane

## Run a single line of script: 
- Ctrl+Enter while the cursor is pointing to that line, or select the chunk and click "run"

## Open a new script: 
- Ctrl+Shift+N 

# 1.2 R Basics

## Assigning values to variables
```
a <- 1
b <- 1
c <- -1
```

## Ways to see value stored in variable
- type variable name
- ` print(variable_name) `

## Solving the quadratic equation
```
(-b + sqrt(b^2 - 4*a*c))/(2*a)
(-b - sqrt(b^2 - 4*a*c))/(2*a)
```
## Object
- stored in named containers, like variables, functions, etc

## Show names of objects saved in workspace 
` ls() `

## Parentheses () to evaluate a function
- If we type a function without parenthesis => the code for the function
- Most functions require an argument

## Access help files
` help(function_name) `
` ?function_name `
` args() `
- help file shows argument the function is expecting (some optional)
- default value is assigned with equal sign, and is assumend to be in order

## Comment
` # `
- to make code more readable

# 1.3 Data Types
## To determine type of object
` class(murders) `

## Finding out more about the structure of the object
` str(murders) `

## Showing the first 6 lines of the dataset
` head(murders) `

## Data frames
- rows => observations
- columns => variables

## To access data from columns of data frame
- accessor
` murders$population`

## Displaying the variable names in the murders dataset
` names(murders) `

## Vectors
- object consisting of several entries
- numeric, charater or logical
- use quotes "" to distinguish between variable names & character strings

## Determining how many entries are in a vector
```
pop <- murders$population
length(pop)
```

## Vectors can be of class numeric and character
```
class(pop)
class(murders$state)
```

## Logical vectors are either TRUE or FALSE
```
z < -3 == 2
z
class(z)
```

## Factors
- store categorical data
- more memory efficient than storing characters
- another type of class
`class(murders$region)`

## Obtaining the levels of a factor
`levels(murders$region)`

## Generate the first five integers 
- 3rd argument of seq() is increment (default = 1)
` seq(1,5) ` or ` 1:5 `
` seq(1,100,2) `

## Length of sequence
```
x <- 1:5
length(x)
```

## Length.out
- generate sequence that are increasing by the same amount but are of the prespecified length
` x <- seq(0, 100, length.out = 5) ` produces 0,25,50,75,100
` class(x) ` produces numeric
` a <- seq(1,10) `
` class(a) ` produces integer

## Integer
- occupy less space in computer memory
- add L after a whole number
` 3L `

## Other methods to access variables in data frame
- use square bracker [] or [[]]
	1.` murders["population"] ` 
	- returns a subset of original data frame 
	- object of class `data.frame`
	2.` murders[["population"]] `
	- access column

## Concatenate
`c()`
- connects all of the strings within it into a single vector, which we can assign to `x`
` x <- c("a", "a", "b", "b", "b", "c") `

## Table 
` table(x) `
- takes a vector as input and returns the frequency of each unique element in the vector.
` table(murders$region) `


