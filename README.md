# Plotting_Intro_ggplot2
This is an intro to plotting with R, and will introduce basic ggplot techniques as well as how to intregrate with Plotly.

<img src="/pics/plot_examples.png" width="800">  
     
       
       

&nbsp;   
&nbsp; 
### There are a lot of Intros on ggplot2 available, I put together a brief overview that takes no more than 1 hour to work through, but I highly reccomend also considering the following tutorials for a more in depth training:
1. http://r-statistics.co/Complete-Ggplot2-Tutorial-Part1-With-R-Code.html  
2. https://rpubs.com/arvindpdmn/ggplot2-basics  
3. https://bookdown.org/skaltman/visualization-book/the-basics-of-ggplot2.html  

*Some information and examples described below are from the above links*   
  
&nbsp;  
&nbsp;  

<img src="/pics/logo_ggplot2.png" width="200">  

## The Basics: What is ggplot2?

ggplot2 is an R package that allows for customizable data visualization. It is part of the tidyverse package suite and is a very well maintained and continuously updated package. https://ggplot2.tidyverse.org/

To use ggplot2, you will need to have access to `R`, and I recommend following along with `RStudio`. You can use a local installation, a server installation, or prefereably you can follow along using the docker image built by the dockerfile found here.


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

#### As always, you must load the package

The easiest way is to just `library` the package
```
library("ggplot2")
```

#### You are now ready to work with ggplot2, see cheat sheeps below to get started with the basics

ggplot2 cheat sheets: &nbsp;  
<img src="/pics/datavis_1.png" width="400">  
<img src="/pics/datavis_2.png" width="400">  
https://ggplot2.tidyverse.org/index.html



# Basic ggplot2 concepts:

ggplot2 was developed by Hadley Wickham (developer of the Tidyverse).    
<img src="/pics/hadley_wickham.jpeg" width="600">  

ggplot2 is different than most graphics packages, it uses underlying grammar that is based on the ["Grammar of Graphics"](https://link.springer.com/chapter/10.1007/978-3-642-21551-3_13). This allows the user to compose graphs by combining independent components. One can think about the plots as having layers of data.   
&nbsp;   

### The Grammar of Graphics
<img src="/pics/grammar_of_graphics.png" width="800">  
`The Grammar of Graphics. Visual by Thomas de Beus`


### There are three main components to every ggplot graph:
#### 1. Data (usually as a datafram)
#### 2. Plot Aesthetics (indicates x and y variables, colors, shapes, sizes, etc.)
#### 3. Geometry (boxplot, scatter plot, violin plot, etc.)


