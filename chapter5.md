---
title       : Just some title to make this work in Datacamp
description :

--- type:NormalExercise lang:r xp:100 skills:1 key:646acee888
## 1. Changing Measurements

Previously we created these data frames -
`desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")`
`calories <- c(257, 355, 243, 411, 288)`
`desserts_calories <- data.frame(Dessert = desserts, Calorie = calories)`

*** =instructions
Remake the dataframes using the code from above.
However, add a line of code that changes the calories of these desserts from calorie units to joules.
(1 cal = 4.18 joules)
Store it in `joules`.
Include `desserts, calories, joules, desserts_joules` in the code.

*** =hint
*** =pre_exercise_code
```{r}
#no pec
```
*** =sample_code
```{r}
# Converting temperature from farenheit to celcius
temp <- c(35, 88, 42, 84, 81, 30)
temp <- (temp - 32)*4/9

# Re-make the dataframes

# Print the dataframe `desserts_joules`
```
*** =solution
```{r}
# Re-make the dataframes
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
joules<- calories*4.18
desserts_joules<- data.frame(Dessert = desserts, Joules = joules)

# Print the dataframe `desserts_joules`
desserts_joules
```
*** =sct
```{r}
test_error()
test_object("desserts", undefined_msg = "", incorrect_msg = "")
test_object("calories", undefined_msg = "", incorrect_msg = "")
test_object("joules", undefined_msg = "", incorrect_msg = "")
test_object("desserts_joules", undefined_msg = "", incorrect_msg = "")
test_student_typed("desserts_joules", not_typed_msg = "")
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
Use code: `x <- seq(1,2500)`
`sum (1/ x^3)`.

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
test_object("x", undefined_msg = "", incorrect_msg = "")
test_student_typed("sum (1/ x^3)", not_typed_msg = "")
success_msg("")
```
----


--- type:NormalExercise lang:r xp:100 skills:1 key:39eec07e4a
## 3. Arithmetic Funtions 3


*** =instructions
Compute the per 100,000 murder rate for each state and store it in the object `murder_rate`.
Then compute the average murder rate for the US using the function `mean`. What is the average?

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
```

*** =sample_code
```{r}
# Store the per 100,000 murder rate for each state in `murder_rate`


# Calculate the average murder rate in the US


```

*** =solution
```{r}

# Store the per 100,000 murder rate for each state in `murder_rate`
murder_rate <- murders$total/murders$population*100000

# Calculate the average murder rate in the US
mean(murder_rate)
```

*** =sct
```{r}
test_error()
test_object("murder_rate", incorrect_msg = "")
test_function("mean", incorrect_msg = "")
success_msg("Awesome!")

```
----
