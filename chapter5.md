---
title       : 5. Vector Arithmetics
description :

--- type:NormalExercise lang:r xp:100 skills:1 key:646acee888
## 1. Changing measurements

Previously we created data frames with the calories of some yummy desserts. (in calorie units). 
Run the first few lines to reload the data values. How can we change their values from calories to joules?

*** =instructions
- In the `dessert_joules` dataframe, change the calories column from calories to joules. (1 cal = 4.18 joules)
- Store it in `joules`.
- Store the modified dataframe as `desserts_joules` again.
- Print the new dataframe.
- Check sample code to see how to perform calculations on each and every element in a vector.

*** =hint

*** =pre_exercise_code
```{r}
#no pec
```
*** =sample_code
```{r}
# Example: Converting temperature from farenheit to celcius
temp <- c(35, 88, 42, 84, 81, 30)
temp <- (temp - 32)*4/9

# Code from previous exercises:
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
desserts_calories <- data.frame(Dessert = desserts, Calorie = calories)

# Convert from calories to joules 


# Re-make the dataframe - `desserts_joules`


# Print the dataframe `desserts_joules`



```
*** =solution
```{r}
# Example: Converting temperature from farenheit to celcius
temp <- c(35, 88, 42, 84, 81, 30)
temp <- (temp - 32)*4/9

# Code from previous exercises:
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
desserts_calories <- data.frame(Dessert = desserts, Calorie = calories)

# Convert from calories to joules
joules<- calories*4.18

# Re-make the dataframes
desserts_joules<- data.frame(Dessert = desserts, Joules = joules)

# Print the dataframe `desserts_joules`
desserts_joules
```

*** =sct
```{r}
test_error()
test_object("joules", undefined_msg = "Define joules first.", incorrect_msg = "Check the conversion rate.")
test_object("desserts_joules", undefined_msg = "Define desserts_joules first.", incorrect_msg = "Create the dataframe with joules instead of calories.")
test_student_typed("desserts_joules", not_typed_msg = "Just type out the variable you need to print.")
success_msg("Awesome!")
```
----


--- type:NormalExercise lang:r xp:100 skills:1 key:b7994768fd
## 2. Sum and Seq

Let's use the functions of sequence and sum that we've learnt earlier.

*** =instructions
What is the sum of the following :
`1 + 1/(2^3) + 1/ (3^3) +...+ 1/(2500^3)`?

*** =hint
Use the seq command first and then the seq. 

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Create a sequence of numbers from 1-2500 and store it in `x`


# Use the `sum` command to answer the question


```
*** =solution
```{r}
# Create a sequence of numbers from 1-2500 and store it in `x`
x <- seq(1,2500)

# Use the `sum` command to answer the question
sum (1/ x^3)
```
*** =sct
```{r}
test_error()
test_object("x", undefined_msg = "Define x first.", incorrect_msg = "Use the seq command.")
test_student_typed("sum (1/ x^3)", not_typed_msg = "Check the formula.")
success_msg("Awesome! Good job.")
```
----


--- type:NormalExercise lang:r xp:100 skills:1 key:39eec07e4a
## 3. Vector arithmetic with multiple vectors

In the previous exercises, only one of the values in an operation was a vector, and the other was just one number (scalar). In such cases, R creates a vector of the same length with repeated values of the single number, and then perform the calculation on matching elements of the two vectors.

Run the sample code on the right to seehow it works. Note how shorter vectors (including single values) are "recycled", and you get a warning when the length of the longer vector is not a multiple of the shorter vector.

*** =instructions

Recall we used the `murders` dataset from the `dslabs` package in previous chapters. Load the package and dataset with appropriate commands. To recall the column names, run `names(murders)`

Compute the murder rate per 100,000 people for each state and store it in the vector `murder_rate`. Then compute the average murder rate per 100,000 people across all US states.

*** =hint

Murder rate per x = (total number of murders / population) * x

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Example: Vectors and scalars
x <- c(1,3,5,7,9,11)
y <- 6:10
z <- c(100, 1000)
x + y
x * z

# Load the dslabs package and murders dataset
library(dslabs)
data(murder)

# Store the per 100,000 murder rate for each state in `murder_rate`


# Calculate and print the average per 100,000 murder rate in the US 

```

*** =solution
```{r}
# Load the dslabs package and murders dataset
library(dslabs)
data(murders)

# Store the per 100,000 murder rate for each state in `murder_rate`
murder_rate <- murders$total/murders$population*100000

# Calculate and print the average murder rate in the US
mean(murder_rate)
```

*** =sct
```{r}
test_error()
test_object("murder_rate", incorrect_msg = "Make sure you multiply the murder rate by 100,000.")
test_output_contains("mean(murder_rate)")
success_msg("Awesome! You are done with this chapter.")
```
----