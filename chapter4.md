---
title       : Sorting
description : This chapter deals with getting more of an insight into the data we have, by helping us sort through it

--- type:NormalExercise lang:r xp:100 skills:1 key:f2c94437a4
## 1. Sort

When looking at a dataset, we may want to sort the data in an order that makes more sense to analyse it.
The dataset we're using in this chapter is called `RatPupWeight`. The variables we're using are:

weight       : Birth weight of the rat pup
sex            : Sex of the rat pup (Male, Female)
Litter          : Litter ID number
Lsize          : Number of pups per litter
Treatment  : Level of dosage given to to the litter (High, Low, Control)

If you want to, you can have a look at the entire data by typing `View(RatPupWeight)` in the R console.


*** =instructions
Use the `$` operator to access the weight data and store it the object `weight`.
Then use the sort function to redefine `weight` so that it is sorted.
Finally use the `[` operator to report the smallest weight size.


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
## 3. New Codes

We can actually perform the same operation as in the previous exercise using the function `which.min`. It basically tells us which is the minimum value.

*** =instructions
Write one line of code that gives the index of the lowest population entry, using the `which.min` command.

*** =hint
Use `which.min` directly.

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


# Find the smallest value for variable `total`
which.min(murders$total)

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
## 4. Learning more about Ordering

Now we know how much the smallest rat pup weighed and we know which row represents it. However, what treatment (low, high, control) did it receive ?

*** =instructions
Define a variable `treat` to be the `Treatment` groups.
Report the treatment group of the rat pup with the least weight using the `treat[which.min(RatPupWeight$weight)]` code.

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


# Define variable `treat`

# Report the treatment group of the pup with the least weight

```

*** =solution
```{r}
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

You can create a data frame using the data.frame function. Here is a quick example:

`temp <- c(35, 88, 42, 84, 81, 30)`
`city <- c("Beijing", "Lagos", "Paris", "Rio de Janeiro", "San Juan", "Toronto")`
`city_temps <- data.frame(name = city, temperature = temp)`


*** =instructions
Use the `rank(RatPupWeight$weight)` function to determine the weight rank (from smallest to biggest) of each rat pup.
Save these ranks in an object called `ranks`.
Then create a data frame with the treatment groups and its rank. Call the data frame `treat_weight`.


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


# Store temperatures in an object
temp <- c(35, 88, 42, 84, 81, 30)

# Store city names in an object
city <- c("Beijing", "Lagos", "Paris", "Rio de Janeiro", "San Juan", "Toronto")

# Create data frame with city names and temperature
city_temps <- data.frame(name = city, temperature = temp)

# Define variable `treat`

# Define a variable `ranks` to determine the weight size ranks

# Create a dataframe `treat_weight` with the treatment groups and their ranks

```

*** =solution
```{r}
# Define variable `treat`
treat <- RatPupWeight$Treatment

# Define a variable `ranks` to determine the weight size ranks
ranks <- rank( RatPupWeight$weight)

# Create a dataframe `treat_weight` with the treatment groups and their ranks
treat_weight <- data.frame(Treatment = treat, ranks = ranks)
```

*** =sct
```{r}
test_error()
test_object("treat", undefined_msg = "Define treat first!", incorrect_msg = "Assign treatment group values from dataset to object.")
test_object("ranks", undefined_msg = "Define ranks first!", incorrect_msg = "Define the rank of the weight values!")
test_object("treat_weight", undefined_msg = "Define the dataframe first.", incorrect_msg = "Use the command similar to the example.")
success_msg("That`s awesome! You got this!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:22594ff7ec
## 6. Data Frames, Ranks and Orders

*** =instructions

Repeat the previous exercise but this time order `treat_weight` so that the ratpups are ordered from least heavy to most.
Create an object ind that stores the indexes needed to order the weight values, using the `order` command.  
Then use the bracket operator [ to re-order each column in the data frame. example: `abb = abb [0]`


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


# Define variable `treat`

# Define a variable `ranks` to determine the weight size ranks

# Define a variable `ind` to store the indexes needed to order the weight values

# Create a dataframe `treat_weight` with the treatment groups and their ranks and ordered from lightest to heaviest



```
*** =solution
```{r}
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
## 7.NA (really, the chapter is called NA)

The na_example represents a series of counts. You can quickly examine the object using

`data(na_example)`  
`str(na_example)`

However, when we compute the average we obtain an NA

`mean(na_example)`

*** =instructions
The `is.na` returns a logical vector that tells us which entries are NA.
Assign this logical vector to an object called `ind`, using code `is.na(na_example)` and determine how many NA does na_example have, using the `sum` command?

*** =hint
```{r}

```
*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/na_example.rda"))
```

*** =sample_code
```{r}
# Using new dataset
data(na_example)  

# Checking the structure
str(na_example)

# Find out the mean of the entire dataset
mean(na_example)

# Assign `is.na` to logical vector `ind`

# Determine how many NA does `ind` have?


```

*** =solution
```{r}
# Assign `is.na` to logical vector `ind`
ind <- is.na(na_example)

# Determine how many NA does `ind` have?
sum(ind)

```

*** =sct
```{r}
test_error()
test_object("ind", undefined_msg = "Make sure to define ind first.", incorrect_msg = "Check instructions for the code.")
test_output_contains("sum(ind)", incorrect_msg = "Use the sum command to get the number of NAs.")
success_msg("Great job! Now let's move to one last thing in this chapter.")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:7d6eebca10
## 8. NA !

We can leave out the points that are NA and do operations on the rest.

*** =instructions
Compute the average again but only for the entries that are not NA making use of the `!` operator before `ind`.

*** =hint
```{r}
Remember the ! operator. Use code "mean(na_example[!ind])".
```
*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/na_example.rda"))
ind <- is.na(na_example)
```

*** =sample_code
```{r}
# Compute the average, for entries that are not NA


```

*** =solution
```{r}
# Compute the average, for entries that are not NA
mean(na_example[!ind])
```

*** =sct
```{r}
test_error()
test_output_contains("mean(na_example[!ind])", incorrect_msg = "Check your code from the instructions again.")
success_msg("Awesome ! Now you're all set with vectors! Get practicing on your own!")
```
----
