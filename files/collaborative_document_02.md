![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document. Day 2, Wed 23 March 2022

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

Barbara Vreede
Pablo Rodríguez-Sánchez

## 🧑‍🙋 Helpers

Candace Makeda Moore
Lieke de Boer

## 🗓️ Agenda

<div class="row">
  <div class="col-md-6">
    <h3>Day 2. Wed 23 March 2022</h3>
    <table class="table table-striped">
      <tr> <td>09:00</td>  <td>Welcome and icebreaker</td> </tr>
      <tr> <td>09:15</td>  <td>Testing</td> </tr>
      <tr> <td>10:15</td>  <td>Coffee break</td> </tr>
      <tr> <td>10:30</td>  <td>Testing (continuation)</td> </tr>
      <tr> <td>11:00</td>  <td>Documenting your packages</td> </tr>
      <tr> <td>11:30</td>  <td>Coffee break</td> </tr>
      <tr> <td>11:45</td>  <td>Documenting your packages (continuation)</td> </tr>
      <tr> <td>12:15</td>  <td>Managing dependencies</td> </tr>
      <tr> <td>12:45</td>  <td>Wrap-up</td> </tr>
      <tr> <td>13:00</td>  <td>END</td> </tr>
    </table>
  </div>
</div>

## 🔧 Exercises

### Write a test that shows that addition works. 

Elma:
```R=
test_that("addition works", {
  expect_equal(2 + 2, 4)
})
```
Wahideh:
```R=
test_that("addition works", {
expect_equal(2 + 2, 4)
})
```
Sally:
```R=
test_that("Addition works", {
  expect_equal(2 + 2, 4)
})
```
Sheery:
```
test_that("addition works", {
  expect_equal(2 + 2, 4)
})
```
Floor: 
```R= 
test_that("addition works", {
  expect_equal(1 + 3, 4)
}) 
```


### Write a test that tests the shape of the table (3 rows x 2cols)
Elma:
```r=
test_that("Shape of output", {

  # Create an example
  names <- c("Luke","Vader","Lea","Chewbacca","Solo","R2D2")
  # Use the function
  grouped_names <- make_groups(names)

  # Get the dimension of the output
  dimensions_output <- dim(grouped_names)

  # Test feature rows
  expect_equal(dimensions_output[1],3)
  # Test feature columns
  expect_equal(dimensions_output[2],2)
})
```
Wahideh:
```r=
test_that("shape of table", {
  # Create an example
  names <- c("L", "V", "L2", "C", "S", "R2D2")
  # Use the function
  grouped_names <- make_groups(names)
  # Test a feature
  expect_equal(nrow(grouped_names), 3)
  expect_equal(ncol(grouped_names), 2)
})

```
Sally:
```r=
# Test: the number of columns 
# = the number of people per group
  expect_equal(ncol(grouped_names),
               n_people_per_group)

  # Test: the number of rows
  expect_equal(nrow(grouped_names),
               ceiling(length(coffee_names) 
                       / n_people_per_group))
```
Sheery:
```r=

```
Floor:
```r=
test_that("number_of_cols_and_rows", {
  #Create an example
  names <- c("Luke", "Vader", "Leia", "Chewbacca", "Solo", "R2D2")
  # use the function
  grouped_names <- make_groups(names)

  #test columns
  expect_equal(ncol(grouped_names),2)

  #test rows
  expect_equal(nrow(grouped_names),3)


})

```
Chunyuan:
```r=
test_that("shape_of_group",{
# Test the shape of table
# Create an example
names <- c("L", "V", "LL", "C", "S", "R")
group_name <- make_groups(names)

# Test features
expect_equal(ncol(group_name),2)
expect_equal(nrow(group_name),3)
  }
``` 

### Write a second function
- This function either uses `make_groups()`, or is used by `make_groups()`
- The function uses another package (like `knitr`, but it can be anything you like)
- One of your function is exported, the other is not (hint: which function should be exported?)
- Both functions have a Roxygen documentation structure
- If you have time, you can write a test for this second function :smiley: 

Elma:
```r=
#' Making random groups from a list of names
#'
#' Helper function to make the random groups.
#'
#' @param names vector of strings with participant names
#'
#' @return a matrix with random couples

make_groups <- function(names) {
  # Shuffle the input names
  names_suffled <- sample(names)

  # Arrange it as a 2-columns matrix
  names_coupled <- matrix(names_suffled, ncol = 2)

  return(names_coupled)
}

#' Making random groups from a list of names
#'
#' Makes random groups and returns in a pretty table
#'
#' @param names vector of strings with participant names
#'
#' @return a pretty table with random couples
#' @export

make_pretty_groups <- function(names){
  # make random group of the input names
  grouped_names <- make_groups(names)

  # Create a pretty table of the grouped names
  pretty_table <- knitr::kable(grouped_names)

  return(pretty_table)
  }
```
Wahideh:
```r=

```
Sally:
```r=
' Visualize Coffee Groups
#'
#' @param names a string of names
#' @param n_people the number of people per group
#'
#' @return a ggplot2 graph with groups that will drink coffee together.
#' @export

visualize_groups <- function(names,
                             n_people = 2) {

  # Make groups
  grouped_names <-
    create_groups(names = names,
                  n_people = n_people)

  # Initialize plot
  coffee_plot <-
  ggplot2::ggplot() +
    # Plot coffee cups
    emojifont::geom_emoji(alias = "coffee",
                          x = 0,
                          y = 1:nrow(grouped_names),
                          size = 10) +
    # Plot names
    ggplot2::geom_text(ggplot2::aes(x = -1,
                  y = 1:nrow(grouped_names),
                  label = grouped_names[,1]))+
    ggplot2::geom_text(ggplot2::aes(x = 1,
                                    y = 1:nrow(grouped_names),
                                    label = grouped_names[,2]))+
    # Nice styling
    ggplot2::theme_void() +
    ggplot2::scale_x_continuous(limits = c(-5, 5))

  return(coffee_plot)

}

```
Sheery:
```r=
make_visual <- function(names){
    #
}

```
Floor:
```r=
#' Making random groups from a list of names
#'
#' @param names vector of strings with participant names
#'
#' @return a matrix with random couples

make_groups <- function(names) {
  # Shuffle the names
  names_shuffled <- sample(names)

  # Arrange it as a two-column matrix
  names_coupled <- matrix(names_shuffled, ncol = 2)

  return(names_coupled)
}

#tweede functie die gebruik maakt van de eerste

#' Html Table of grouped names
#'
#' @param names
#'
#' @return an html table of the grouped names
#' @export
#'
make_groups_html_table <- function(names) {
   grouped_names <- make_groups(names)
  html_table <- kableExtra::kable(grouped_names)
    return(html_table)
  #

}


```
Chunyuan:
```r=

```

### h3
Elma:
```r=

```
Wahideh:
```r=

```
Sally:
```r=

```
Sheery:
```r=

```
Floor:
```r=

```
Chunyuan:
```r=

```

## 🧠 Collaborative Notes

### Testing

Open your package from yesterday. 

We have this function:

```r=
make_groups <- function(names) {
  # Shuffle the names
  names_shuffled <- sample(names)
  
  # Arrange it as a two-column matrix
  names_coupled <- matrix(names_shuffled, ncol = 2)
  
  return(names_coupled)
}
```

We're going to write some tests. Usually, when you write a function, you try that it works. 

Press `install and restart`

We will make a variable `names`

```r=
names <- c("Luke", "Vader", "Leia", "Chewbacca", "Solo", "R2D2")

grouped_names <- make_groups(names)

grouped_names
```

This worked as we expected. This is probably the way you test your own functions or scripts at the moment. We want to make sure no name appears twice, we want two columns only, we want to make sure everyone has a partner. We want the output to be a matrix, and we want the output to be random. Usually, you find this out just by looking (you do it once, and you forget about it). But we can also write a test.

Tests are files in the package. Everything inside testthat.R will be understood as a test. 

We can automatically create a folder that includes test. For this, use the command:

```r=
usethis::use_testthat()
```

Now we have added a folder `tests/testthat`
And a script `tests/testthat.R`

So far, the `testthat.R` script includes a check that the package is loaded. 

We use the colon notation `::` so we don't attach the package `usethis`, we only attach the function `use_testthat()` from the `usethis` package.

Rstudio is advising us to call `use_test()` to initialize a basic test file and open it for editing. Let's do that:

```R=
usethis::use_test()
```

Now, Rstudio created a file that looks like this:

```r=
test_that("multiplication works", {
    expect_equal(2 * 2, 4)
})
```

The `expect_equal` function has two arguments, the real input, and the expected output. What we are checking, is that if we multiply 2 and 2, we arrive at the answer 4. 

The first argument (``"multiplication works"``) is just a string that tells us what the test does.

**IMPORTANT!** If you put anything that's not a function inside an R file inside the R folder, R does not know how to deal with it! You package will not load when you press `Install and restart`.

It's a good idea to be paranoid when testing. 2 times 2, and 2 + 2 have the same answer. So 2 * 2 and 2 + 2 are perhaps not the best tests for multiplication and additon, respectively. In order to test, you have to think of ways to break the code. 

You can add multiple tests to a single `test_that` function

```r=
test_that("multiplication works", {
    expect_equal(2 * 2, 4)
    expect_equal(4 * 12, 48)
})
```
`test_that` contains several functions that can expect things, like `expect_error`.

Let's make a test that's actually useful to our package. 

```r=
usethis::use_test('make_groups')
```

Again, R creates an example for us, that tests if multiplication works. 

What would we like to check for our package?

We can create a file called `test-make_groups.R`

```r=
test_that("number of elements"){
# create an example
    names <- c("Luke", "Vader", "Leia", "Chewbacca", "Solo", "R2D2")
# use the function
    grouped_names <- make_groups(names)
#test a feature
    expect_equal(length(grouped_names), 6)
    expect_equal(length(grouped_names), length(names))
}
```

You can test your package, by clicking on "more" > "test package"

R then loads and tests the package. All of your tests should have passed. 

The most interesting thing happens when tests fail. Imagine that in one month, you reopen the project. 

If a test fails, Rstudio will directly point you to the test that fails, so you can expect the way in which your package is behaving unexpectedly. 

Let's copy the number of elements test, but use an uneven number of elements. 

```r=
test_that("number of elements"){
# create an example
    names <- c("Luke", "Vader", "Leia", "Chewbacca", "Solo", "R2D2", "Jar Jar Binks")
# use the function
    grouped_names <- make_groups(names)
#test a feature
    expect_equal(length(grouped_names), 7)
}
```

A test fails, because now the matrix has 8 elements, not 7. 

What can we do to fix this problem? 

Create groups of 3, let one person have coffee twice. 

Testing can help you improve your code!

### Documentation

For who do you write your code? 

- Yourself
- Potential users
- Colleagues

There is you, people who will work with it, and people who are working with you and using it. To make life easier for everyone, including yourself, there is documentation that we can provide. 

In what ways can you add text to your package?

- Comments (important for yourself and developers)
- Text file in the project with workflow (like vignettes)
- Help functions

We will use `roxygen2` to write help functions. 

Go to Rstudio, click on `build`, and `configure build tools`. 

Go to "generate documentation", and tick "install and restart" on top of everything else. 

Open your `functions.R` script. 

Sidenote: NAMESPACE contains everything that is contained in this package. We will now start building documentation. Roxygen is going to make it easy.

Click on `code` and `Insert Roxygen skeleton`

Now we have a section at the top of the function with some elements:

```r=
#' Title
#' 
#' @param names
#' 
#' @return
#' @export
#' 
#' @examples
```

Let's fill out the skeleton:

```r=
#' Making random groups from a list of names
#'
#' This function can be used to make couples for random coffee dates out of a vector of names.
#' 
#' @param names vector of strings
#' 
#' @return a matrix with random couples
#' @export
```
We skip the examples for now. 

You should delete the `man` folder and the `NAMESPACE` file. 

When you have filled this in, click "install and restart".

After installing and restarting, the man folder contains a help function, generated automatically by Roxygen. 

Check out your help function!

```r=
?make_groups
```

The `export` element in roxygen is important. It makes sure the function is available to users. It needs to be included for people to be able to call the function. If there is something that needs to be done in the package that has nothing to do with what the package does for the user.

For example:

```r=
#' Making random groups from a list of names
#'
#' This function can be used to make couples for random coffee dates out of a vector of names. It returns a pretty table
#' 
#' @param names vector of strings with participant names
#' 
#' @return a pretty table with random couples
#' @export
make_pretty_groups <- function(names){
    grouped_names <- make_groups(names)
    pretty_table <- knitr::kable(grouped_names)
    return(grouped_names)  
}

```
If we don't want to give users direct access to the helper function (`make_groups`), we can remove `@export` from the `make_groups` function. 

### Managing dependencies

When we use other packages inside our package, we create a dependency. How do you work when you are calling other packages? When you are using functions from another package, you want to make sure you always use the double colon notation. 

Sometimes you cannot do this. In those cases, you have to import your package inside your function space. 

We have to make sure that the user of our package also installs the other required packages. 

Inside the function, we can use the following notation:

```r=
usethis::use_package("knitr", type = "Imports")
```

there are two types, "Imports" and "Suggests". 

When we execute this in the console, our DESCRIPTION file is updated. Now, the Imports field has "knitr" written underneath. 

If you have a package that would be _nice to have_, but not essential, you can use the following:

```r=
usethis::use_package("ggplot2", type = "Suggests")
```

Now, the DESCRIPTION file is updated to include `ggplot2` in the `Suggests` field. 

You can also simply edit your DESCRIPTION file directly in the editor. 

Versions can be relevant as well. 

```r=
usethis::use_package("knitr", type="Imports", min_version="1.2")
```

This states that the minimum version we need to have of knitr is 1.2.




## Questions

Q: **How should I use tests for more complicated functions?**

A: Think about how you are testing your code in the console. You could turn all of your checks into a test. 

Q: **How do we document default values? For example, number of default numbers of a group.**

A: When you write a function and there's a default, you can include it in the function. In the roxygen skeleton, you can include it in the @param description of the parameters. There is also a @usage parameter in the Roxygen skeleton where you can specify the usage of each parameter. Check out `?knitr::kable` for an example of `usage`

Q: **Should you add the fact that @export isn't used in the documentation?**

A: Helper functions don't often have roxygen documentation. They can do, but it's not common, because the functions don't end up in the users workspace

## Tips (what could be improved)
- Some excersises were a bit easy whereas others were a tad difficult.

- Perhaps some sort of differentiation could be benefitial to keep teaching at the individual levels of ability. Break-out rooms could perhaps be useful. This also allows for more complicated examples (content wise, e.g., more elaborate tests; more elaborate grouping functions) while keeping the workflow/basic-knowledge instructions the same.

## Tops (what went well)
- Great instructions. Also the collaborative document is very handy. Thanks.
- Appreciated the pace of the instructions and the exercises. Really found it useful to have the workflow shown once and having to replicate it after. 
- Thank you for making sure no one was left behind. I missed the first class but was brought up to speed in no time. The collaborative document also really helps to go over the materials I have missed.
- Sometimes the notes were needed/usefull because you'd forgotten a step. So will also be using them as documentation after the course.
- Great, to go to each step, very clear instructions
- Again the 'sfeer' was very open for asking whatever question or error was encountered. Also appreciated the fact that some 'group' errors were improvised and resolved on the spot.
- The fact that 'helpers' encourage eachother to share their knowledge shows that no-one can know it all... This way asking a question is less of an obstacle!
- 
## 📚 Resources
- [Package dependencies](https://rstudio.github.io/renv/reference/dependencies.html)
- 