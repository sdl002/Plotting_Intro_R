# Plotting_Intro_R
This is an intro to plotting with R, and will introduce basic ggplot techniques as well as how to intregrate with Plotly.

<img src="/pics/plot_examples.png" width="800">  
     
       
       

&nbsp;  
&nbsp; 
### There are a lot of Intros on ggplot2 available, I put together a brief overview that takes no more than 1 hour to work through, but I highly reccomend also considering the following tutorials for a more in depth training:
1. http://r-statistics.co/Complete-Ggplot2-Tutorial-Part1-With-R-Code.html  
2. https://rpubs.com/arvindpdmn/ggplot2-basics  
3. https://bookdown.org/skaltman/visualization-book/the-basics-of-ggplot2.html  

*Some examples used below are from the above links*   
  
&nbsp;  
&nbsp;  

<img src="/pics/logo_ggplot2.png" width="200">  

## The Basics: What is ggplot2?

ggplot2 is an R package that allows for customizable data visualization. It is part of the tidyverse package suite and is a very well maintained and continuously updated package. https://ggplot2.tidyverse.org/

To use ggplot2, you will need to have access to `R`, and I reccomend following along with `RStudio`. You can either use a local installation or a server installation. 

To install ggplot2 you can do the following:

#### The easiest way to get ggplot2 is to install the whole tidyverse:
```
install.packages("tidyverse")
```
*tidyverse includes popular R packages such as dplyr, readr, tibble, and others. They follow a tidy data philosophy: https://www.tidyverse.org/*

#### Alternatively, install just ggplot2:
```
install.packages("ggplot2")
```

ggplot2 cheat sheets:
<img src="/pics/datavis_1.png" width="200">

https://github.com/rstudio/cheatsheets/blob/master/data-visualization-2.1.pdf
