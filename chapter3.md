--- type:NormalExercise lang:r xp:100 skills:1 key:ddf0db0f7d

## 1. Creating a character vector
Vectors are one-dimension arrays that can hold numeric data, character data, or logical data. In other words, a vector is a simple tool to store data.
In R, you create a vector with the combine function c(). The character vectors have to be written as strings and so the names are enclosed within double inverted commas. 

A character vector would look something like this:
`food <- c("pizza", "burgers", "salads", "cheese", "pasta")`

*** =instructions


Create a character vector containing the names of these yummy desserts, called `desserts`, including  `cheesecake, chocolate_mousse, brownie, apple_pie, pudding`, using the function c. 

*** =hint
Be sure to place the names within double inverted commas. 

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# create a character vector to store the different types of food items and assign it to `food`
food <- c("pizza", "burgers", "salads", "cheese", "pasta")

# create a character vector to store the names of 5 desserts and assign it to `desserts`

```

*** =solution
```{r}
# create a character vector to store the names of 5 desserts and assign it to `desserts`
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
```

*** =sct
```{r}
test_error()
test_object("desserts", incorrect_msg = "Each of the dessert names need inverted commas.")
success_msg("Good job! Do you want to now try creating a numeric vector!?")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:5e66879c2c

## 2. Numeric Vectors  

As in the previous question, we are going to create a vector. Only this time, let's learn to create a numeric vector. The main difference is that you place the vector elements separated by a comma between the parentheses and they don't need inverted commas. 

For example a numeric vector would look something like this: 
`cost <- c(50, 75, 90, 100, 150)`

*** =instructions
Create a numeric vector with the calories of the desserts from question 1. It's in the same order presented above: 257, 355, 243, 411, 288. Store the numbers in object `calories`.

*** =hint
Make sure your numbers are within parenthesis and have commas separating them. 

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# create a numeric vector to store the cost of different food items and assign it to `cost`
cost <- c(50, 75, 90, 100, 150)

# create a numeric vector to store the calories of the desserts and assign it to `calories`

```

*** =solution
```{r}
# create a numeric vector to store the calories of the desserts and assign it to `calories`

calories <- c(257, 355, 243, 411, 288)

```

*** =sct
```{r}
test_error()
test_object("calories", incorrect_msg = "Check to match the numbers from the question!")
success_msg("Awesome! Now you`ve learnt to store both numeric and character vectors!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:c0b17dfdc7
## 3. Connecting Numeric and Character Vectors 

We have successfully assigned the temperatures (numeric values) to `temp` and the city names(character values) to `city`. But can we associate the temperature to it's related city? Yes! We can do so using a code we already know - `names`. We assign names to the numeric values.  

It would look like this:
`cost <- c(50, 75, 90, 100, 150)`
`food <- c("pizza", "burgers", "salads", "cheese", "pasta")`
`names(cost) <- food` 

*** =instructions
Use the "names" function and the objects defined in the previous exercises to associate the dessert with its corresponding calorie count.
(You can go back to the previous questions and copy the objects stored.)

*** =hint
```{r}
Assign names to the numeric values. 
```

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Associate the cost values with its corresponding food item
cost <- c(50, 75, 90, 100, 150)
food <- c("pizza", "burgers", "salads", "cheese", "pasta")
names(cost) <- food

# Remember, R just stores the values in the object and doesn't display unless asked. To display, just type the name of the object
cost

# Associate the dessert with the calories using the `names` function 
desserts <- 
calories <- 

```

*** =solution
```{r}
# Associate the dessert with the calories using the `names` function 
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
names(calories) <- desserts
```

*** =sct
```{r}
test_error()
test_object("desserts", incorrect_msg = "Check to match the numbers from the question!")
test_object("calories", incorrect_msg = "Each of the city names need inverted commas.")
test_function("names", incorrect_msg = "The numeric vector should be in the parenthesis.") 
success_msg("Great job! We now know the number of calories for these desserts!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:7c4dfa097b
## 4. Class 

In R, we can determine the class of an object we've created using the `class` command. It can be an integer, or just numeric or a character. 

*** =instructions
Determine the class of the vector `desserts`. 

*** =hint

*** =pre_exercise_code
```{r}
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
```

*** =sample_code
```{r}
# Determine the class of `desserts` 

```

*** =solution
```{r}
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
## 5. Using Operators

If we want to display only selected values from the object, R can help us do that easily. 

For example, if we want to see the cost of the last 3 items in our food list, we would type:
`cost[3:5]`

Note here, that we could also type `cost [c(3,4,5)]` and get the same result. The `:` operator helps us condense the code and get consecutive values. 


*** =instructions

Use the [ and : operators to access the calories of the first 3 desserts in the list of `desserts`. 

*** =hint
Square brackets and : are the important bits in this.

*** =pre_exercise_code
```{r}
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
names(calories) <- desserts
```

*** =sample_code
```{r}
# cost of the last 3 items in our food list
cost[3:5]

# Calories of the first 3 desserts 
```

*** =solution
```{r}
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
## 6. Using Operators continued...

In the previous question, we accessed the number of survivors for consequtive animals (1st three). But what if we want to access the number of survivors for any 2 specific animals. Well, let's see how we can do that in R! 

An example:
To access the cost of `pizza` (1st) and `pasta` (5th food item) in our list, the code would be:
`cost [c(1,5)]` 


*** =instructions
Use the [ operator to access the calories of the `chocolate_mousse`(2nd) and `brownie`(3rd). 


*** =hint


*** =pre_exercise_code
```{r}
desserts <- c("cheesecake", "chocolate_mousse", "brownie", "apple_pie", "pudding")
calories <- c(257, 355, 243, 411, 288)
names(calories) <- desserts

```

*** =sample_code
```{r}
# Access the cost of pizza and pasta from our food list 
cost [c(1,5)]

# Access the calories for chocolate mousse and brownie 

```

*** =solution
```{r}

# Access the calories for chocolate mousse and brownie 
calories[c(2,3)]

```

*** =sct
```{r}
test_error()
test_output_contains("calories[c(2,3)]", incorrect_msg = "You need to use `c` and parenthesis inside the square brackets.")
success_msg("Isn`t that awesome! Let`s move to the next exercise!")
```
----



--- type:NormalExercise lang:r xp:100 skills:1 key:02d64318c8
## 7. Sequences 

We can also create different types of sequences in R. 
For example, in `seq (7, 49, 7)`, the first argument defines the start, and the second the end. 
The default is to go up in increments of 1, but a third argument let's us tell it how much to jump by.

*** =instructions
Create a vector containing all the positive odd numbers smaller than 1000.

*** =hint
```{r}
If you start at 1 and jump by 2, you`ll get the positive even numbers. 
```
*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Create a vector with the multiples of 7, smaller than 50. 
seq(7, 49, 7) 

# Create a vector containing all the positive odd numbers smaller than 100.

```
*** =solution
```{r}
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
## 8. Sequences and length  

We're going to now use the `seq` from the previous question and add in the `length` command. 
The `seq` command will generate the sequence and the `length` command will tell you how many numbers the list has. 

*** =instructions
Create a vector of numbers that start at 99 and don’t exceed 999, in increments of 9: 99, 18,...999
How many numbers does the list have? 
Use only one line of code to answer both questions.

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
# Create a sequence of numbers from 9 to 999, in increments of 9 and determine its length
length(seq(99,999,9)
```

*** =sct
```{r}
test_error()
test_output_contains("length(seq(99,999,9)", incorrect_msg = "Check the code again.")
success_msg("Great job! Looks like you`re getting good with sequences!")
```
----


--- type:NormalExercise lang:r xp:100 skills:1 key:c056565056
## 9. Class, Integers and Numerics

Note that if you run the class of `class(a<-1)` it shows up as numeric and not integer. 
R defaults to numeric and to force a number to be recognized as an integer, you need to add the letter L.

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
# Check the class of `1`, assigned to the object `a`
class(a<-1)

# Confirm the class of 999L as an integer

```

*** =solution
```{r}
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

The concept of coercion is a very important one. Watching the video, we learnt that when an entry does not match the expected, R tries to guess what we meant before throwing an errors. That might get confusing at times. 

As we've discussed in earlier questions, there are numbers and character vectors. The character vectors are placed within inverted commas, and the numeric aren't. 

We can coerce R into changing characters to integers and vice-versa. The code, `as.integer(x)` and `as.character(x)` help us do this. 
Let's practice doing it!

*** =instructions
Coerce the `desserts` values into numeric values, using "as.integer". 

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
# Coerce it to get a numeric vector for `desserts`
as.integer(desserts)

```

*** =sct
```{r}
test_error()
test_output_contains("as.integer(desserts)", incorrect_msg = "Check the code again.")
success_msg("Awesome!Doesn`t that feel wonderful. Now, you can try changing it back to characters, using the code as.character(x)`.")
```
----

