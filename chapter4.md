---
title       : 4. Sorting
description : This chapter deals with getting more of an insight into the data we have, by helping us sort through it

--- type:NormalExercise lang:r xp:100 skills:1 key:f2c94437a4
## 1. Sort

In exploratory data analysis, we often want to sort the data. Let's see how we can do that with a sample dataset. 

The dataset we're using in this chapter is called `RatPupWeight`. Since `RatPupWeight` is a built-in dataset in R's `nmle` package, there is no need to load the data. 

The variables we're using are:

weight     : Birth weight of the rat pup
sex        : Sex of the rat pup (Male, Female)
Litter     : Litter ID number
Lsize      : Number of pups per litter
Treatment  : Level of dosage given to to the litter (High, Low, Control)

To have a look at the dataset, simply run `RatPupWeight` in the R console.


*** =instructions
- Use the `$` operator to access the weight data and store it the object `weight`.
- Then use the sort function to redefine `weight` so that it is sorted.
- Finally use the `[` operator to report the smallest weight size.
- Use sample code on the `murders` dataset (preloaded in your working environment) as reference.

*** =hint

*** =pre_exercise_code
```{r}
library(nlme)
data(RatPupWeight)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Load the datasets
library(nmle)
data(RatPupWeight)

# Access the variable `state` from the dataset `murders` and store it in an object `state`
state <- murders$state

# Sort the object and redefine the object
state <- sort(state)

# Report the smallest state
state[1]

# Access `weight` from the dataset and store it in `weight`


# Sort the object and save it in the same object


# Report the smallest weight size



```

*** =solution
```{r}
# Load the datasets
library(nmle)
data(RatPupWeight)

# Access the variable `state` from the dataset `murders` and store it in an object `state`
state <- murders$state

# Sort the object and redefine the object
state <- sort(state)

# Report the smallest state
state[1]

# Access `weight` from the dataset and store it in `weight`
weight <- RatPupWeight$weight

# Sort the object and save it in the same object
weight <- sort(weight)

# Report the smallest weight size
weight[1]
```

*** =sct
```{r}
test_error()
test_object("weight", undefined_msg = "Make sure you define the object weight.", incorrect_msg = "Check whether you have redefined it or not.")
test_output_contains("weight[1]", incorrect_msg = "Print the smallest ")
success_msg("Good job! Now you know how to sort data in an ascending order.")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:c55b4ac0f9
## 2. Order


*** =instructions
Now instead of the smallest weight size, let's find out the index number of the rat pup with the smallest weight size, using the command `o[1]`.

*** =hint
Use order instead of sort

*** =pre_exercise_code
```{r}
library(nlme)
data(RatPupWeight)
```

*** =sample_code
```{r}
# Load the datasets
library(nmle)
data(RatPupWeight)


# Access `weight` from the dataset and store it in `weight`

# Use the command `order`, to order `weight` and store in object `o`

# Find the index number of the entry with the smallest weight size


```

*** =solution
```{r}
# Access `weight` from the dataset and store it in `weight`
weight <- RatPupWeight$weight

# Use the command `order`, to order `weight` and store in object `o`
o <- order(weight)

# Find the index number of the entry with the smallest weight size
o[1]
```

*** =sct
```{r}
test_error()
test_object("weight", undefined_msg = "Define weight first.", incorrect_msg = "Make sure you save weight in weight.")
test_object("o", undefined_msg = "Make sure you define o first!", incorrect_msg = "Store weight using the order code in object o.")
test_output_contains("o[1]", incorrect_msg = "Use the command provided in the instructions.")
success_msg("Great job!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:44a224bc10
## 3. Index of max and min values

A more compact way to perform the same operation in the previous exercise is using the `which.min()` function. 
Again, use the sample code as a reference.

*** =instructions
Use the `which.min` function in one line of code to find the index number of the pup that has the smallest weight.

*** =hint
Use `which.min` directly.

*** =pre_exercise_code
```{r}
library(nlme)
data(RatPupWeight)
library(dslabs)
data(murders)
total <- murders$total
```

*** =sample_code
```{r}
# Example: Find the population of the state with the smallest number of total murders
murders$population[which.min(total)]

# Load the datasets
library(nmle)
data(RatPupWeight)

# Find the smallest value for `weight`


```

*** =solution
```{r}
# Find the smallest value for `weight`
which.min(RatPupWeight$weight)

```

*** =sct
```{r}
test_error()
test_output_contains("which.min(RatPupWeight$weight)", incorrect_msg = "Make sure you to use $ to get the weight data and simultaneously use which.min.")
success_msg("Great ! You`ve learnt another code in R!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:90b98a2790
## 4. Sorting in a dataframe

Now we know how much the smallest rat pup weighed and we know which row represents it. However, what treatment (low, high, control) did it receive ?
There are a few ways to find that out. Check out the sample code on `murders` for one example.

*** =instructions
- Define a variable `treat` to be the `Treatment` groups.
- Report the treatment group of the rat pup with the least weight using the `treat[which.min(RatPupWeight$weight)]` code.

*** =hint

*** =pre_exercise_code
```{r}
library(nlme)
data(RatPupWeight)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Example: Find out the state with the least total number of murders
murders$state[which.min(murders$total)]

# Load the datasets
library(nmle)
data(RatPupWeight)


# Define variable `treat`

# Report the treatment group of the pup with the least weight

```

*** =solution
```{r}
# Example: Find out the state with the least total number of murders
murders$state[which.min(murders$total)]

# Define variable `treat`
treat <- RatPupWeight$Treatment

# Report the treatment group of the pup with the least weight
treat[which.min(RatPupWeight$weight)]
```

*** =sct
```{r}
test_error()
test_object("treat", undefined_msg = "Define treat first!", incorrect_msg = "Assign treatment group values from dataset to object.")
test_output_contains("treat[which.min(RatPupWeight$weight)]", incorrect_msg = "Copy code from instructions.")
success_msg("Awesome! Now we have the treatment groups of the rat pups as well !")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:47c076de70
## 5. Data Frames and Ranks

Now let's take a look at how to create a data frame. The function `data.frame` takes both data frames and vectors as arguments.

As long as vectors have the same length, `data.frame` can bind them together to create a new data frame. 

Check out the sample code as a reference.


*** =instructions
- Create a dataframe called `treat_weight_rank` which with three columns:
    - the `Treatment` and `weight` columns from `RatPupWeight`
    - and a new variable `rank` which is the ranking of weight of the pups, obtained by the `rank()` function.
- There are several ways to do this. You can either create the whole dataframe at once, or begin with one or two columns and then add the other(s).

*** =hint

*** =pre_exercise_code
```{r}
library(nlme)
data(RatPupWeight)
```

*** =sample_code
```{r}
# Load the datasets
library(nmle)
data(RatPupWeight)


# Example: Store temperatures in an object 
temp <- c(35, 88, 42, 84, 81, 30)

# Example: Store city names in an object 
city <- c("Beijing", "Lagos", "Paris", "Rio de Janeiro", "San Juan", "Toronto")

# Example: Create data frame with city names and temperature 
city_temps <- data.frame(name = city, temperature = temp)

# Define variable `treat`


# Define a variable `ranks` to determine the weight size ranks


# Create a dataframe `treat_weight_rank` with the treatment groups and their ranks


```

*** =solution
```{r}
# Define variable `treat`
treat <- RatPupWeight$Treatment

# Define a variable `ranks` to determine the weight size ranks
ranks <- rank( RatPupWeight$weight)

# Create a dataframe `treat_weight` with the treatment groups and their ranks
treat_weight_rank <- data.frame(Treatment = treat, ranks = ranks)
```

*** =sct
```{r}
test_error()
test_object("treat", undefined_msg = "Define treat first!", incorrect_msg = "Assign treatment group values from dataset to object.")
test_object("ranks", undefined_msg = "Define ranks first!", incorrect_msg = "Define the rank of the weight values!")
test_object("treat_weight_rank", undefined_msg = "Define the dataframe first.", incorrect_msg = "Use the command similar to the example.")
success_msg("That`s awesome! You got this!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:22594ff7ec
## 6.  Sort a dataframe

We have practiced sorting a vector by its own order. Now try to sort every column of a data frame by the values of one of the variables (columns).

Use the sample code using the `murders` dataset as a reference. For your exercise, you will continue to work on the `RatPupWeight` dataframe.

*** =instructions

- Repeat the previous exercise but this time order `treat_weight` so that the ratpups are ordered from least heavy to most.
- Create an object ind that stores the indexes needed to order the weight values, using the `order` command.  
- Then use the bracket operator `[]` to re-order each column in the data frame.


*** =hint

*** =pre_exercise_code
```{r}
library(nlme)
data(RatPupWeight)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}

# Example: Obtain order of total number of murders and save ordering in `order_total`
order_total <- order(murders$total)

# Example: Use order_total to sort every variable in `murders`
murders <- murders[order_total,]


# Load the datasets
library(nmle)
data(RatPupWeight)


# Define variable `treat`


# Define a variable `ranks` to determine the weight size ranks


# Define a variable `ind` to store the indexes needed to order the weight values


# Create a dataframe `treat_weight` with the treatment groups and their ranks and ordered from lightest to heaviest



```
*** =solution
```{r}
# Example: Obtain order of total number of murders and save ordering in `order_total`
order_total <- order(murders$total)

# Example: Use order_total to sort every variable in `murders`
murders <- murders[order_total,]

# Define variable `treat`
treat <- RatPupWeight$Treatment

# Define a variable `ranks` to determine the weight size ranks
ranks <- rank( RatPupWeight$weight)

# Define a variable `ind` to store the indexes needed to order the weight values
ind <- order(treat)

# Create a dataframe `treat_weight` with the treatment groups and their ranks and ordered from lightest to heaviest
treat_weight <- data.frame(Treatment = treat[o], ranks = ranks[o])
```

*** =sct
```{r}
test_error()
test_object("treat", undefined_msg = "Define treat first!", incorrect_msg = "Assign treatment group values from dataset to object.")
test_object("ranks", undefined_msg = "Define ranks first!", incorrect_msg = "Define the rank of the weight values!")
test_object("ind",undefined_msg = "Define ind first.", incorrect_msg = "Use the order command as well.")
test_object("treat_weight", undefined_msg = "Define the dataframe first.", incorrect_msg = "Use the command similar to the example.")
success_msg("Great job! See how well you're building on your knowledge of R!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:f7d3786068
## 7. Missing data: NA

Take a look at a preloaded dataset `na_example`. It is a set of numbers from 1 to 1000, but with a certain number of missing values. 
In R, missing values are represented by `NA`.

You can quickly examine the object using:
      - `data(na_example)`  
      - `str(na_example)`

Function `is.na` returns a logical `TRUE` or `FALSE` indicating whether a value is `NA`. Recall that you can use a logical vector in square brackets to access values in a vector that satisfy certain conditions. 

*** =instructions

- Think of a way to find out how many `NAs` there are in `na_example`.
- Store the number in `count_na`.

*** =hint
One way is to combine `is.na()` with `sum()`. Another way is to extract all `NAs` in the vector and use `length()`.

*** =pre_exercise_code
```{r}
na_example <- sample(1:100, 1000, replace = TRUE)
na_indices <- sample.int(1000, 300)
na_example[na_indices]<-NA

```

*** =sample_code
```{r}
# Find out how many NAs there are in `na_example` and save the count in `na_count`


```

*** =solution
```{r}
# Find out how many NAs there are in `na_example` and save the count in `na_count`
na_count <- sum(is.na(na_example))

# Or
na_count <- length(na_example[is.na(na_example)])

```

*** =sct
```{r}
test_error()
test_object("ind", undefined_msg = "Make sure to define ind first.", incorrect_msg = "Check instructions for the code.")
success_msg("Great job! Now let's move to one last thing in this chapter.")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:7d6eebca10
## 8. Calculations with NA 

Run `mean(na_example)` on the right. As you can see, `NAs` mess up some operations in R and we 
might want to exclude them for those purposes. The `na.rm` argument in many functions helps remove `NAs`.

*** =instructions

Calculate the mean of all non-missing data in `na_example`, and store the mean in `mean_na_rm`. 

*** =hint

You could also use `!` and indexing to get rid of all `NAs` in the vector. 

*** =pre_exercise_code
```{r}
na_example <- sample(1:100, 1000, replace = TRUE)
na_indices <- sample.int(1000, 300)
na_example[na_indices]<-NA
```

*** =sample_code
```{r}
mean(na_example)

# Calculate the mean of all non-missing data in `na_example` and store the mean in `mean_na_rm`

```

*** =solution
```{r}
# Calculate the mean of all non-missing data in `na_example` and store the mean in `mean_na_rm`
mean_na_rm <- mean(na_example, na.rm=TRUE)

# Or
mean_na_rm <- mean(na_example[!is.na(na_example)])
```

*** =sct
```{r}
test_error()
test_object("mean_na_rm", undefined_msg = "Make sure you store the value in `mean_na_rm`.", incorrect_msg = "Check out the hint.")
success_msg("Awesome! Now you're all set with this chapter!")
```
----