--- 
title: "Computational Probability and Statistics"
author: 
- Matthew Davis
- Brianna Hitt
- Ken Horton
- Kris Pruitt
- Bradley Warner
date: "2022-08-11"
header-includes:
   - \usepackage{multirow}
   - \usepackage{multicol}
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
cover-image: "figures/Cover_Majors.png"
description: "This is a set of notes used for Math 377, starting in the fall of 2020, that has been compiled into a book."
---

\input{latex/math-definitions.tex}

# Preface {-}


<img src="./figures/Cover_Majors.png" width="100%" />
  

This book is based on the notes we created for our students as part of a one semester course on probability and statistics. We developed these notes from three primary resources. The most important is the Openintro Introductory Statistics with Randomization and Simulation [@ointrorand] book. In parts, we have used their notes and homework problems. However, in most cases we have altered their work to fit our needs. The second most important book for our work is Introduction to Probability and Statistics Using R [@ipsur]. Finally, we have used some examples, code, and ideas from the first edition of Prium's book, Foundations and Applications of Statistics: An Introduction Using R [@pruim2011foundations].  

## Who is this book for?

We designed this book for the study of statistics that maximizes computational ideas while minimizing algebraic symbol manipulation. Although we do discuss traditional small-sample, normal-based inference and some of the classical probability distributions, we rely heavily on ideas such as simulation, permutations, and the bootstrap. This means that students with a background in differential and integral calculus will be successful with this book. 

This book makes extensive using of the `R` programming language. In particular we focus both on the **tidyverse** and **mosaic** packages. We include a significant amount of code in our notes and frequently demonstrate multiple ways of completing a task. We have used this book for junior and sophomore college students.

## Book structure and how to use it

This book is divided into four parts. Each part begins with a case study that introduces many of the main ideas of each part. Each chapter is designed to be a standalone 50 minute lesson. Within each chapter, we give exercises that can be worked in class and we provide learning objectives. 

This book assumes students have access to `R`. Finally, we keep the number of homework problems to a reasonable level and assign all problems.

The four parts of the book are:

1. Descriptive Statistical Modeling: This part introduces the student to data collection methods, summary statistics, visual summaries, and exploratory data analysis. 

2. Probability Modeling: We discuss the foundational ideas of probability, counting methods, and common distributions. We use both calculus and simulation to find moments and probabilities. We introduce basic ideas of multivariate probability. We include method of moments and maximum likelihood estimators.

3. Inferential Statistical Modeling: We discuss many of the basic inference ideas found in a traditional introductory statistics class but we add ideas of bootstrap and permutation methods. 

4. Predictive Statistical Modeling: The final part introduces prediction methods, mainly in the form of linear regression. This part also includes inference for regression.


The learning outcomes for this course are to use computational and mathematical statistical/probabilistic concepts for:  

a. Developing probabilistic models.  
b. Developing statistical models for description, inference, and prediction.   
c. Advancing practical and theoretical analytic experience and skills.  


## Prerequisites

To take this course, students are expected to have completed calculus up through and including integral calculus. We do have multivariate ideas in the course, but they are easily taught and don't require calculus III.  We don't assume the students have any programming experience and, thus, we include a great deal of code. We have historically supplemented the course with [Data Camp](http://datacamp.com/) courses. We have also used [RStudio Cloud](http://rstudio.cloud) to help students get started in `R` without the burden of loading and maintaining software.

## Packages

These notes make use of the following packages in `R`: **knitr** [@R-knitr], **rmarkdown** [@R-rmarkdown], **mosaic** [@R-mosaic], **mosaicCalc** [@R-mosaicCalc], **tidyverse** [@R-tidyverse], **ISLR** [@R-ISLR], **vcd** [@R-vcd], **ggplot2** [@R-ggplot2], **MASS** [@R-MASS], **openintro** [@R-openintro], **broom** [@R-broom], **infer** [@R-infer],  **kableExtra** [@R-kableExtra], and **DT** [@R-DT].

## Acknowledgements 

We have been lucky to have numerous open sources to help facilitate this work. Thank you to those who helped to correct mistakes to include Skyler Royse.

This book was written using the **bookdown** package [@R-bookdown].

<img src="./figures/by-nc-sa.png" width="10%" />


This book is licensed under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/).



## File Creation Information 

  * File creation date: 2022-08-11
  * R version 4.1.3 (2022-03-10)




