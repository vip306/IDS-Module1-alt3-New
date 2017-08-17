---
title       : 6. Indexing
description : R provides a powerful and convenient way of indexing vectors. We're going to learn some ways of doing that!

--- type:NormalExercise lang:r xp:100 skills:1 key:6bb68b8400
## 1. Logical Vectors

A logical vector contains `TRUE` or `FALSE` values based on a logical criteria you define. 

For example, if `vct = [2,3,4,1,5]` and you want to find which elements of `v` are less than 4, you can create a logical vector with the following command: 
`lvct <- vct < 4`
This would result in the logical vector `lvct = [TRUE TRUE FALSE TRUE FALSE]`. 

You can use any of the logical operators `<`, `>` or `=`. 

For this exercise, a dataset `women` is loaded. Follow the instructions to define and print the logical vector.  

*** =instructions
- In an object `weight_rate`, store `women$weight`/ `women$height` 
- Create a logical vector `low` for the condition `weight_rate < 2`
- Print the logical vector `low` and observe the result


*** =hint


*** =pre_exercise_code
```{r}
library(datasets)
data(women)
```

*** =sample_code
```{r}
# Load the datasets
library(datasets)
data(women)

# Store the weight rate for each tree, in `weight_rate`


# Store the `weight_rate < 2` in `low`


```

*** =solution
```{r}

# Store the weight rate for each tree, in `weight_rate`
weight_rate<-women$weight/women$height

# Store the `weight_rate < 2` in `low`
low <- weight_rate < 2
```

*** =sct
```{r}
test_error()
test_object("weight_rate", undefined_msg = "Define the weight rate first!", incorrect_msg = "Check the formula.")
test_object("low", undefined_msg = "Define low!", incorrect_msg = "It should be weight rates less than 2.")
success_msg("Great job!")

```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:a76be07302
## 2. Indices of a Logical Vector

As you learnt earlier, a logical vector has `TRUE` or `FALSE` elements. 

You can find out the indices of the `TRUE` elements using the `which()` function. 

For `lvct = [TRUE TRUE FALSE TRUE FALSE]`, `which(lvct)` would print `1 2 4` since those elements are `TRUE` and satisfy the logical condition you had defined. 

For this exercise, you will repeat the instructions from the previous exercise, and use the `which()` function to print the indices for the elements that satisfy the condition. 

*** =instructions
- In an object `weight_rate`, store `women$weight`/ `women$height` 
- Create a logical vector `low` for the condition `weight_rate < 2`
- Use `which()` to determine the indices of `weight_rate` associated with values lower than 2

*** =hint


*** =pre_exercise_code
```{r}
library(datasets)
data(women)
```

*** =sample_code
```{r}
# Load the datasets
library(datasets)
data(women)

# Store the weight rate for each tree, in `weight_rate`


# Store the `weight_rate < 2` in `low`


# Use `which(low)`, to get the lowest value


```

*** =solution
```{r}
# Store the weight rate for each tree, in `weight_rate`
weight_rate<-women$weight/women$height

# Store the `weight_rate < 2` in `low`
low <- weight_rate < 2

# Use `which(low)`, to get the lowest value
which(low)
```

*** =sct
```{r}
test_error()
test_object("weight_rate", undefined_msg = "Define the weight rate first!", incorrect_msg = "Check the formula.")
test_object("low", undefined_msg = "Define low!", incorrect_msg = "It should be weight rates less than 2.")
test_function("which", incorrect_msg = "Use the command from the instructions.")
success_msg("Awesome!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:43f34535d7
## 3. Use indexing to access values of a vector


*** =instructions
Use the results from the previous exercise to report the indices of women with weight rate lower than 2, using the square brackets to retrieve the heights of those women from the dataset.

For example: `food$cost[low]`, would give us the cost of food lower than 1.

*** =hint

*** =pre_exercise_code
```{r}
library(datasets)
data(women)
```

*** =sample_code
```{r}
# Load the datasets
library(datasets)
data(women)

# Store the weight rate for each tree, in `weight_rate`


# Store the `weight_rate < 2` in `low`


# Heights of women with weight rates lower than 2


```

*** =solution
```{r}
# Store the weight rate for each tree, in `weight_rate`
weight_rate<-women$weight/women$height

# Store the `weight_rate < 2` in `low`
low <- weight_rate < 2

# Height of women with weight rates lower than 2
women$height[low]
```

*** =sct
```{r}
test_error()
test_object("weight_rate", undefined_msg = "Define the weight rate first!", incorrect_msg = "Check the formula.")
test_object("low", undefined_msg = "Define low!", incorrect_msg = "Same as last question.")
test_output_contains("women$height[low]", incorrect_msg = "Follow code from example given!")
success_msg("Good job!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:a15f758c03
## 4. Combined logical expressions


*** =instructions

Now extend the code from exercise 2 and 3 to report the weight of the women whose height is 60 inches with weight rates lower than 2.
For example: `low & food$courses=="Deserts"`, would give us the deserts from the courses variable in the food dataset.  


*** =hint
Use the previously defined logical vector low and the logical operator &.


*** =pre_exercise_code
```{r}
library(datasets)
data(women)
```

*** =sample_code
```{r}
# Load the datasets
library(datasets)
data(women)

# Store the weight rate for each tree, in `weight_rate`
weight_rate<-women$weight/women$height

# Store the `weight_rate < 2` in `low`
low <- weight_rate < 2

# Store height=60in, with weight rates lower than 2 in `ind`


# Get weight of that entry


```

*** =solution
```{r}
# Store the weight rate for each tree, in `weight_rate`
weight_rate<-women$weight/women$height

# Store the `weight_rate < 2` in `low`
low <- weight_rate < 2

# Store height=60in, with weight rates lower than 2 in `ind`
ind <- low & women$height== "60"

# Get weight of that entry
women$weight[ind]
```

*** =sct
```{r}
test_error()
test_object("ind", undefined_msg = "Make sure to define ind first!", incorrect_msg = "Check code.")
test_output_contains("women$weight[ind]", incorrect_msg = "Use [] to retrieve names.")
success_msg("Wasn`t that good! Let`s move to the next one.")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:f2004ac34f
## 5. Average and below average

*** =instructions
In a previous exercise we computed the weight rate for each tree. We know the mean for the weight rate to be 2. How many women have a weight rate above the average?

*** =hint

*** =pre_exercise_code
```{r}
library(datasets)
data(women)
```

*** =sample_code
```{r}
# Load the datasets
library(datasets)
data(women)

# Store the weight rate for each tree, in `weight_rate`
weight_rate<-women$weight/women$height


# Compute average weight rate and store in `avg` using the function `mean`

# How many women are > avg ? Check using `sum`

```

*** =solution
```{r}
# Store the weight rate for each tree, in `weight_rate`
weight_rate<-women$weight/women$height

# Compute average weight rate and store in `avg` using the function `mean`
avg <-mean(weight_rate)

# How many women are > avg ? Check using sum
sum(weight_rate > avg)

```


*** =sct
```{r}
test_error()
test_object("avg", undefined_msg = "Define avg first.", incorrect_msg = "Compute the mean and store it here.")
test_function("sum", incorrect_msg = "Check the number of women above average weight rate.")
success_msg("Awesome!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:19320f72ab
## 6. Match

We’ll use the `murders` dataset for the next three exercises.

The `match()` function gives the index numbers of observations that match a supplied vector mentioned above, and then you can use `[]` to acess the names of observations that matched positively.

*** =instructions
What states are represented by abbreviations "NH", "OH"and "TN"?

*** =hint
As an example, `match(x, y)` finds the index values of `y` that match with `x`.

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```


*** =sample_code
```{r}

# Store the 3 abbreviations in `abbs`. (remember that they are character vectors)

# Match the abbs to the murders$abb and store in `ind`

# Extract and print state names with matching state abbreviations


```

*** =solution
```{r}
# Store the 3 abbreviations in `abbs`. (remember that they are character vectors)
abbs <- c("NH", "OH", "TN")

# Match the abbs to the murders$abb and store in `ind`
ind <- match(abbs , murders$abb)

# Extract and print state names with matching state abbreviations
murders$state[ind]
```

*** =sct
```{r}
test_error()
test_object("abbs", undefined_msg = "Define abbs!", incorrect_msg = "Check the abbreviations stored.")
test_object("ind", undefined_msg = "Define ind!", incorrect_msg = "Make sure to use the match function ")
test_output_contains("murders$state[ind]", incorrect_msg = "Use square brackets.")
success_msg("Awesome!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:beea127137
## 7. %in%

If, rather than a vector of index numbers, we want a logical vector that tells us whether or not each element of a vector is in another vector, we can use the operator `%in%`. Check the sample code to see how it works. 

Note: The true state abbreviations are stored in `murders$abb`.

*** =instructions
Use the `%in%` operator to create a logical vector that answers which of the following strings are actual state abbreviations in the `murders` dataset: "ND", "NE", "NM", "NN", "NY".

*** =hint
Use code `abbs%in%murders$abb`.

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}

# Store the 5 abbreviations in `abbs`. (remember that they are character vectors)


# Use the %in% command


```

*** =solution
```{r}
# Store the 5 abbreviations in `abbs`. (remember that they are character vectors)
abbs <- c("ND", "NE", "NM", "NN", "NY")

# Use the %in% command
abbs%in%murders$abb

```

*** =sct
```{r}
test_error()
test_object("abbs", undefined_msg = "Define abbs!", incorrect_msg = "Make sure to store the 5 abbreviations in abbs.")
test_output_contains("abbs%in%murders$abb", incorrect_msg = "Check the code. ")
success_msg("Awesome!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:65a74691fd
## 8. Negation operator 

*** =instructions

In the previous exercise you created a logical vector indicating whether the character strings "ND", "NE", "NM", "NN", "NY" are actual state abbreviations in `murders`. 

Now try to find the character strings that are *not* abbreviations using the negation operator `!`. 

Note: The true state abbreviations are stored in `murders$abb`.

*** =hint
Use the code `ind <- which(!abbs%in%murders$abb)`.

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}

# Store the 5 abbreviations in `abbs`. (remember that they are character vectors)


# Use the `which` command and `!` operator to find out which abbreviation is not actually part of the dataset and store in 'ind'


# Names of abbs in `ind`



```

*** =solution
```{r}
# Store the 5 abbreviations in `abbs`. (remember that they are character vectors)
abbs <- c("ND", "NE", "NM", "NN", "NY")

# Use the `which` command and `!` operator to find out which abbreviation is not actually part of the dataset and store in 'ind'
ind <- which(!abbs%in%murders$abb)

# Names of abbs in `ind`
abbs[ind]
```

*** =sct
```{r}
test_error()
test_object("abbs", undefined_msg = "Define abbs!", incorrect_msg = "Check the 5 abbreviations from the instructions.")
test_object("ind", undefined_msg = "Make sure you define ind first! ", incorrect_msg = "Use the which and ! codes." )
test_output_contains("abbs[ind]", incorrect_msg = "Have you used square brackets?")
success_msg("Awesome!")
```
----
