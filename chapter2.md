---
title       : 2. Data Types
description :

--- type:NormalExercise lang:r xp:100 skills:1,3 key:b0bd1a7eb3

## 1. Take a first look at your dataset

In this series of exercises, you will examine the `murders` dataset. First of all, load the package `dslabs` and load the dataset `murders` using the `data()` function. Then use the `str()` function to get an idea of what variables are included.

*** =instructions 
Use the `str()` function to check the structure of the `murders` dataset.

*** =hint 
`murders` is now an R object and therefore does not need the quotations marks to be referred to.

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Use the str() function to check the structure of murders


```

*** =solution
```{r}
# Use the str() function to check the structure of murders
str(murders)
```

*** =sct
```{r}
test_output_contains("str(murders)", incorrect_msg = "Make sure you spell `murders` correctly!")
test_error()
success_msg("Good job! Head over to the next exercise.")
```
----

--- type:NormalExercise lang:r xp:100 skills:1,3 key:8f0ed4ae4f

## 2. Inspecting your dataset

Now, look at the last few rows of the `murders` dataset. The `tail()` function outputs the last 6 rows of a given dataset. 
You can change the number of rows by adding the number as a second argument in the `tail()` function. 
For example, `tail(murders, 10)` outputs last 10 rows of the dataset. 

*** =instructions
Use the `tail()` function to check the last six rows of murders.

*** =hint


*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Use the tail() function to look at the last rows of murders


```
*** =solution
```{r}
# Use the tail() function to look at the last rows of murders
tail(murders)
```

*** =sct
```{r}
test_output_contains("tail(murders)", incorrect_msg = "Make sure you spell `murders` correctly!")
test_error()
success_msg("Good job! Head over to the next exercise.")
```
----
--- type:NormalExercise lang:r xp:100 skills:1,3 key:d6e46d357d

## 3. Inspecting data type

You can see all the variables in a dataset using the `names()` command. For example, `names(murders)` lists the variables (or the column names) in the murders dataset. 

To refer to a specific variable within the dataset, you use the `$` operator. For example, `murders$state` refers to the `state` variable within the `murders` dataset. 

The `class()` command lets you know the data type of a variable. For example, `class(murders$state)` lists the data type of the `state` variable within the `murders` dataset. 

For this exercise, you will find out the data types of all the variables in the `murders` dataset. 

*** =instructions 
- Use `names()` function to find out the variables in `murders`
- Use the `class()` function to find the data types of each variable in murders

*** =hint 
Remember to use `$` operator to refer to individual variables in the dataset

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}

# Use names() to find out variables in murders. Select the command, and press 'shift' + 'enter' on your keyboard. 



# Use class() to find out data types of each variable in murders



```

*** =solution
```{r}
# # Use names() to find out variables in murders. Select the command, and press 'ctrl' + 'enter' on your keyboard. 
names(murders)

#Use class() to find out data types of each variable in murders
class(murders$region)
class(murders$state)
class(murders$population)
class(murders$abb)
class(murders$total)
```

*** =sct
```{r}
test_output_contains("names(murders)"), incorrect_msg = "Check for typos")
test_output_contains(c("class(murders$region)", "class(murders$state)", "class(murders$population)","class(murders$abb)", "class(murders$total)"), incorrect_msg = "Make sure you check all five variables!")
success_msg("That was great! Now you know the data types of all variables in your data set!")  
test_error()
```
----

--- type:NormalExercise lang:r xp:100 skills:1,3 key:0126dd4245

## 4. Factors

In the last exercise you found out that the type of the region variable is "factor". Now let’s take a closer look at this type of data.

*** =instructions 
Use the function nlevels() to check how many levels are there in the variable region.

*** =hint 
Use $ to access a variable in a data set.

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Use nlevels() to find out the number of levels in region


```

*** =solution
```{r}
# Use nlevels() to find out the number of levels in x
nlevels(murders$region)
```

*** =sct
```{r}
test_output_contains("nlevels(murders$region)", incorrect_msg = "Make sure you spell `nlevels()` correctly!")
success_msg("That was great! Let’s head over to the next exercise!")  
test_error()
```
----

--- type:NormalExercise lang:r xp:100 skills:1,3 key:f4b43c38fc

## 5. Lists in R

Remember data sets are stored as data frames, and are essentially lists in R. Now let’s create a list.

*** =instructions 
- Create a list consisting three objects: a vector c(2,5,3), a numeric value $21.3$ and a function sin. 
- Name this list `list1`. 
- Print the `list1`.

*** =hint 
Use list() to create a list.

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Create list1, which includes three objects: a vector c(2,5,3), a numeric value 21.3, and a function sin


# Print list1


```
*** =solution
```{r}
# Create list1, which includes three objects: a vector c(2,5,3), a numeric value 21.3, and a function sin
list1<-list(c(2,5,3), 21.3, sin)

# Print list1
print(list1)
```
*** =sct
```{r}
test_object("list1", undefined_msg = "Make sure you define the variable!", incorrect_msg = "Check out your code again!")
test_output_contains("print(list1)", incorrect_msg = "Type out the name, to print the variable.")
success_msg("That was great! You are done with the chapter!")  
test_error()
```