![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document. R Packaging, Day 1, Tue 22 March 2022

2022-03-22-ds-rpackaging.

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

Collaborative Document day 1: [link](https://tinyurl.com/2022-03-22-ds-rpackaging-01)

Collaborative Document day 2: [link](https://tinyurl.com/2022-03-22-ds-rpackaging-02)

Collaborative Document day 3: [link](https://tinyurl.com/2022-03-22-ds-rpackaging-03)

## 👮Code of Conduct

Participants are expected to follow these guidelines:
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
    <h3>Day 1. Tue 22 March 2022</h3>
    <table class="table table-striped">
      <tr> <td>09:00</td>  <td>Welcome and icebreaker </td> </tr>
      <tr> <td>09:15</td>  <td>Introduction</td> </tr>
      <tr> <td>09:45</td>  <td>Accessing packages</td> </tr>
      <tr> <td>10:15</td>  <td>Coffee break</td> </tr>
      <tr> <td>10:30</td>  <td>Getting started</td> </tr>
      <tr> <td>11:30</td>  <td>Coffee break</td> </tr>
      <tr> <td>11:45</td>  <td>Writing your own functions</td> </tr>
      <tr> <td>12:45</td>  <td>Wrap-up</td> </tr>
      <tr> <td>13:00</td>  <td>END</td> </tr>
    </table>
  </div>
</div>

## 🔧 Exercises
### Exercise: The `DESCRIPTION` file
Open the `DESCRIPTION` file.
What do you see here?

Take 5 minutes to edit this file with the information it asks.
In particular, edit the following fields (when needed):
`Title`, `Version`, `Author`, `Maintainer`, `Description`.
For now, ignore the rest.

Answers:
* Elma
```
Package: mysterycoffee
Type: Package
Title: Create Mystery Coffee Couples
Version: 0.1.0
Author: Elma Tenner
Maintainer: Elma Tenner
Description: To create a datatable where the inputdata is reordered, whereby 
couples are created. The input is a list of names, the output a datatable with
for each couple a row. This can be used to make random couples from a list
of names.
License: What license is it under?
Encoding: UTF-8
LazyData: true
```

* Joey
* Muhammad
* Sally
```
Title: Create Random Coffee Encounters
Version: 0.1.0
Author: Sally A.M. Hogenboom
Maintainer: Sally Hogenboom <sally.hogenboom@gmail.com>
Description: A simulator for random coffee encounters with groups of N people.

```

* Sheery：
```
Package: mysterycoffee
Type: Package
Title: Seq_match_Excel
Version: 1.0.0
Author: Xirui Liu
Maintainer: Xirui Liu
Description: Read the sequence from PDB file and align them with the sequence read from excel file
License: 
Encoding: UTF-8
LazyData: true
```
* Teshome
* Wahideh
```
Title: Random Coffee Simulator
Version: 0.1.0
Author: Wahideh Achbari
Maintainer: https://github.com/wachbari
Description: This package simulates a random coffee encounters for pairs in a team.
```


## 🧠 Collaborative Notes
**What is a package?**
* A project that is structured with a standardized folder-structure

**Benefits of a package**
* Usability
* Sharing & re-use
* Maintenance
* ...

**Issues with a 'normal' folder structure**
* Where to start reading?
* What is the most recent version?
* Lack of documentation
* Fear of breaking code

**Quick recap: writing a function in R**
```r=
fahrenheit_to_celsius <- function(temp_F) {
  temp_C <- (temp_F - 32) * 5 / 9
  return(temp_C)
}
```

**Install packages from cran**
Several existing packages, written by other people, are available from [CRAN](https://cran.r-project.org/), the official repository for R packages.
We need to install `devtools`. We can do that from the tools window, or in the commandline:
```r=
install.packages("devtools")
```
Make sure to check the box 'install dependencies', so all required dependencies are also installed.

Look carefully at the output when in installing a packages, there could be an error message there.

If you created a useful package, you can submit it to CRAN.

**Using an installed package**
Installed packages first need to be attached to our environment with:
```r=
library("devtools")
```
It automatically attaches also required packages.

You can also use a function from a package, *without* attaching it:
```r=
dplyr::filter()
```
runs the `filter` function from the `dplyr` package.
Especially useful if a function name exists in multiple packages!
The packages still needs to be installed.

**Installing packages from github**
GitHub is the most popular open code repository and many R packages can be found there (we may upload our own package there). Packages that we install from GitHub are *not reviewed*.
We need the package `devtools`.
```r=
devtools::install_github("PabRod/kinematics")
```

**Install a package from source**
if the package is only available on your own computer (like the one you will write yourself) you need to install it from source. You can use the 'build' tab in RStudio and click 'install and restart'. This converts the local package to an installable package, installs it and attaches it to your session. So: build -> install -> attach.

### Getting started
The structur of an R package:
```
.
├── R
│   └── <R functions>
├── README.md
├── LICENSE
├── DESCRIPTION
└── NAMESPACE
```

To create package, in RStudio click `File > New project > New directory` and select `R Package`.
Create a package with package name `mysterycoffee`. Leave the two boxes (git repository, renv) unchecked. Tick 'open in new session' and click 'Create Project'.

Rstudio already created some content in the current directory. It created the `hello.R` file in the `R` directory, with one function in it. The comments in the file contain useful information.

Let's try installing it by pressing `Build -> Install and Restart`. Now we can run:
```r=
hello()
```

Advantages of putting your functions in a package:
* Scripts can become very long and messy with many functions
* If you reuse functions in serveral scripts, you avoid duplication. If you update / improve your function, only need to do it once!

Other possible folders to add in your pacakage structure: 
```
.
├── R
│   └── <R functions>
├── data (optional)
│   └── <data>
├── tests (optional)
│   ├── testthat.R
│   └── testthat
│       └── <tests>
├── vignettes (optional)
│   └── <Rmd vignettes>
├── inst (optional)
│   └── <any other files>
├── README.md
├── LICENSE
├── DESCRIPTION
└── NAMESPACE
```

We will talk more about the `data`, `tests`, `inst` and `vignettes` folders.

We will use the `vignettes` folder to put documentation in Rmarkdown format. 

### Editing our own package
The problem that we want to solve with our package: simulate random encounters between colleagues. 
So we create a function with:
* Input: list of names
* Output: matrix with two columns, each row contains the names of one couple

Open the file `DESCRIPTION` and edit it to update the `Title, Version, Author, Maintainer, Description` (see Exercise).

Note that the description can be very long.

#### Writing our own functions
Open the R folder, to start editing your functions.
We will create a new file: in the top left window, under the files tab, click (+) > R script. Call it `functions.R`.

In this file, write:
```r=
make_groups <- function(names) {
  # Shuffle the names
  names_shuffled <- sample(names)
  
  # Arrange it as a two-column matrix
  names_coupled <- matrix(names_shuffled, ncol = 2)
  
  return(names_coupled)
}
```
The `return()` statement is not necessary (it will automatically return the last assigned variable), but increases the readability and clarity of the function.

We can now also delete the `hello.R` file.

You can make single files per function, of group your functions. There is no single approach to this.

To try the function, we load the package: Build > Install and Restart OR `ctrl+shift+B` / `cmd+shift+B`

We need a variable with a list of names to try this function.
```r=
names <- c("Dafne", "Makeda", "Lieke", "Barbara") 
```
Now we can use the function:
```r=
make_groups(names)
```
### Versioning and Licenses

#### Versions/Versioning
Semantic versioning (not a mandatory system, but recommended) works with 3 numbers: major.minor.patch.
For example, 0.1.0 (a default for your package and a good start!).

Every update that breaks previous functionality should be accompanied by an increase in the **major** version number. If a functionality is added but it doesn't break anything, it can be updated in the **minor** version number. A **patch** update is for small changes, often bugs that are fixed (but if your fix changes the behavior in a backwards-incompatible way, change the major version!). Deciding which to update is not an exact science.

If you encounter a problem in how your package works and write a fix, it is always a good idea to also write a test for it (but we will get back to this!).

Version numbers are for releases only: when you are editing you don't have to update your version, rather when you have a release, that is when you label it. You can do this updating of versions frequently or rarely.

#### Licensing
A license tells users how they can use and re-use your work; e.g. can someone use this software? If they do, can you make money with this or not? Is the author of the work liable in any way? If you do not use a license then your software is completely restricted i.e. the rights are with you and you alone. If you want anyone else to be able to use what you wrote, you must include a license. 

As soon as you start using someone else's package in your work, their license starts being relevant (though with R, using another package as a dependency does not require you to adhere to their license).

Types of (open source) licenses: 'permissive' and 'viral'. The former, like Apache, BSD, MIT licenses, allow the use of your work, but do not mandate that software that uses your work also need to make their software open source. A viral license, like GPL, does do this: if you use software with GPL license in your product, you are also mandated to license your work with GPL.

Your license is stored in a file called `LICENSE` or `LICENSE.md` in the root of your package; also, the `DESCRIPTION` file contains a `License:` field. With the `usethis` functions `use_mit_license()` or `use_gpl_license()` (and many others!) you can update both the `DESCRIPTION` and the `LICENSE.md` in one go (for selected licenses).

Take a look at [choosealicense.com](https://choosealicense.com/) if you want to select a good license for your work. Considerations can be: (how) do you want others to be able to reuse your work? Is there a license that your employer or team uses?
 
Question: If you copy code, but change something, "tweaking it" does the license apply?
Answer: Probably. Depending on the license, but it likely has to do with whether the licensed software is a part of the product. If you write `package A` in R, with `package B` as a dependency, then `package B` gets installed _separately, from its own source_ when your `package A` is installed. Thus, one can argue that the license for `package B` does not apply because it is not part of `package A`. However, when you take code from `package B`, paste it and tweak it into your package, then it becomes part of `package A` and its license is relevant.

Take home:
1. Use a license!
2. Select your license at [choosealicense.com](https://choosealicense.com/)
3. Use `usethis` functions to change your license.

**Summary notes** (Pablo):
Important to understand the following about the future package: What, how and why? Avoid re-inventing the wheel. We can consider re-using existing package. Good idea to keep what and how uncoupled i.e. design and implementation should be kept separate.





## Questions
**What does the `source()` command do?** This is to load a local script into your environment. Not recommended to do this for external packages

**Better to use `::` notation or use `library(package)` and solve conflicts between packages in different way?** Answer: `::` is nicer, because it is explicit where functions come from. But for smaller, single-purpose scripts it's fine to attach packages and refer to a function without `package::` notation. For functions in a package you need to be explicit.

**Installing a package not from GitHub: how to describe the path?**
These are functions in devtools that can be used to install a package from another location than GitHub:

`install_bioc()` = Bioconductor
`install_cran()` = CRAN repository
`install_gitlab()` = GitLab
`install_bitbucket()` = BitBucket
`install_svn()` = SVN repository
`install_local()` = local file
`install_url()` = URL

**How to create package without RStudio?** It's much easier to do it in RStudio, it automates a lot of the work. It's possible to do it programatically with the commandline and plain text files, using the `devtools` and `usethis` packages. Or you could even create all files manually (but that's a lot of labour that is not needed!)

**If your `DESCRIPTION` does not work, use this**
```
Package: mysterycoffee
Type: Package
Title: Facilitating random encounters
Version: 0.1.0
Author: Barbara Vreede
Maintainer: Barbara Vreede <b.vreede@esciencecenter.nl>
Description: This package can be used to group people into random pairs.
License: Apache License (>= 2)
Encoding: UTF-8
LazyData: true

```

## Tips and Tops
### Tips (what can we improve?)
- As an intermediate+ user of R and R studio the introduction was rather slow. Having 5 minutes for changing some data in a description file is realy long and I'm not even sure it should be an exercise at all. That's not to say the speed/the exerceise was usefull for at least some of the participants.
- Encourage participants to send in chat messages to everyone so that helpers do not have to keep reading the comments out loud.
- Some of the bits over packaging and R were a bit basic, good for a base level for everyone but could have been in the pre-reading part as well? Could have got us through that bit faster.
- sometimes a bit mess of looking to which things. Because we have Rstudio and the collaborative document
- During the introduction of the course show the results of the pre-questions of everyone, to get a view how experienced the participants are. And change the speed of the course on this, for me it is a bit slow as experienced user.
- Maybe you will discuss this tomorrow, how to think from programming in 1 big script with some function in there to programming with packages? I mean, today was really clear goal from the beginning to programm a package. It is not clear to me how to incorporate this way of programming in my analyses.

### Tops (What went well?)
- Really nice coverage of licences and some key points that I wasn't aware of
- Overall, very useful overview of issues involved with packaging.
- Very happy with responses of helpers.
- Helpers respond very quickly to any questions in the chat.
- Adding answers to the hackmd file is very useful, though 1 would be sufficient as a dcoumentation for after the course.
- very detailed explanation of the each step and also show very clearly to audiences. 
- The level of expertise is really high which motivates asking spontaneous questions which can actually be answered during the meetings. 
- Great team!!!

## 📚 Resources
[`renv` package for managing dependencies](https://rstudio.github.io/renv/articles/renv.html)
[Download the latest version of R here](https://cran.r-project.org/)
[Kinematics package](https://github.com/PabRod/kinematics) on GitHub
[Choose a license](https://choosealicense.com/)
[Applying a license](https://r-pkgs.org/license.html)