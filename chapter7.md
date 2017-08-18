---
title       : 7. Basic Data Manipulation
description : Just as the name suggests, we're going to practice the basics of data manipulation here.

--- type:NormalExercise lang:r xp:100 skills:1 key:fa7b6092fb
## 1. Mutate

The term 'data manipulation' refers to tasks that you perform to facilitate analysis on the data. In this chapter, you will learn several helpful techniques that will allow you to *clean* and *wrangle* a dataset, so that it becomes easier to use later on.

For many of those tasks, we will use the `dplyr` package, a versatile toolbox that expands upon `base R`. Many users find its syntax more intuitive when it comes to data manipulation tasks. 

One of the most useful `dplyr` functions is `mutate`. It adds a new column to a dataframe. 

This is useful if you want to calculate a summary statistic of a variable, or combine two variables, without altering the original data.

Consider this example: You have a dataset `fruits` with 2 columns `apples` and `oranges`. 

You want to add a third column `total` that is a sum of the existing 2 columns. 

You can use `mutate` to do this as follows: 

`fruits <- mutate(fruits, total = apples + oranges)`

For this exercise, the `dplyr` package is already loaded. You will add a new column `rate` to the `murders` data frame that is defined as `total/population * 100000`. 

*** =instructions
- Use `mutate()` function with the help of the syntax above to add a column `rate` to the `murders` data frame
- After running the function above, run `str(murders)` in the console to observe how the `murders` data frame has changed  

*** =hint
Use code `mutate(murders, rate =  total / population * 100000)`

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# The rate of murders can be calculated by first dividing the number of murders by the population number, and then multiplying by the desired scale (100,000).
# In base R the calculation would look as follows:
murders$total / murders$population * 100000


# Use mutate to add the `rate` column and store in `murders`

```

*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# The rate of murders can be calculated by first dividing the number of murders by the population number, and then multiplying by the desired scale (100,000).
# In base R the calculation would look as follows:
murders$total / murders$population * 100000


# Use mutate to add the `rate` column and store in `murders`
murders <- mutate(murders, rate =  total / population * 100000)
```

*** =sct
```{r}
test_error()
test_object("murders", undefined_msg = "Define murders first.", incorrect_msg = "Check the code again. Make sure you store your answer in `murders`")
success_msg("Awesome! Let's learn another command with mutate.")
```
----





--- type:NormalExercise lang:r xp:100 skills:1 key:545fbadeea
## 2. Mutate and rank 

You can create several new columns in just one line of `mutate` code. 

In this exercise, you will add another column `rank` that ranks the states by their `rate` which you added in the previous exercise. 

You want to identify the states with the highest murder rate. So, add a column `rank` that assigns scores to the states by descending values of `rate`. Recall that `rank()` function assigns a rank of 1 to the lowest value. 

*** =instructions
* Use the function `mutate` again to add a column `rate` with the per-100,000- murder rate (same as in previous exercise)
* In the same command, add a `rank` column which assigns 1 to the state with the highest murder rate, 2 to the state with the second-highest murder rate, and so on
* Use the `-` operator within the `rank()` function to rank in this order
* Run `murders` in the console to see how the data frame has changed 

*** =hint
Use the function `rank` and remember it ranks form lowest to highest by default. Use the `-` operator for descending order.

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# Use mutate to add a rate column,
# then add `rank` (highest to lowest) and store in `murders`


```

*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# Use mutate to add a rate column,
# then add `rank` (highest to lowest) and store in `murders`
murders <- mutate(murders, rate =  total / population * 100000, rank = rank(-rate))
```

*** =sct
```{r}
test_error()
test_object("murders", incorrect_msg = "Remember, rank from highest to lowest.")
success_msg("Good job!")
```





--- type:NormalExercise lang:r xp:100 skills:1 key:555ca41873
## 3. Filter 

From a large data frame, you might want to subset certain *rows* based on a criteria met by one of the columns. 

For example, from a data frame `food` with a column on `calories`, you might want to extract a subset of *rows* with food that has a calorie value less than 100. 

You can do this using the `filter()` function. 

`filter(food, calories < 100)` will help you achieve this operation. 

Now, consider the `murders` dataset. In the previous exercise, you added a new column `rank` that ranked the states based on their murder rates. In this exercise, use the `filter` function to retrieve the *rows* that correspond to the 'unfortunate' top 8 states with the highest murder rates. 


*** =instructions

Using `rank` column in the `murders` dataset, `filter` the top 8 states with the highest murder rates

*** =hint
Use `filter` to select the observations with a `rank` of less than or equal to 8, i.e. `rank <= 8`


*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)

# Use mutate to add a rate column, rank from highest to lowest and store in `murders`
murders <- mutate(murders, rate =  total / population * 100000, rank = rank(-rate))

# Select the top 8 states with the highest murder rates (using the `murders` dataframe)

```

*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# Use mutate to add a rate column, rank from highest to lowest and store in `murders`
murders <- mutate(murders, rate =  total / population * 100000, rank = rank(-rate))

# Select the top 8 states with the highest murder rates (using the `murders` dataframe)
filter(murders, rank <= 8)
```

*** =sct
```{r}
test_error()
test_output_contains("filter(murders, rank <= 8)", incorrect_msg = "Make sure you've written `murders` in your code.")
success_msg("Great job!")
```
----





--- type:NormalExercise lang:r xp:100 skills:1 key:42352c70c5
## 4. Filter and Negation Operator '!'

As you know by now, the `!` symbol means *not* and can be used to reverse an operation. 

This operator comes in handy when you want to select all observations that do not fall into a certain category. 

For example, if you have a dataset including a column with professions and you want to exclude one type of profession. 
It would be tedious to write `filter(data, profession = "...")` and list all professions you want to include. 

Instead, you could make this selection task much easier with the `!` symbol, by writing `filter(data, profession != "...")` and then listing the one profession you want to exclude. 

For this exercise, you will filter the states that are not in the *West* region and store them in a new data frame called `no_west`. 

In the code, you find `levels(murders$region)` command to list the levels in the `region` column. 

*** =instructions
- In the data frame `no_west`, assign the filtered results of `murders` that removes states from the *West*
- Use `nrow()` function to print the number of states that are in `no_west`
- Run `no_west` in the console and observe the data frame

*** =hint
Use filter and the `!=` operator. 

Since `region` is of character data type, you need to use `region != "West"` in the `filter()` function. 

You can use `nrow` to quickly get the number of rows of a data frame.


*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# Note that the `region` column tells you whether a state is in the West or not
levels(murders$region)

# Create the new dataframe `no_west` by using `filter`


# Number of states (rows) in this dataframe 

```

*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# Note that the `region` column tells you whether a state is in the West or not
levels(murders$region)

# Create the new dataframe `no_west` by using `filter`
no_west <- filter(murders, region != "West")

# Number of states (rows) in this dataframe 
nrow(no_west)
```

*** =sct
```{r}
test_error()
test_object("no_west", undefined_msg = "Define no_west first!", incorrect_msg = "Make sure you`re excluding the states not in the West.")
test_output_contains("nrow(no_west)", incorrect_msg = "You need the number of rows for the number of states.")
success_msg("That's great! Let's move to the next exercise.")
```
----





--- type:NormalExercise lang:r xp:100 skills:1 key:18111c7bfd
## 5. Filter and %in%

You have dealt with relatively short `filter` statements, where you selected variables using a logical operation, such as `rank <= 8` and `region != "West"`.

If you are dealing with a longer list of criteria, the `%in%` operator becomes important. 

It allows you to check whether an observation takes on *one* of the specified values. 

In the example of the hypothetical dataset with different professions, this would allow you to select all observations that are part of a certain group by writing `filter(data, profession %in% c("Barber", "Chef", "Doctor"))`.

*** =instructions
- In a new dataframe `murders_ns`, store filtered states from `murders` dataset, whose `region` is either "Northeast" or "South" 
- Use `nrow()` function to print the number of states that are in `murders_ns`
- Run `murders_ns` in the console and observe the data frame 


*** =hint
```{r}
Use filter and the %in% operator. You can use nrow to quickly get the number of rows of a data frame.
```

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# Create a new dataframe called `murders_ns` with only the states from the Northeast and the South


# Number of states (rows) in this dataframe 

```

*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)
## The data is already preloaded in the dataframe `murders`

# Create a new dataframe called `murders_ns` with only the states from the Northeast and the South
murders_ns <- filter(murders, region %in% c("Northeast", "South") )

# Number of states (rows) in this dataframe
nrow(murders_ns)
```

*** =sct
```{r}
test_error()
test_object("murders_ns", undefined_msg = "Define murders_ns first.", incorrect_msg = "Make sure you're using the %in% command.")
test_output_contains("nrow(murders_ns)", incorrect_msg = "You need the number of rows again, same as in the previous question.")
success_msg("This is great!")
```
----





--- type:NormalExercise lang:r xp:100 skills:1 key:e572c8806a
## 6. Combining functions (1)


You are becoming pretty good at this. so now, you can do advanced data selection. 

What if you wanted to live only in certain parts of the country and want the murder rate to be below a certain threshold? 

You can filter out the states that meet both these criteria by combining the data manipulation commands you have learnt in the previous exercises. 

You combine the criteria in the `filter` function using the `&` operator. 
For example, `new_data <- filter(data, condition1 & condition2)` would help you filter the data that meet both 'condition1' and 'condition2'. 

*** =instructions
- In a data frame `my_states`, store the filtered states from `murders` dataset with `region` in the "Northeast" or "South" as well as with murder rate less than 2 
- Use `nrow()` function to print the number of states that are in `my_states`
- Run `my_states` in the console and observe the data frame 


*** =hint
Use `filter`, the `%in%` operator and the `<` sign. The `&` sign can be used to combine two or more conditions.


*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)

# Use mutate to add a rate column and store in `murders`
murders <- mutate(murders, rate =  total / population * 100000)

# Select states that satisfy both conditions and store their entries in `my_states`


# Number of states (rows) in this dataframe

```

*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)

# Use mutate to add a rate column and store in `murders`
murders <- mutate(murders, rate =  total / population * 100000)

# Select states that satisfy both conditions and store their entries in `my_states`
my_states <- filter(murders, region %in% c("Northeast", "South") & rate < 2)

# Number of states (rows) in this dataframe
nrow(my_states)
```

*** =sct
```{r}
test_error()
test_object("my_states", undefined_msg = "Define my_states first!", incorrect_msg = "Use the filter, %in% and < commands.")
test_output_contains("nrow(my_states)", incorrect_msg = "You need the number of rows again, same as previous question.")
success_msg("Now you know how to combine functions and use them to get specific answers. Let's try it one more time!")
```
----





--- type:NormalExercise lang:r xp:100 skills:1 key:3d4de3a34a
## 7. Combining functions (2)

To find the number of entries, it is not always necessary to create a new object. 

To improve efficiency, you can use the pipe (`%>%`) operator, which allows you to run `filter` and `nrow` operations sequentially, without creating a new data frame.

In this exercise, you will repeat the previous exercise but instead of creating a new object, you will print the result directly. This result should only have `state`, `rate` and `rank` columns. 

You select these columns using the `select` function in `dplyr`, and using this function with the pipe (`%>%`) operator after the `filter` function. 

For example, `filter(...) %>% select(column1, column2,..)` will print the rows that satisfy the conditions in the `filter` function, and only the columns specified in the `select` function. 

*** =instructions
- Use `filter` function to set the criteria of `region` being either "Northeast" or "South" as well as `rate` < 2
- In the same command, use the pipe (`%>%`) operator and then `select` function to include `state`, `rate`, `rank` columns 

*** =hint
Use the same `filter` operation as in the previous exercise. Then use the pipe (`%>%`) and add `select(state, rate, rank)`.
    
*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)

# Use mutate to add a rate column and store in `murders`, and to add a rank column
murders <- mutate(murders, rate =  total / population * 100000, rank = rank(-rate))

# Show the result and only include the state, rate, and rank columns, all in one line

```
*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)

# Use mutate to add a rate column and store in `murders`, and to add a rank column
murders <- mutate(murders, rate =  total / population * 100000, rank = rank(-rate))

# Show the result and only include the state, rate, and rank columns, all in one line
filter(murders, region %in% c("Northeast", "South") & rate < 2) %>% select(state, rate, rank)
```
*** =sct
```{r}
test_error()
test_function("filter", incorrect_msg = "Everything needs to be in one line! Use a pipe to help.")
success_msg("You're getting a pretty good hang of stuff now!")
```
----




--- type:NormalExercise lang:r xp:100 skills:1 key:1b45c7acac
## 8. Combining functions (3)

You have almost mastered the basics of data manipulation. Now, it is time to polish and apply what you have have learnt so far and become even more efficient. 

In this exercise, you will use pipes to repeat and combine all the steps you did in previous exercises.


*** =instructions
- In a dataframe `my_states`, use `%>%` to combine the following operations
    - Use `mutate()` for `murders` dataframe to add the murder `rate` for each state and create a `rank` variable (descending order of `rate`)
    - Use `filter()` to select the states that are in the Northeast or South and have a murder rate of less than 2
    - Use `select()` to select the columns `state`, `rate` and `rank`

*** =hint
```{r}
Use `mutate`, `filter` and `select` combining them with `%>%`.
```

*** =pre_exercise_code
```{r}
library(dplyr)
library(dslabs)
data(murders)
```

*** =sample_code
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)

# Create new data frame called `my_states` (with specifications in the instructions)

```

*** =solution
```{r}
# Loading the libraries
library(dplyr)
library(dslabs)
data(murders)

# Create new data frame called `my_states` (with specifications in the instructions)
my_states <- mutate(murders, rate =  total / population * 100000, rank = rank(-rate)) %>%
filter(region %in% c("Northeast", "South") & rate < 2) %>%
select(state, rate, rank)

# You could also use this alternative form where you type `murders` before `mutate` function
my_states <- murders %>% 
mutate(rate =  total / population * 100000, rank = rank(-rate)) %>%
filter(region %in% c("Northeast", "South") & rate < 2) %>%
select(state, rate, rank)
```

*** =sct
```{r}
test_error()
test_object("my_states", undefined_msg = "Define my_states!", incorrect_msg = "Make sure you use pipes to put everything in one line.")
success_msg("This is absolutely awesome! You now know how to use basic data manipulation techniques in R.")
```
