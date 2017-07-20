---
title       : 7. Basic Data Manipulation
description : Just as the name suggests, we're going to practice the basics of data manipulation here.

--- type:NormalExercise lang:r xp:100 skills:1 key:fa7b6092fb
## 1. Mutate

Data manipulation? Are you telling me to lie with my data? By no means! The term data manipulation refers to tasks that you perform to facilitate analysis on the data. In this chapter you will learn several helpful techniques that will allow you to *clean* and *wrangle* a dataset so that it becomes easier to use later on.

For many of those tasks we will use the `dplyr` package, a versatile toolbox that expands upon `base R`. Many users find its syntax more intuitive when it comes to data manipulation tasks. So let's dive right in and explore one of the most useful `dplyr` functions.

`mutate` essentially adds a new column to a dataframe. This is useful if we want to calculate a summary statistic of a variable, or combine two variables, without altering the original data.

In this exercise, you will load in the `dplyr` package and add a new column to the `murders` dataset.

*** =instructions
* Calculate the "per-100.000" murder rate for each state.
* By using `mutate`, add a column called `rate` containing this information to the `murders` dataframe.

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
Now that we have calculated the murder rate for each state, we want to order our dataset by the size of the murder rate. We want to identify the states with the highest murder rate, so let us add a column `rank` that assigns scores to the states by descending values of `rate`. You can create several new columns in just one line of `mutate` code.

*** =instructions
* Use the function `mutate` again to add a column `rate` with the per-100,000- murder rate (same as in previous exercise).

* Add a `rank` column which assigns 1 to the state with the highest murder rate, 2 to the state with the second-highest murder rate, and so on.

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
murders <- mutate(murders, rate =  total / population * 100000, rank = )
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
Now let us zoom in closer to the states with the highest murder rates. We want to identify the list of states that are part of this unfortunate "top 8". The function `filter` can be used to subset *rows* of a dataset by specifying which values of a certain *column* to select.

*** =instructions
* Use the function `filter` to show the top 8 states with the highest murder rates. Do not store in `murders`, just show the result.

* To perform the operation, use the `rank` column we created in the previous exercise.


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
## 4. Filter and ! 
Filter and shout? No worries, `R` is not trying to yell at us. The `!` symbol means *not* and can be used to reverse an operation.

This operator comes in handy when we want to select all observations that do not fall into a certain category. For example, imagine we had a dataset including a column with professions and we wanted to exclude one type of profession. It would be tedious to write `filter(data, profession = "...")` and list all professions we want to include. We can make this selection task much easier with the `!` symbol, by writing `filter(data, profession != "...")` and then listing the one profession we want to exclude

*** =instructions
Create a new data frame called `no_west` that removes states from the West. 
How many states are in this category? 

*** =hint
Use filter and the `!=` operator. You can use `nrow` to quickly get the number of rows of a data frame.


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
So far we have dealt with relatively short `filter` statements, where we either selected variables less than or equal to a certain value (`rank <= 8`), or equal to a certain string value (`region != "West"`).

If we are dealing with a longer list of criteria, the `%in%` operator becomes important. It allows us to check whether an observation takes on *one* of the specified values. In our example of the hypothetical dataset with different professions, this would allow us to select all observations that are part of a certain group by writing `filter(data, profession %in% c("Barber", "Chef", "Doctor"))`.

*** =instructions
Create a new dataframe called `murders_ns` with only the states from the Northeast and the South. How many states are in this category? 


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
## 6. Combining functions 
You are becoming pretty good at this, so we can become pickier! What if we wanted to live only in certain parts of the country and want the murder rate to be below a certain threshold? No problem - by combining the data manipulation commands we have learned, you can identify such subsets.

*** =instructions
* Suppose you want to live in the Northeast or South and want the murder rate to be less than 2. 

* Create a table `my_states` with entries that satisfy both of these conditions.
How many states are in this table?

*** =hint
Use `filter`, the `%in` operator and the `<` sign. The `&` sign can be used to combine two or more conditions.


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
## 7. Combining functions 2 
To find the number of entries, it is not always necessary to create a new object. To improve efficiency, we can use the pipe (`%>%`) operator, which allows us to run our `filter` and `nrow` operations sequentially, without creating a new dataframe.

*** =instructions
* Repeat the previous exercise, but now instead of creating a new object, show the result directly and only include the state, rate, and rank columns. 
* Use a pipe (`%>%`) to do this in just one line. Remember that you can use `dplyr`'s `select` function to include only certain columns.
* Reminder: We want to select states in the Northeast and South with a murder rate of less than 2.

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
## 8. Combining functions 3 
You have almost mastered the basics of data manipulation. Now it is time to polish what we have learned so far and become even more efficient. In this exercise, we will use pipes to repeat and combine all the steps we have taken in previous exercises.


*** =instructions
* Calculate the murder `rate` for each state and create a `rank` variable (descending order of `rate`).
* Select the states that are in the Northeast or South and have a murder rate of less than 2. 
* Select the columns `state`, `rate` and `rank`. Use `%>%` to combine these three steps and store the final result in the object `my_states`.

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
