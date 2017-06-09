---
title       : 8. Basic Plots
description :

--- type:NormalExercise lang:r xp:100 skills:1 key:4c6d0d3bc3
## 1. Scatterplot

In this chapter we practice using basic plotting tools in R. 

We’re using the same dataset as we did in the chapter on `Sorting` - `RatPupWeight`.

*** =instructions
- Store the value of the rats' weights in `weight`, and the number of pups per litter in `lsize`.
- Create a scatterplot of the weights of the ratpups with the size of the litter they were born in.  

*** =hint

*** =pre_exercise_code
```{r}
library(nlme)
data(RatPupWeight)
```

*** =sample_code
```{r}
# Load the datasets
library(nmle)
data(RatPupWeight)

# Store the values of `weight` and `lsize`



# Create a scatterplot with `weight` and `lsize`

```

*** =solution
```{r}
# Store the values of `weight` and `lsize`
weight <- RatPupWeight$weight
lsize <- RatPupWeight$Lsize

# Create a scatterplot with `weight` and `lsize`
plot(weight, lsize)
```

*** =sct
```{r}
test_error()
test_object("weight", undefined_msg = "Define weight first.", incorrect_msg = "Store the value of weight.")
test_object("lsize", undefined_msg = "Define lsize first.", incorrect_msg = "Store the lsize.")
test_function("plot", incorrect_msg = "Scatter weight on lsize.")
success_msg("Doesn't that plot look neat!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:4c598008e7
## 2. Histogram


*** =instructions
Create a histogram of the weights of the rat pups.

*** =hint
```{r}

```

*** =pre_exercise_code
```{r}
library(nmle)
data(RatPupWeight)
```

*** =sample_code
```{r}
# Load the datasets
library(nmle)
data(RatPupWeight)

# Store the value of `weight` (same as previous question)

# Create a histogram of the weight

```

*** =solution
```{r}
# Store the value of `weight` (same as previous question)
weight <- RatPupWeight$weight

# Create a histogram of the weight
hist(weight)
```

*** =sct
```{r}
test_error()
test_object("weight", undefined_msg = "Define weight first.", incorrect_msg = "Check code!")
test_function("hist", incorrect_msg = "Check code again.")
success_msg("We got a histogram! Awesome!")
```
----

--- type:NormalExercise lang:r xp:100 skills:1 key:126ec89fd8
## 3. Boxplot


*** =instructions
Generate boxplots of the weights of the pups by sex (`weight~sex`), using one line of code.  

*** =hint
```{r}
Make sure you specify the dataset.
```

*** =pre_exercise_code
```{r}
# Load the datasets
library(nmle)
data(RatPupWeight)
```

*** =sample_code
```{r}
# Store values as in previous questions
weight<-
sex <-

# Create a boxplot of weight by sex and specify the dataset

```

*** =solution
```{r}
# Create a boxplot of weight by sex and specify the dataset
boxplot(weight~sex, dataset = RatPupWeight)

```

*** =sct
```{r}
test_error()
test_function("boxplot", incorrect_msg = "Check code. use ~ sign and include dataset.")
success_msg("Great job! Now you've learnt all three basic types of plots in R!")
```
----
