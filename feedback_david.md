# Feedback on Alt3
## Author: David


## General comments for all chapters:
* Spacing between comments: If there is a comment and right below the student enters the answer, I'd leave two lines empty so that once the student has filled in the answer there is still one empty line. Makes the final answer nicely formatted.


## Chapter 1: Intro to R
### General:
* Formatting, space between object name and "<- "
* Lowercase variable names

#### Ex 1:
* Does not accept 55,000,000 and 50,000,000 as values even though that is the number of books sold. Either accept or make clear that the unit is millions of books.
#### Ex 2:
* Error in SCT, couldn't locate source. Did type the right answer.
Ex 4: SCT not flexible enough. Didn't accept the answer `area_g <- 1/2*pi*15^2`. And the solution contradicts the instructions (does not store result in total_area)
Ex 5: Specify `speed`. What unit? Miles per hours?

Chapter 2: Data-types
Does not run at all in my teaching editor. I believe this is because there are no ```{r} ``` tags in the file.
Does the author have the same issue or is this problem localized to my Datacamp?

Chapter 3: Vectors
* Comments in sample_code are all in lowercase. I think beginnings of sentences should be uppercase to make it consistent with other exercises
Ex 1:
* Backticks for code: c() should be `c()`
Ex 2:
* This sentence does not make sense to me: "It's in the same order presented above: 257, 355, 243, 411, 288". Maybe change to "The calories values are: 257, etc"
Ex 3:
* This sentence does not make sense: "We have successfully assigned the temperatures (numeric values) to temp and the city names(character values) to city. But can we associate the temperature to it's related city?". I assume it's referring to a different iteration of the exercise.
* Instructions: "(You can go back to the previous questions and copy the objects stored.)" I think this might be frustrating for some users. Why not just put `desserts <- c("blabla", "bla")` in the sample_code?
* I think the "It would look like this" paragraph on the left-hand side is not necessary, since it's duplicated in the sample_code
Ex 4:
* Make it clear that the `desserts` object was carried over from previous exercise. Maybe add it to the first line of sample_code: `desserts <- c("bla", "blabla")`. Just to make it clear why it's class character.
Ex 5:
* > cost[3:5]
Error: object 'cost' not found
* Instructions are ambiguous. First, I would not use the word "list", since that's a separate class in R, use vector. Second, the instructions sound like the user is supposed to show the first three elements of `desserts`, not `calories`.
Ex 6:
* "In the previous question, we accessed the number of survivors for consequtive animals (1st three)." - This ex. is about food, so I assume it's an error. Also I would write "first" instead of 1st.
* sample_code: Replace the word "list" with vector or character vector
* No space between object name and brackets: `cost [c(1,5)]`
* > cost[c(1,5)]
Error: object 'cost' not found
* "But what if we want to access the number of survivors for any 2 specific animals. " Referring to different iteration and missing quotation mark
* "Isn`t...": Don't use backticks in the "Exercise completed" message, it changes to formatting to R code

Ex 7:
* "Exercise completed" message: Don't use backticks, changes formatting ("Let`s")

Ex 8:
* Instructions: 18 should be 108?
* Unable to enter solution since I get an error in the console: "Error in run_code(dc$get("DC_Solution")) ... etc"


Chapter 4: Sorting
Ex 1:
* Left hand side: "analyse". I think we may want to US spelling ("analyze")
* "We're": Might be to informal? I personally would change to "We are" and stick to no-abbreviations in all exercises
* > library(nmle)
Error: there is no package called 'nmle'
* Variables list (weight, sex etc) is very hard to read, use bullet points?
* Instructions, Missing word: "store it the object"
* sample_code: Why all the code about states and murder rates? I think this may be confusing for some users without explicitly saying that this is a template to follow. Maybe move to left hand side of page?
* Confusing wording: "# Access `weight` from the dataset and store it in `weight`". Maybe change to "Access the `weight` column from the `RatPupWeight` dataset and store it in a new object called `weight`"
* Ambiguous: "Sort the object and save it in the same object". Descending or ascending. Sort by what?
* Accept `min(weight)` as alternative solution

Ex 2:
* Error: there is no package called 'nmle'
* Left hand side is empty except for instructions. Use it to explain how `order` is different from `sort`.
* According to stye guidelines we should not use short object names like this, instead `order` or `weight_order`.
* I think the instructions are *too* helpful. They basically give the answer (`o[1]`)

Ex 3:
* Error in title of exercise? "3. New Codes" Instead should be something about the new command users are learning
* "Write one line of code that gives the index of the lowest population entry". What population data? Refers to different iteration?
*  sample_code: Murders example is confusing (user doesn't know where it comes from and what it has to do with the weight data. And it doesn't run:
> which.min(murders$total)
Error: object 'murders' not found
* The object `weight` is undefined, so one cannot complete this exercise without first defining it. Either make clear in the instructions that user has to define it, or preload it in sample code. The solution uses RatPupWeight$weight, which is confusing since it's different from the previous exercises where we defined a separate object (`weight`)
* Comment is ambiguous: "# Find the smallest value for `weight`". But really, what we are asking for is the *index* of the vector, not the *value*

Ex 4:
* sample_code: "Define variable `treat`". How? The user doesn't know anything about the dataset, needs more detailed instructions
* Not obvious to me why we need a new object for `treat`, but we don't define a new object for `weight` (as we did in previous exercises)
* Instructions are *too* helpful, they directly give the answer: `treat[which.min(RatPupWeight$weight)]`
* > library(nmle)
Error: there is no package called 'nmle'

### Ex 5:
* R example is duplicated in left-hand side and sample_code. Looks a little cluttered. On left hand side each command should be in a new line
* I would copy `treat <- RatPupWeight$Treatment` over from the previous exercises. The instructions don't ask the user to create the treat object, so might be confusing.
* Error: there is no package called 'nmle'

Ex 6:
* Does not run at all, object `o` undefined, error in console.
* Use self-explanatory name for object instead of `o`

Ex 7:
* Add spacing: "7. NA"
* Backticks and no definite article: `na_example` represents...
* `na_example` is actually not loaded into the environment, so this exercise does not run properly

Ex 8:
* Title might be too hard to understand for new R users
* What is the object `ind`? No explanation of what it contains and why it might be partially NA
* Accept alteranative solution: `mean(na_example[!is.na(na_example)])`


## Chapter 5: Vector arithmetics
### Ex 1:
* Left hand side looks cluttered. Add line breaks between code.
* The sample_code is about temperatures, the instructions are about food. Mistake?
* Unclear what to remake? Had to use solution

### Ex 2
* "We've" -> "We have"
* I got the right answer, but it was not accepted as a solution. Here is what I used:
x <- 1:2500
sum(1/(x^3))
* Solution, formatting: No space between sum and parantheses `sum (1/ x^3)`

Ex 3:
* In sample code, preload `murders` dataset and explain it's columns on the left hand side. Too little context to understand the instructions
* Use `dslabs` package
* Instruction is ambiguous, it asks for the average murder rate in the US.  That number would be ```sum(murders$total$)/sum(murders$population$```.  But what the question really is asking for is to calculate a weighted mean, with weight=1 for each state.


## Chapter 6: Indexing
### Ex. 1:
* "We’re using the same dataset as we did in the chapter on Sorting - women." - I don't thin this dataset was used in this iteration?
* Conflicting instructions and sample_code... One refers to trees, one to women
* Instructions: Why does it say "lower than its mean of 2?" The mean of the data is not 2, it's approximately 2.098. Change to just "lower than 2".
