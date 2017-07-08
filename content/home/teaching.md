+++
# An example of using the custom widget to create your own homepage section.
# To create more sections, duplicate this file and edit the values below as desired.

date = "2016-04-20T00:00:00"
draft = false

title = "Teaching"
subtitle = ""
widget = "custom"

# Order that this section will appear in.
weight = 60

+++
I  taught an intersession course on R programming at Johns Hopkins. Here are my class notes:


Let’s first start Rstudio. This is a good GUI that helps you organize the R expressions(functions called with some arguments)  you run, the plots and outputs as a result of those commands.
 
We have four panes. The upper left is the R script file editor, where you will enter your commands and save them as a text file. The lower left is the R console where you will see the commands sent to R and the results of those expressions. The results of expressions can be stored in variables to be used in future expressions. The upper right shows the variables and the data stored in those variables. The lower right pane has Files,Plots,Packages,Help tabs.
-Files will list  the files in the current working directory in your computer’s file system
-Plots  will show you any plots you have asked R to draw.
-Help  is where you can see information about R functions
-Packages:  we don’t need to worry about now
 
We’ll use R to read, modify and analyze data. Let’s start entering some R expressions and see the results. 
 
 
# How to store data in R
The most basic way  one can think of   to organize numeric data  is a vector. Let’s create a vector whose elements are numbers by concatenating a few of them. We’ll call  “c” function with the numbers as  arguments to the function.
```r 
#creating a numeric vector
a.vector <- c(2,4,5)
```
If we need a sequence of integers, we can use double colon operator between the starting integer and ending integer
```r 
another.vector <- 2:6
```
We can concatenate different vectors to get new vectors.
a.brand.new.vector <-c(a.vector,another.vector)
 
For any sequence with regular increments, “seq” is the function to use. It has three arguments  the first number , the last number and the interval
```r 
a.seq.of.numbers <- seq(0,1,0.01)
``` 
If we need to store data as a two-dimensional  array , we use “array” function (with number of rows and columns)
```r 
an.array <- array(a.seq.of.numbers,dim=c(10,10))
```

In the “array” function, we make use of the “dim” argument which is a vector of length two(number of rows and number of columns). Note that the functions we call might have possible arguments that we don’t provide.  R will assume the values of those arguments are the default values, which you can look up in the help document for that function.
To do that, enter
```r 
?array   
```
We usually won’t need to look up all these arguments, though, since the default values are sensible.
 
```r 
day.number <- 1:7
```
What is the size of the vector?
```r 
length(day.number)
```
Suppose the data is not numeric, but is composed of strings(any combination of characters words, sentences, etc.)  ( Qualitative data for example). We can store multiple strings in a vector like numbers. We call such vectors “character vectors”. We let R know we’re  dealing with characters by putting quotes around them. 
 
 
```r  
#Creating a character vector
 
#We can store qualitative data as vectors, too. (2.1.1)
day.names <- c("Mon","Tue","Wed","Thu","Fri")
```
During analysis of data, one often needs to modify some portion of a vector. we use square brackets after the name of the vector and inside the brackets  we enter a vector of indices.  The elements are indexed starting from 1  so if we want to get the first three elements of “day.names”
 
```r 
# If we want to use only part of a vector, we use indexing to choose
# which elements want
#Numeric indexing
day.names[1:3]
```
If we want to get the elements  with indices 2,4,5 (the numbers  we had stored in a.vector
```r 
day.names[a.vector]
```
When we need to access some portion of the two-dimensional array we created
```r 
an.array[1:4,1:3]
```
If we want to edit some elements of vectors and arrays, we can edit them in RStudio.
If you’re using Rgui, we can use edit function to open up a spreadsheet interface
```r
edit(an.array)
```
 
 
 
 
An array is a two-dimensional array of numbers or strings. But data can be a combination of different kinds of variables. The traditional convention of data organization in spreadsheet format is  columns corresponding to different variables or features (qualitative or quantitative)  being studied  and rows corresponding to different observations of those variables. 
We will use data frames in R to store data organized like this. A data frame in R is a collection of vectors that all have the same length, but can  be of any type (numeric vector, character vector). Each vector forms one column of the data frame. Many datasets that you load into R will be stored in data frames.
```r 
# data.frames in R
```
Let’s create a data.frame that is composed of the name of days and the integer corresponding to that day. “data.frame” function creates a data frame with each supplied argument as one of the columns. Columns can also be named, the names of the columns are supplied when creating the data frame. In the following example, these are “number” and “names” respectively 
```r 
#creating a data.frame (many datasets will be in this form)
a.data.frame <- data.frame(number=day.number,names=day.names)
```
This R expression caused an error, because we didn’t have vectors that have the same length. 
Let’s fix this
```r 
day.names <- c(day.names,"Sat","Sun")
 
a.data.frame <- data.frame(number=day.number,names=day.names)
```
The indexing for data.frames is like  arrays:
```r 
#Indexing for data frames
a.data.frame[1:3,]
a.data.frame[,2]
```
One can also access specific columns by using the name of that column, which will return the vector in that column
```r 
a.data.frame$names
```
And we can access  some portion of that vector like any vector
```r 
a.data.frame$names[1:3]
```
The variables in data can also be logical variables, that is they take one  of the values TRUE or FALSE. Logical vectors that store this kind of data are very useful, especially in indexing.

```r 
# A vector can be composed of logical values, too(TRUE or FALSE)
a.logic.vector<-c(TRUE,FALSE,TRUE,FALSE,FALSE,FALSE,FALSE)
```
If we use one of the comparison operators (“<”,”>”,”<=”,”>=”,”==”) with other type of vector, the result will be a logical vector whose elements are TRUE or FALSE. The value in the logical vector will be  TRUE, when the comparison is true.
```r 
day.names==”Mon”
day.names==”Tuesday”
day.number<3
```
If we wanted to get  some specific elements  of a vector, say “a”, we can use logical vectors  that have the same length  as index vectors to extract those specific elements. The elements of “a”  that will be extracted are the ones which have TRUE values in the logical vector used for indexing
```r 
#logical indexing (3.3,3.4)
day.names[a.logic.vector]
 
# Count the number of TRUEs in the logical vector
sum(a.logic.vector)
```
The logical indexing is very useful, when you want to extract some portion of the vector that satisfies a particular condition. Let’s look at an example
 
 
This function will load a dataset that’s built into R. This dataset includes a vector with the name nhtemp. It will be loaded with the name nhtemp. It’s the yearly temperature record from New Haven.
```r 
data(nhtemp)
```
 
One can use ls() function to list all the variables that are currently loaded into R
```r 
ls()
```
nhtemp is an R variable that’s slightly different than a vector, so we first want to turn into a regular vector.
```r 
nhtemp <- as.vector(nhtemp)
```
 
If we want to get  temperature records that are  higher than 54 degrees, we can use the logical vector 
```r 
nhtemp>54
nhtemp[nhtemp>54]
```
If we want to get the indices  of the TRUE values in  logical vectors, we use the “which” function

```r 
which(nhtemp>54)
```
Now we  can use plot functions to plot this series of tempearatures
If we  use only  one argument in the plot function, 
```r 
plot(nhtemp)
```
If we want to plot x-y plot (temperature against the years
```r 
plot(1912:1971,nhtemp)
 
plot(1:60,nhtemp,type='l')
```
These are the summary statistics functions in R
```r 
mean(nhtemp)
median(nhtemp)
max(nhtemp)
min(nhtemp)
var(nhtemp)
 
sd(nhtemp)
sqrt(var(nhtemp))
summary(nhtemp)
```
For plotting histograms, we use hist function with different 
```r 
hist(nhtemp)
hist(nhtemp,breaks=14)
hist(nhtemp,breaks=seq(min(nhtemp),max(nhtemp),0.5))
boxplot(nhtemp)
```
 
```r 
smokes = c("Y","N","N","Y","N","Y","Y","Y","N","Y")
amount = c(1,2,2,3,3,1,2,1,3,2)
 
a.table <- table(smokes,amount)
prop.table(a.table)
 
chisq.test(a.table)
```
 
