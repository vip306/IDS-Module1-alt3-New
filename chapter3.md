---
title       : 3. Vectors
description :

--- type:NormalExercise lang:r xp:100 skills:1 key:ddf0db0f7d

## 1. Character vector

Vectors are one-dimensional arrays that can store different types of data such as numeric data, character data, and logical data. 
In R, you create a vector with the concatenate function `c()`.  

See how you would create a character vector in the sample code.

*** =instructions

- Create a character vector `desserts` using the function `c()` with names of 5 desserts: "cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding"
- print `desserts` and observe the output

*** =hint
Be sure to place the names within double inverted commas.

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Example: Create a character vector to store the different types of food items and assign it to `food`
food <- c("pizza", "burgers", "salads", "cheese", "pasta")

# Create a character vector to store the names of 5 desserts and assign it to `desserts`


# Print the vector `desserts`


```

*** =solution
```{r}
# Example: Create a character vector to store the different types of food items and assign it to `food`
food <- c("pizza", "burgers", "salads", "cheese", "pasta")

# Create a character vector to store the names of 5 desserts and assign it to `desserts`
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")

# Print the vector `desserts`
desserts

```

*** =sct
```{r}
test_error()
test_object("desserts", incorrect_msg = "Each of the dessert names need inverted commas.")
test_object("desserts", incorrect_msg = "Check the spelling of the variable")
success_msg("Good job! Do you want to now try creating a numeric vector!?")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:5e66879c2c

## 2. Numeric Vector  

Now, you will create a numeric vector. The main difference between a numeric and character vector is that you don't need quotation marks in numeric vector. 

See how you would create a numeric vector in the sample code.

*** =instructions

- Create a numeric vector `calories` with the calories of the desserts from the previous exercise: 257, 355, 243, 411, 288
- Type `calories` in the console to observe how the output looks like

*** =hint
Make sure your numbers are within parenthesis and have commas separating them.

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Example: Create a numeric vector to store the cost of different food items and assign it to `cost`
cost <- c(50, 75, 90, 100, 150)

# Create a numeric vector to store the calories of the desserts and assign it to `calories`


```

*** =solution
```{r}
# Example: Create a numeric vector to store the cost of different food items and assign it to `cost`
cost <- c(50, 75, 90, 100, 150)

# Create a numeric vector to store the calories of the desserts and assign it to `calories`
calories <- c(257, 355, 243, 411, 288)

```

*** =sct
```{r}
test_error()
test_object("calories", incorrect_msg = "Check to match the numbers from the question!")
success_msg("Awesome! Now you've learnt to create both numeric and character vectors!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:c0b17dfdc7
## 3. Named Vector

When you defined the numeric vector in the previous exercise, you listed the numbers in the same order as the desserts' names in the first exercise. Now, you will learn to use the character vector to name the numeric vector elements. 

You use the `names()` function to do this. 

`names(num_vct) <- char_vct` will name the numbers in the numeric vector `num_vct` with the elements in the character vector `char_vct`.  

You can see an example of how this is done in the sample code.

*** =instructions
- Use the `names()` function and the objects defined in the previous exercises to give the numeric values (calories) their corresponding names (desserts)
- Type `calories` in the console and observe how the vector has changed

*** =hint
Assign names to the numeric values. 

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Example 1: Name directly and print
codes <- c("italy" = 380, "canada" = 124, "egypt" = 818)
codes

# Example 2: Or indirectly using `names()` and print 
codes <- c(380, 124, 818)
countries <- c("italy", "canada", "egypt")
names(codes) <- countries
codes

# Dessert names and calories from the previous question
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")
calories <- c(257, 355, 243, 411, 288)

# Associate the dessert with the calories using the `names` function


```

*** =solution
```{r}
# Example 1: Name directly and print
codes <- c("italy" = 380, "canada" = 124, "egypt" = 818)
codes

# Example 2: Or indirectly using `names()` and print 
codes <- c(380, 124, 818)
countries <- c("italy", "canada", "egypt")
names(codes) <- countries
codes

# Dessert names and calories from the previous question
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")
calories <- c(257, 355, 243, 411, 288)

# Associate the dessert with the calories using the `names` function
names(calories) <- desserts
```

*** =sct
```{r}
test_error()
test_function("names", incorrect_msg = "The numeric vector should be in the parenthesis.")
success_msg("Great job! You have now learnt to create a named vector!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:7c4dfa097b
## 4. Class

When you use R to analyze data, it is always a good practice to keep track of the class of an object. 

You can do that using the `class(<object name>)` command. 

Common classes include: an integer, a numeric value, a character, a logical value, and a factor. 

*** =instructions
Determine the class of `desserts`.

*** =hint

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Store values for desserts, same as previous question
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")

# Determine the class of `desserts`


```

*** =solution
```{r}
# Store values for desserts, same as previous question
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")

# Determine the class of `desserts`
class(desserts)
```

*** =sct
```{r}
test_error()
test_output_contains("class(desserts)", incorrect_msg = "Don't put desserts within parenthesis.")
success_msg("That's great! Let's use some operators on this data now.")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:925fcceb04
## 5. Indexing Vector Elements (Part 1)

If you want to display only select values from a vector, R can help you do that easily. 

You can use square brackets (`[]`) to specify which elements you would like to select, as can be seen in the example on the right.

Note that you could also type `cost [c(3,4,5)]` and get the same result as `cost[3:5]`. The `:` operator helps you condense the code and get consecutive values. 

*** =instructions
Use the `[]` and `:` operators to access the calories of the first 3 elements in the list of `calories`.

*** =hint
Square brackets and : are the important bits in this.

*** =pre_exercise_code
```{r}
cost <- c(50, 75, 90, 100, 150)
food <- c("pizza", "burgers", "salads", "cheese", "pasta")
names(cost) <- food
```

*** =sample_code
```{r}
# Example: Cost of the last 3 food items
cost[3:5]
cost[c(3,4,5)]

# Defining dessert names and calories (code from previous exercises)
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
names(calories) <- desserts

# Calories of the first 3 desserts


```

*** =solution
```{r}
# Example: Cost of the last 3 items in our food list
cost[3:5]

# Defining dessert names and calories (code from previous exercises)
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
names(calories) <- desserts

# Calories of the first 3 desserts
calories[1:3]

```

*** =sct
```{r}
test_error()
test_output_contains("calories[1:3]", incorrect_msg = "The square brackets and colon operators are essential to this command.")
success_msg("Awesome! You`ve learnt how to make your work easier.")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:7e98f2ad1b
## 6. Indexing Vector Elements (Part 2) 

In the previous exercise, you used operator `:` to access consective elements in a vector. Now, you will learn to access
any elements in a vector.

You mention the index of the elements you want to display separated by commas. 

`vct_name[c(index1,index2)]` will print the elements of the `vct_name` in `index1` and `index2` locations of the vector. 

Run the sample code to see how this is done.

*** =instructions
Use the `[]` operator to access the calories of the `chocolate mousse`(2nd) and `pudding`(5th).

*** =hint
Use `c()` function to create a numeric vector to index elements of a vector.

*** =pre_exercise_code
```{r}
cost <- c(50, 75, 90, 100, 150)
food <- c("pizza", "burgers", "salads", "cheese", "pasta")
names(cost) <- food
```

*** =sample_code
```{r}
# Access the cost of pizza and pasta from our food list
cost [c(1,5)]

# Defining dessert names and calories (code from previous exercises)
desserts <- c("cheesecake", "chocolate mousse", "brownie", "apple pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
names(calories) <- desserts

# Access the calories for chocolate mousse and brownie


```

*** =solution
```{r}
# Access the cost of pizza and pasta from our food list
cost [c(1,5)]

# Defining dessert names and calories (code from previous exercises)
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
names(calories) <- desserts

# Access the calories for chocolate mousse and brownie
calories[c(2,5)]

```

*** =sct
```{r}
test_error()
test_output_contains("calories[c(2,5)]", incorrect_msg = "You need to use `c` and parenthesis inside the square brackets.")
success_msg("Isn`t that awesome! Let`s move to the next exercise!")
```
----



--- type:NormalExercise lang:r xp:100 skills:1 key:02d64318c8
## 7. Sequences

`seq()` is a function in R with which you can easily generate numeric vectors with a certain pattern.

You can create different types of sequences in R. 
For example,to create a vector with the multiples of 7, smaller than 50, the code would be `seq (7, 49, 7)`, where:

- the first argument defines the start,
- the second the end, and
- the third tells how much to jump by (increments)

Run the sample code to see how you can create a sequence of numbers within a certain range with a specified increment. 

*** =instructions
- Create a vector containing all the positive odd numbers smaller than 1000
- 

*** =hint
```{r}
If you start at 1 and jump by 2, you`ll get the positive odd numbers.
```
*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Example: Create a vector with all non-negative multiples of 7 smaller than or equal to 50
seq(from = 0, to = 50, by = 7) 

# Example: Or more concisely
seq(0, 50, 7) 

# Create a vector containing all the positive odd numbers smaller than 100.


```
*** =solution
```{r}
# Example: Create a vector with all non-negative multiples of 7 smaller than or equal to 50
seq(from = 0, to = 50, by = 7) 

# Example: Or more concisely
seq(0, 50, 7) 

# Create a vector containing all the positive odd numbers smaller than 100.
seq (1,100,2)
```

*** =sct
```{r}
test_error()
test_output_contains("seq (1,100,2)", incorrect_msg = "Make sure the third argument has the value the sequence needs to jump by.")
success_msg("Awesome! Let`s `jump` to the next exercise.")
```
----


--- type:NormalExercise lang:r xp:100 skills:1 key:373b201f36
## 8. Length of a Vector  

Recall that in the last exercise we created sequences of numeric values within a certain range with a specified increment. 

Now consider how to find out how many numeric elements are included in such sequences. 

Use the sample code as reference.

*** =instructions
- Create a vector of numbers that start at 99 and don’t exceed 999, in increments of 9: 99, 18,...999
- How many numbers does the list have?
- Use only one line of code to answer both questions.

*** =hint
```{r}
Use length and then seq within parenthesis.
```

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Creating a sequence of numbers `12,13,14...73` and storing it in object `x`
x <- 12:73

# Determining the length of object `x`
length(x)

# Create a sequence of numbers from 9 to 999, in increments of 9 and determine its length


```

*** =solution
```{r}
# Creating a sequence of numbers `12,13,14...73` and storing it in object `x`
x <- 12:73

# Determining the length of object `x`
length(x)

# Create a sequence of numbers from 9 to 999, in increments of 9 and determine its length
length(seq(99,999,9))
```

*** =sct
```{r}
test_error()
test_output_contains("length(seq(99,999,9))", incorrect_msg = "Check the code again.")
success_msg("Great job! Looks like you`re getting good with sequences!")
```
----


--- type:NormalExercise lang:r xp:100 skills:1 key:c056565056
## 9. Class: Integer and Numeric

To force a number to be recognized as an integer, you need to add the letter L.

Run the sample code to learn about how numeric values defined in different manners have different default class in R.

*** =instructions
Confirm that the class of 999L is integer.

*** =hint
```{r}
Just type class and 999L.
```

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Example: Check several classes. Are they integers or not?
class(a<-1)
class(c(1,3,5))
class(c(1,2.4,3/13))
class(1:5)

# Confirm the class of 999L as an integer

```

*** =solution
```{r}
# Example: Check several classes. Are they integers or not?
class(a<-1)
class(c(1,3,5))
class(c(1,2.4,3/13))
class(1:5)

# Confirm the class of 999L as an integer
class(999L)

```

*** =sct
```{r}
test_error()
test_output_contains("class(999L)", incorrect_msg = "Check the class of `999L` to make sure the L makes it an integer.")
success_msg("Great, now let's move on to one more fun thing in this module.")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:1e7c932a3d
## 10. Coercion

As we mentioned before, it is always good practice to keep track of the class of objects in R. When an element in R does not match the expected class, R usually tries to guess what we mean before throwing an error. That might create confusion or result in undetected mistakes. 

Thus, it never hurts to use coercion functions to make sure the objects are of the right class.

The following commands can be used to coerce values into the respective data types:

- `as.integer()`
- `as.numeric()`
- `as.logical()`
- `as.character()`

*** =instructions
Coerce the `desserts` values into numeric values.

*** =hint


*** =pre_exercise_code
```{r}
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
```

*** =sample_code
```{r}
# Define the `desserts` values
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")

# Coerce it to get a numeric vector for `desserts`


```

*** =solution
```{r}
# Define the `desserts` values
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")

# Coerce it to get a numeric vector for `desserts`
as.numeric(desserts)

```

*** =sct
```{r}
test_error()
test_output_contains("as.numeric(desserts)", incorrect_msg = "Check the code again.")
success_msg("Awesome!Doesn`t that feel wonderful. Now, you can try changing it back to characters, using the code as.character(x)`.")
```
----
