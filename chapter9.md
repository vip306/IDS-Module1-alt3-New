---
title       : 9. Programming Basics
description : 

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ba015a0cbd
## 1. Conditional expressions

What will this conditional expression return?
Run it from the console.

```{r}
x <- c(1,2,-3,4)
if(all(x>0 & x<10)){
  print("All between 0 and 10 (non-inclusive)")
}else{
  print("Some are out of range")
}
```

*** =instructions
- All between 0 and 10 (non-inclusive)
- Some are out of range
- N/A
- None of the above

*** =hint
Are all the numbers stored in `x` between 0 and 10?

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Look at the values again."
msg2 = "Awesome! That is correct."
msg3 = "Check the question again."
msg4 = "Check the values in x once more."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3,msg4))
```







--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:3641a0ea21
## 2. Logical operators

Which of the following expressions is always `TRUE` when at least one entry of a logical vector x is `FALSE`?


*** =instructions
- all(x)
- any(x)
- any(!x)
- all(!x)

*** =hint

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Check the question again. Try an example on the R console."
msg2 = "Re-read the question! Try an example on the R console."
msg3 = "Good job! Let's move to the next question.”
msg4 = "Try again!Try an example on the R console."
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3,msg4))
```







--- type:NormalExercise lang:r xp:100 skills:1 key:9e33032243
## 3. More conditional expressions

The function `tolower()` changes all your characters to lower case, for example:

```{r}
state_lower <- tolower(murders$state)
state_lower[1:5]
```
*** =instructions

Write one line of code using `ifesle` that assigns to the object `new_names` the lower case state name when the state name begins with "M" or a letter that comes after "M" in the alphabet. When the state name begins with a letter before "M", keep the state name.

*** =hint
R uses arithmetic operators (>, <, ==, etc.) to compare the order of characters in the alphabet. Play with it in the R console!

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
```

*** =sample_code
```{r}
# Create new_names using ifelse()

# Append new_names to murders

```

*** =solution
```{r}
# Create new_names using ifelse()
new_names <- ifelse(murders$state>"M", tolower(murders$state), murders$state)

# Append new_names to murders as a new column
murders<-cbind(murders, new_names)
```

*** =sct
```{r}
test_object("new_names", undefined_msg = "Make sure you define `new_names`!")
test_function("ifelse", args = c("test", "yes", “no"), incorrect_msg = "It has to be one line of code. Combine `tolower()` and `ifelse()`.”)
test_object(“murders”, incorrect_message = “Make sure you use `cbind` to append `new_names` to `murders`!”)
test_error()
success_msg("Whoohoo! You're becoming a pro at this!")
```






--- type:NormalExercise lang:r xp:100 skills:1 key:8232e54e7b

## 4. Write your own functions

You will encounter situations where the function you need has not been defined in R, but luckily you can write your own function. Let's practice writing a function in R. The functions you define can have multiple arguments as well as default values.

*** =instructions
Create a function `max_total` that takes `murders` as the argument and tells you which state has the most gun murders. Remember to use built-in function `max`.

*** =hint
Use `$` and `[]` on `murders` in the body of your function to determine which state has the most gun murders.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
```

*** =sample_code
```{r}
# Create function max_total


# Find out the state with the most murders in the murders data set


```

*** =solution
```{r}
# Create function max_total
max_total<-function(x){x[x$total==max(x$total),]$state}

# Find out the state with the most murders in the murders data set
max_total(murders)
```

*** =sct
```{r}
test_error()
test_function_definition("max_total",
                        function_test = {
                        test_expression_result("max_total(murders)")
                        },
                        body_test = {
                        test_function("max")
                        })
test_output_contains("max_total(murders)")
success_msg("This is awesome! You just wrote a function in R!")
```






--- type:NormalExercise lang:r xp:100 skills:1 key:eb931680e3

## 5. Write your own functions continued

The functions you define can have multiple arguments as well as default values. Now try write a more complicated function to get information about `murders`.  

*** =instructions
Create a function `nplus_states` that takes `murders` as an argument and for any given `n`, prints the name of the states that have more than `n` gun murders. Set the default value of `n` to be 100.

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
```

*** =sample_code
```{r}
# Create function nplus_states


# Find out the states in the Western region that have more than 100 gun murders

```

*** =solution
```{r}
# Create function dangerous_states
nplus_states<-function(x, n=100){x[x$total>n,]$state}

# Find out the states that have more than 100 gun murders
nplus_states(murders)
```

*** =sct
```{r}
test_error()
test_function_definition("nplus_states",
                        function_test = {
                        test_expression_result("nplus_states(murders)")
		  test_expression_result("nplus_states(murders, 1000)")
                        })
test_output_contains("rate_per_n(murders)")
success_msg("This is awesome! You can write much cooler functions now!")
```




--- type:NormalExercise lang:r xp:100 skills:1 key:6544013f7c

## 6. Function environment

Keep in mind that variables defined in a function only hold within the function environment and does not affect the value of the variable anywhere else.

*** =instructions

After running the code below, what are the values of `x` and `y`?

```{r}
x <- 3
y <- 1
func1 <- function(x, y=2){
		y+x
		}
func2 <- function(x){
		x<-5
		func1(x)}
func2(1)
```

*** =hint

Try to answer the question before running the code in the R console!

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
#Assign the right value to x and y

```

*** =solution
```{r}
#Assign the right value to x
x<-7
y<-1

```

*** =sct
```{r}
test_error()
test_object("x", incorrect_msg = "The default value of a variable is only valid within the scope of the function!")
test_object("y", incorrect_msg = "Be mindful where `y` is called!")
success_msg("Good job!")
```




--- type:NormalExercise lang:r xp:100 skills:1 key:75bc32926c

## 7. Define a variable within your function

Recall from an earlier exercise that we wrote a function to find out the state with the most gun murders. Let’s now find out the state with the highest gun murder rate.

When you start writing more complicated functions, you’ll find breaking down the steps and creating new variables along the way to be very helpful. And don’t worry about messing up your working environment because all variables defined within a function are only valid when the function is being called!

*** =instructions
Create a function `max_rate` that takes `murders` as the argument and tells you which state has the highest murder rate.

*** =hint
Create a new variable `murder_rate` and append it to the `murders` data set so you can use its values in the conditional expression.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
```

*** =sample_code
```{r}
# Create function max_rate


# Find out the state with the highest murder rate


```

*** =solution
```{r}
# Create function max_rate
max_rate<-function(x){x$murder_rate<-x$total/x$population
			    max_murder_rate<-max(x$murder_rate)
                                    row_max_rate<-x[x$murder_rate==max_murder_rate,]
                                    row_max_rate$state}

# Find out the state with the highest murder rate
max_rate(murders)

```

*** =sct
```{r}
test_error()
test_function_definition("max_rate",
                        function_test = {
                        test_expression_result("max_rate(murders)")
                        },
                        body_test = {
                        test_function("max")
                        })
success_msg("This is awesome! You can write much cooler functions now!")
```





--- type:NormalExercise lang:r xp:100 skills:1 key:340b9eba39
## 8. Control flow statement: for loop

Recall that in an earlier exercise, you changed the names of states that begins with an "M" or a letter that comes after "M" to lower case using the `ifelse()` function. Now do the same with an `if()` statement and a for loop.  

*** =instructions

Use an `if()` statement and a for loop to assign to the object `new_names2` the lower case state name when the state name starts with "M" or a letter that comes after "M" in the alphabet. When the state name starts with a letter before "M", keep the state name.

*** =hint
Use `i in 1:nrow(murders)` to loop through all rows of the data frame.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
```

*** =sample_code
```{r}
# Create new_names2 using if() for for()

# Print new_names2

```

*** =solution
```{r}
# Create new_names2 using if() for for()
new_names2<- vector()
for(i in 1:nrow(murders)){
  if(murders$state[i]>="M"){
      new_names2[i] <- tolower(murders$state[i])
  }else{
      new_names2[i] <- murders$state[i]
    }
  }

# Print new_names2
print(new_names2)

```

*** =sct
```{r}
test_for_loop(cond_test = test_student_typed("in 1:nrow(murders)”, not_typed_msg = "You can use `(i in 1:nrow(murders))` to define your for loop."),
                expr_test = test_function("tolower"),
                not_found_msg = "Make sure to code a for loop in the first place!”)
test_output_contains("print(new_names2)")
test_error()
success_msg("Whoohoo! You're becoming a pro at this!")
```






--- type:NormalExercise lang:r xp:100 skills:1 key:cb64a8f82d

## 9. Check matching of values

*** =instructions
Confirm that the result of the for loop in the last exercise (`new_names2`) is identical to the result of the `ifelse()` function in exercise 3 (new_names). Both values are pre-loaded into your environment.

*** =hint

Do not miss any `*` and `()` when writing code for the formula `n*(n+1)*(2*n+1)/6`.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))

new_names2<- vector()
for(i in 1:nrow(murders)){
  if(murders$state[i]>="M"){
      new_names2[i] <- tolower(murders$state[i])
  }else{
      new_names2[i] <- murders$state[i]
    }
  }

new_names <- ifelse(murders$state>"M", tolower(murders$state), murders$state)
```

*** =sample_code
```{r}
# Compare new_names and new_names2 using identical()

```

*** =solution
```{r}
# Compare new_names and new_names2 using identical()
identical(new_names, new_names2)

```

*** =sct
```{r}
test_output_contains("identical(new_names, new_names2)", incorrect_msg = "Check that you used `identical()` correctly!")
test_error()
success_msg("This is great! Let’s go to the last question of this module!")
```





--- type:NormalExercise lang:r xp:100 skills:1,3 key:81431dc1d4

## 10. For loops and plots

Now let’s plot some graphs!  

*** =instructions
Write a function `dangerous` that defines and plots two vectors `x`  and `y`, where `x` is the population and `y` the total number of murders of all the states with murder rate of greater than `n` per 100,000 people.

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
```

*** =sample_code
```{r}
#  Create the function


# Create the plot when n=5

```

*** =solution
```{r}
#  Create the function
dangerous<-function(data, n){
	x <- vector()
	y <- vector()
	data$rate <- data$total/data$population*100000
	for(i in 1:nrow(data)){
		if(data$rate[i] > n){
			x <- append(x, data$population[i])
			y <- append(y, data$total[i])
		}
	}
	plot(x, y)
}


# Create the plot when n=3
dangerous(murders, 3)

```

*** =sct
```{r}
test_error()
test_function_definition("dangerous",
                        function_test = {
                        test_expression_result("dangerous(murders, 3)")
                        test_expression_result(“dangerous(murders, 5)")
                        },
                        body_test = {
                        test_function("plot")
                        })
success_msg("Awesome! Let's go to the last exercise in this chapter!")
```
