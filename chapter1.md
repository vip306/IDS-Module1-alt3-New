---
title       : Just some title to make this work in Datacamp
description :

--- type:NormalExercise lang:r xp:100 skills:1 key:bf96ea1498
## 1. Assigning Values and Arithmetic Functions

We’re practicing adding numbers stored in objects in this question. You can add the numbers directly. We want you to practice storing values to variables as you’ll need it for everything in the future!

*** =instructions
Calculate the combined sale of the 2 books, if Harry Potter and the Goblet of Fire(part 4) sold $55 million$ copies and Harry Potter and the Deathly Hallows(part 7) sold $50 million$ copies.

*** =hint

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Assign/ Store values in variables
drinks <- 200
fries <- 100

# Assign values (number of copies sold) to HP4 and HP7


# How much was the total food sale?
drinks + fries

# Total number of copies sold?
```

*** =solution
```{r}
# Assign values (number of copies sold) to HP4 and HP7
HP4<- 55
HP7<- 50

# Total number of copies sold?
HP4 + HP7
```

*** =sct
```{r}
test_error()
test_object("HP4", undefined_msg = "", incorrect_msg = "")
test_object("HP7", undefined_msg = "", incorrect_msg = "")
test_output_contains("HP4 + HP7", incorrect_msg = "")
success_msg("Great job! Isn’t it crazy, how many copies of HP books were sold !")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:1e3753c95a
## 2. Less than, Greater than, Equal to

We can use the lesser than and greater than operators, to determine if the values are lesser, greater or equal to one another. When we print a value in R, it tells us if our operation is true or false. For example, typing `5>5`, would yield the result `FALSE` and typing `6>5`, would yield `TRUE`.
Remember, in R, to say that `5 is equal to 5`, we need to type `5==5`. The double equal to sign indicates that 5 is equal to 5.

*** =instructions
Determine the outcome of the Quidditch match if at the beginning, Gryffindor scored 15 points and Hufflepuff, their opponent, scored 165 points. At the last moment, Harry from Gryffindor caught the Snitch for 150 points.

*** =hint
Which number is lesser than, greater than or equal to the other?


*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Assign total scores to `Gryffindor` and `Hufflepuff`

# Check and determine the outcome of the match using the correct operator

```

*** =solution
```{r}
# Assign total scores to `Gryffindor` and `Hufflepuff`
Gryffindor <- 15 + 150
Hufflepuff <- 165

# Check and determine the outcome of the match using the correct operator
Gryffindor == Hufflepuff
```

*** =sct
```{r}
test_error()
test_object("Gryffindor", undefined_msg = "", incorrect_msg = "")
test_object("Hufflepuff", undefined_msg = "", incorrect_msg = "")
test_output_contains("Gryffindor == Hufflepuff", incorrect_msg = "")
success_msg("Yes! It was a draw!")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:6d8c3c5f06
## 3. Logs
R in its use as a calculator, helps us calculate logs. Look at an example in the console on the right window.

*** =instructions
Lord Voldemort has 7 horcruxes and each of them could be hidden in 4 different spots.
Find the log, to the base 2, of the number if you double the total number of possible spots.


*** =hint
`total_spots <- 7*4`

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Calculate the square root of x = 25
sqrt(25)

# Calculate the log of (sqrt of 25) to the base 10
log10(sqrt(25))
# same as `log(25, base = 10)`

# Calculate the total number of possible spots, and store in ‘total_spots’

# Calculate the log of double the total_spots, to the base 2
```

*** =solution
```{r}
# Calculate the total number of possible spots, and store in ‘total_spots’
total_spots<- 7*4

# Calculate the log of double the total_spots, to the base 2
log2(total_spots*2)
```

*** =sct
```{r}
test_error()
test_object("total_spots", undefined_msg = "", incorrect_msg = "")
test_function("log", incorrect_msg = "")
success_msg("That was great! You’re doing really well !")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:da368a277f
## 4. Calculations
Let’s use R to calculate the area of Hagrid’s house and grounds.
`Area of rectangle = length * width`
`Area of a semi-circle: ½*pi*r^2 (pi = 3.14)`

*** =instructions

Calculate the total area of Hagrid’s house and grounds, if the length of his house = 40 feet, width = 30 feet.
And the radius of the semi-circular ground is 15 feet.

*** =hint
 Use the formula for area of rectangle + area of semi-circle.

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Calculate the area of the house and store it in `area_h`

# Calculate the area of the grounds and store it in `area_g`

# Calculate the total area combining the house and grounds and store it in `total_area`
```

*** =solution
```{r}
# Calculate the area of the house and store it in `area_h`
area_h<- 40*30
# Calculate the area of the grounds and store it in `area_g`
area_g<-(3.14*(15^2))/2
# Calculate the total area combining the house and grounds and store it in `total_area`
area_h + area_g
```

*** =sct
```{r}
test_error()
test_object("area_h", undefined_msg = "", incorrect_msg = "")
test_object("area_g", undefined_msg = "", incorrect_msg = "")
test_output_contains("area_h + area_g", incorrect_msg = "")
success_msg("Awesome job!")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:4d6f2e8e26
## 5. Calculating Distance, Speed and Time


*** =instructions
Calculate the average speed of the Hogwarts Express train from London to Hogwarts, if it  travels 200 miles and takes 4 hours.

*** =hint
Formula for speed = distance/ time

*** =pre_exercise_code
```{r}
#no pec
```

*** =sample_code
```{r}
# Store the distance travelled  in `distance`and time taken in `time`

# Calculate the average speed and store it in `avg_speed`

# Remember that R doesn’t automatically print any output; so print the average speed
```

*** =solution
```{r}
# Store the distance travelled  in `distance`and time taken in `time`
distance<-200
time <- 4

# Calculate the average speed and store it in `avg_speed`
avg_speed<- distance/time

# Remember that R doesn’t automatically print any output; so print the average speed
avg_speed
```

*** =sct
```{r}
test_error()
test_object("distance", undefined_msg = "", incorrect_msg = "")
test_object("time", undefined_msg = "", incorrect_msg = "")
test_object("avg_speed", undefined_msg = "", incorrect_msg = "")
test_output_contains("avg_speed", incorrect_msg = "")
success_msg("That’s great! You’re getting really good at this!")
```
----
