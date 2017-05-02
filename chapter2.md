title : Data-types author_field : description : In this course we introduce you the basics of computing and analyzing data in the 
user-friendly and helpful R interface. This chapter introduce to you different data types and how to work with them in R. author_bio : 
Bo W. is a TA for this course. university : Brown University difficulty level : 1 
time needed : Approximately 1 hour for each module programming language : R 

--- type:NormalExercise lang:r xp:100 skills:1,3 key:b0bd1a7eb3

1. Take a first look at your data set

In this series of exercises, we examine the murders data set (already loaded in your working environment) to learn about data types in R.

*** =instructions Use the str() function to check the structure of the murders data set.

*** =hint murders is now an R object and therefore does not need the quotations marks to be referred to.

*** =pre_exercise_code

load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
*** =sample_code

# Use the str() function to check the structure of murders

*** =solution

# Use the str() function to check the structure of murders
str(murders)
*** =sct

test_output_contains("str(murders)",
            incorrect_msg = "Make sure you spell `murders` correctly!")
test_error()
success_msg("Good job! Head over to the next exercise.")
--- type:NormalExercise lang:r xp:100 skills:1,3 key:8f0ed4ae4f

2. Take a first look at your data set (continued)

Now look at the last few rows of the murders data set.

*** =instructions Use the tail() function to check the last six rows of murders.

*** =hint You can change how many rows you want to see by adding a second argument to the tail() function, e.g. tail(murders, 10).

*** =pre_exercise_code

load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
*** =sample_code

# Use the tail() function to look at the last rows of murders

*** =solution

# Use the tail() function to look at the last rows of murders
tail(murders)
*** =sct

test_output_contains("tail(murders)",
            incorrect_msg = "Make sure you spell `murders` correctly!")
test_error()
success_msg("Good job! Head over to the next exercise.")
--- type:NormalExercise lang:r xp:100 skills:1,3 key:d6e46d357d

3. Check data type

Next check the data types of all the five variables in murders.

*** =instructions Use the class() function to find the data types of each variable in murders.

*** =hint You can use names() to obtain the names of all variables in murders.

*** =pre_exercise_code

load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
*** =sample_code

# Use class() to find out data types of each variable in murders

*** =solution

# Use class() to find out data types of each variable in murders
class(murders$region)
class(murders$state)
class(murders$populaiton)
class(murders$abb)
class(murders$total)
*** =sct

test_output_contains(c("class(murders$region)", "class(murders$state)", "class(murders$population)",
                       "class(murders$region)", "class(murders$region)"), 
                       incorrect_msg = "Make sure you check all five variables!")
success_msg("That was great! Now you know the data types of all variables in your data set!")  
test_error()
--- type:NormalExercise lang:r xp:100 skills:1,3 key:d6e46d357d

4. Factors

In the last exercise you found out that the type of the region variable is "factor". Now let’s take a closer look at this type of data.

*** =instructions Use the function nlevels() to check how many levels are there in the variable region.

*** =hint Use $ to access a variable in a data set.

*** =pre_exercise_code

load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_3073/datasets/murders.rda"))
*** =sample_code

# Use nlevels() to find out the number of levels in region 

*** =solution

# Use nlevels() to find out the number of levels in x
nlevels(murders$region)
*** =sct

test_output_contains("nlevels(murders$region)", incorrect_msg="Make sure you spell `nlevels()` correctly!")
success_msg("That was great! Let’s head over to the next exercise!")  
test_error()
--- type:NormalExercise lang:r xp:100 skills:1,3 key:d6e46d357d

5. Lists in R

Remember data sets are stored as data frames, and are essentially lists in R. Now let’s create a list.

*** =instructions Create a list consisting three objects: a vector c(2,5,3), a numeric value $21.3$ and a function sin. Name this list list1. Print the list1.

*** =hint Use list() to create a list.

*** =pre_exercise_code

#no pec
*** =sample_code

# Create list1, which includes three objects: a vector c(2,5,3), a numeric value 21.3, and a function sin


# Print list1

*** =solution

# Create list1, which includes three objects: a vector c(2,5,3), a numeric value 21.3, and a function sin
list1<-list(c(2,5,3), 21.3, sin)

# Print list1
print(list1)
*** =sct

test_object("list1", undefined_msg = "Make sure you define the variable!", incorrect_msg = "Check out your code again!")
test_output_contains("print(list1)", incorrect_msg = "")
success_msg("That was great! You are done with the chapter!")  
test_error()