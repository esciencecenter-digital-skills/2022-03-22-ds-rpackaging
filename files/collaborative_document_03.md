![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document. Day 3, Thu 24 March 2022

2022-03-22-ds-rpackaging.

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

Collaborative Document day 1: [link](https://tinyurl.com/2022-03-22-ds-rpackaging-01)

Collaborative Document day 2: [link](https://tinyurl.com/2022-03-22-ds-rpackaging-02)

Collaborative Document day 3: [link](https://tinyurl.com/2022-03-22-ds-rpackaging-03)

## 👮Code of Conduct

* Participants are expected to follow those guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.
 
## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, type `/hand` in the chat window.

To get help, type `/help` in the chat window.

You can ask questions in the document or chat window and helpers will try to help you.

## 🖥 Workshop website

[link](https://esciencecenter-digital-skills.github.io/2022-03-22-ds-rpackaging)

🛠 Setup

[link](https://esciencecenter-digital-skills.github.io/2022-03-22-ds-rpackaging/#setup)

## 👩‍🏫👩‍💻🎓 Instructors

Lieke de Boer
Barbara Vreede
Pablo Rodríguez-Sánchez

## 🧑‍🙋 Helpers

Candace Makeda Moore
Dafne van Kuppevelt

## 🗓️ Agenda

<div class="row">
  <div class="col-md-6">
    <h3>Day 3. Thu 24 March 2022</h3>
    <table class="table table-striped">
      <tr> <td>09:00</td>  <td>Welcome and icebreaker</td> </tr>
      <tr> <td>09:15</td>  <td>Data</td> </tr>
      <tr> <td>10:15</td>  <td>Coffee break</td> </tr>
      <tr> <td>10:30</td>  <td>Vignettes</td> </tr>
      <tr> <td>11:30</td>  <td>Coffee break</td> </tr>
      <tr> <td>11:45</td>  <td>...</td> </tr>
      <tr> <td>12:45</td>  <td>Wrap-up</td> </tr>
      <tr> <td>13:00</td>  <td>END</td> </tr>
    </table>
  </div>
</div>

## 🔧 Exercises

### Go into your tests, and replace the testing data with data from the package. 

Elma:
```r=
test_that("number of elements", {

  # Create an example

  names <- load("../data/example_names.rda")
  # Use the function
  grouped_names <- make_groups(names)

  # Test feature number elements
  expect_equal(length(grouped_names),6)
  })
```
*Example did not work*

Wahideh:
```r=

```
Sally:
```r=
test_that("number of elements", {

  n_people_per_group = 2

  # Test the function
  grouped_names <-
    create_groups(names = example_names,
                  n_people = n_people_per_group)

  # Test the feature
  expect_equal(length(grouped_names),
               length(example_names))
  # Hardcoding can be desirable in some cases
  # ... of testing because it replaces
  # ... the manual 'eyeball' testing we normally
  # ... run in the console.
  expect_equal(length(grouped_names),
               6)
})
```
Sheery:
```r=


```
Floor:
```r=
test_that("number_of_elements", {
  # use the function
  grouped_names <- make_groups(example_names)

  #test a feature
  expect_equal(length(grouped_names), length(example_names))
})
```

### Edit the Vignette so it explains the `mysterycoffee` package

Elma:
```r=
{r create pretty groups, echo=FALSE}
```
Wahideh:
```r=
Working from home was boring during lock down. This package helped with pairing colleagues to drink coffee online.
```
Working from home was boring during lock down. This package helped with pairing colleagues to drink coffee online.

```
Sally: DONE


Sheery:
```r=
---
title: "Vignette Title"
output: rmarkdown::html_vignette
vignette: >
  %\VignetteIndexEntry{Vignette Title}
  %\VignetteEngine{knitr::rmarkdown}
  %\VignetteEncoding{UTF-8}
---
```
Floor:
```r=
---
title: "Example of usage"
author: "Floor"
date: "24-3-2022"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
library(tidyverse)
```

## Mystery coffee

Tired of talking to the same people all the time? Let's refresh your work coffee breaks by using the Mystery Coffee package. Mystery coffee let's you input a list of names and randomly shuffle it into pairs. 

Below, we'll show you how to use the functions with our built-in sample data set. 

```{r example_names table}
example_names
```

## Making pairs using make_groups



```{r make_groups}
make_groups(example_names)
```

## You can also create a pretty html-table

```{r html_table}
make_groups_html_table(example_names)
## not very pretty yet though


```


## 🧠 Collaborative Notes

### Data

There are two ways in which you can add data to your package, there is the `data` folder inside your package. The data folder only takes data that is specifically R formatted data. Like `.rda` or `.Rdata`.

Let's make some data. 

```r=
names <- c("Chewbacca", "Solo", "Luke", "Leia", "R2D2", "Vader")

usethis::use_data(names)
```

When we execute this, we see that a folder `data` has appeared, containing a file called `names.rda`.

`names` is not a very good name for a variable. It's also a function. Let's instead use another file name so we don't create a confusing variable name.

```r=
example_names <- c("Chewbacca", "Solo", "Luke", "Leia", "R2D2", "Vader")

usethis::use_data(example_names)
```

Thinking about your data names and your variable names is important. Avoid confusion!

Open a new script inside the R folder inside your package. Call it `example_names.R`. The content of this file needs to be 

`"example_names"`

Inside this file, we will document the data that we have just included. 

```r=
#' Example names
#'
#' Example names with characters from the Starwars universe that
#' can be used to test the functions in mysterycoffee
#' @format a vector of strings
#' @keywords starwars
#' @author George Lucas / Barbara Vreede
#' @references \url{https://www.starwars.com}
"example_names"
```

Save this file and press "install and restart". Now you can call the help function on your data by typing

```r=
?example_names
```

into the console. 

Your datasets should be inside your data folder, and a description of this data in the R folder. 

Let's see how the data referring works

```r=
another_dataset <- c("Makeda", "Lieke", "Pablo", "Barbara")
starwars_names <- c("Chewbacca", "Solo", "Luke", "Leia", "R2D2", "Vader")
```

Save these to variables as `environment.Rdata`, using for example `save.image`. 

```r=
#' Example names
#'
#' Example names with characters from the Starwars universe that
#' can be used to test the functions in mysterycoffee
#' @format a vector of strings
#' @keywords starwars
#' @author George Lucas / Barbara Vreede
#' @references \url{https://www.starwars.com}
"example_names"
#
#' Example names with characters from the Starwars universe that
#' can be used to test the functions in mysterycoffee
#' @format a vector of strings
#' @keywords starwars
#' @author George Lucas / Barbara Vreede
#' @references \url{https://www.starwars.com}
"starwars_names"

#' Another dataset
#'
#' Example names from teachers from our course
#' @format a vector of strings
#' @keywords eScienceCenter
"another_dataset"
```
We can save the above as `datasets.R`, and remove `example_names.R`. Now we can build the package and use help functions on all three datasets. 

We will get rid of the environment variable by deleting `environment.Rdata` from the package, and adding:

```r=
usethis::use_data(starwars_names)
usethis::use_data(another_dataset)
```
It's nicer to save your datasets separately, and not as an environment. 

When you have data saved in your package, your can refer to these datasets directly within a test. You can go to `environment`, and click on Global Environment. If you instead select your package, you can see what datasets are part of it. 

The second way to add data in non R-native formats, is to include it in the `inst` folder in the package. You can then add it to the `data` folder when you are creating your package. 

### Vignettes

Software needs manuals which are readable by users. This is a manual that combines chunks of code with readable text. 

A vignette is a plain text file that contains Markdown text and chunks of R. This file can be knitted. When you knit a document, the code is executed, and the text is displayed. 

You can export it as a website, pdf, or microsoft Word file. It's surprisingly easy to do this. 

Why would you want to combine text and code? 

- Sharing analysis and workflow with others
- Incorporate output of analysis in text
- Updating figures without having to redo it
- Updating data features without having to rerun analyses
- Keeps all the work in one place keeps things tidy

If someone is interested in your results, they could download your package and knit your vignette. This would then lead them to exactly replicate your paper. 

Vignettes are not a necessary part of R packages, but are a powerful addition if you do add them. 

Within a package, you can create a folder called "\vignettes". 

```r=
usethis::use_vignette()
```

We create a new Markdown file. (File > New Markdown File)

Create the titel "Example of usage"

HTML is the right format to start with. You can still always knit to PDF later. 

A new document appears. There's a non-empty example of a markdown file. Click on save, and save this file in the vignettes folder. Save it as `examples.Rmd`. 

Check out the header, which has `title`, `author`, `date` and `output` fields. 

Just like in HackMD, you can write code in the R Markdown file. You can use different languages. The difference is that you have to use curly brackets.

```{r cars}
summary(cars)
```

The first element refers to the language, the second to the identifier for the chunk. You can only use the same identifier once for each vignette. 

There is an `echo` element, which specifies if the chunk is printed in the vignette, or just executed without printing it. 

You can now knit this document by clicking on `knit` at the top of the document. 

You can hide the last chunk (but not the output) by adding `echo = FALSE` to the chunk. 

```{r cars, echo = FALSE}
summary(cars)
```

## Questions

Q: **Can you store a csv file in the data folder?**
A: No, csv files need to go in the `inst` folder. You can load that data in a script in R, and put in into an R readable format in your `data` folder. 

Q: **What should I do if I have lots of data? i.e. gigabytes of data.**
A: If your package is used by others, they will download the gigabytes, but it's not loaded into the workspace until it is called. However, it may be a bad idea to upload huge amounts to GitHub. You may want to use a data repository instead, and include a reference to it in the package. 

That said, there are also data packages, that include just data. 

Q: **Does the file name need to be the same as the data name?**
A: Yes, and it is also good practice. 

Q: **How do I find the datasets that are part of a package?**
A: You can type `packagenames::` and press tab. The data that is included in the package has a spreadsheet symbol in front of it. 
A2: you can change environments from `global` to the package to see which data and functions a package contains.


## 📚 Resources

- [Adding **raw** data to your package](https://r-pkgs.org/data.html)
- [Changing R library location on Windows](https://www.accelebrate.com/library/tutorials/r-rstudio-library)
- [R Packages book](https://r-pkgs.org/)
- [post-workshop survey](https://www.surveymonkey.com/r/GWT6925)