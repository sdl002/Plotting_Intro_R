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
The Grammar of Graphics. Visual by Thomas de Beus
&nbsp; 
  
All plots are composed of the __data__, the information you want to visualise, and a __mapping__, the description of how the data’s variables are mapped to __aesthetic__ attributes. There are five mapping components:

- A __layer__ is a collection of geometric elements and statistical transformations. Geometric elements, geoms for short, represent what you actually see in the plot: points, lines, polygons, etc. Statistical transformations, stats for short, summarise the data: for example, binning and counting observations to create a histogram, or fitting a linear model.

- __Scales__ map values in the data space to values in the aesthetic space. This includes the use of colour, shape or size. Scales also draw the legend and axes, which make it possible to read the original data values from the plot (an inverse mapping).

- A __coord__, or coordinate system, describes how data coordinates are mapped to the plane of the graphic. It also provides axes and gridlines to help read the graph. We normally use the Cartesian coordinate system, but a number of others are available, including polar coordinates and map projections.

- A __facet__ specifies how to break up and display subsets of data as small multiples. This is also known as conditioning or latticing/trellising.

- A __theme__ controls the finer points of display, like the font size and background colour. While the defaults in ggplot2 have been chosen with care, you may need to consult other references to create an attractive plot. A good starting place is Edward Tufte’s early works.  

From: https://ggplot2-book.org/introduction.html


```diff
- The hardest part may be forgetting the preconceptions you brought over from using other graphics tools
```

### There are three main components to every ggplot graph:
#### 1. Data (usually as a datafram)
#### 2. Plot Aesthetics (indicates x and y variables, colors, shapes, sizes, etc.)
#### 3. Geometry (boxplot, scatter plot, violin plot, etc.)

### The main ggplot2 function is:
`ggplot()`

### Generated plots can be kept as variables, printed out at anytime, or saved using:
`ggsave(“plot.png”, width = 5, height = 5)` which saves the last plot in the current working directory.

### ggplot2 can generate the following types of plots (which are dependant on your type of data):
1. One variable - x: continuous or discrete
2. Two variables - x & y: continuous and/or discrete
3. Continuous bivariate distribution - x & y (both continuous)
4. Continuous function
5. Error bar
6. Maps
7. Three variables

## Lets try a few basic plots using a dataset that is part of the ggplot2 package
The below examples are modified from: https://ggplot2-book.org/getting-started.html

load the packages
```
library(ggplot2)
```
Check the following `variable`

```
mpg
```

printed to screen:
```
#> # A tibble: 234 × 11
#>   manufacturer model displ  year   cyl trans      drv     cty   hwy fl    class 
#>   <chr>        <chr> <dbl> <int> <int> <chr>      <chr> <int> <int> <chr> <chr> 
#> 1 audi         a4      1.8  1999     4 auto(l5)   f        18    29 p     compa…
#> 2 audi         a4      1.8  1999     4 manual(m5) f        21    29 p     compa…
#> 3 audi         a4      2    2008     4 manual(m6) f        20    31 p     compa…
#> 4 audi         a4      2    2008     4 auto(av)   f        21    30 p     compa…
#> 5 audi         a4      2.8  1999     6 auto(l5)   f        16    26 p     compa…
#> 6 audi         a4      2.8  1999     6 manual(m5) f        18    26 p     compa…
#> # … with 228 more rows
```

The variables are mostly self-explanatory:

`cty` and `hwy` record miles per gallon (mpg) for city and highway driving.

`displ` is the engine displacement in litres.

`drv` is the drivetrain: front wheel (f), rear wheel (r) or four wheel (4).

`model` is the model of car. There are 38 models, selected because they had a new edition every year between 1999 and 2008.

`class` is a categorical variable describing the “type” of car: two seater, SUV, compact, etc.

This dataset suggests many interesting questions. __How are engine size and fuel economy related?__ __Do certain manufacturers care more about fuel economy than others?__ __Has fuel economy improved in the last ten years?__ We will try to answer some of these questions, and in the process learn how to create some basic plots with ggplot2.


First, lets look at the mpg as our `data`, where our x is engine size and our y is fuel economy

To do so, lets create a scatterplot defined by:

__Data__: mpg.

__Aesthetic mapping__: engine size mapped to x position, fuel economy to y position.
__Layer__: points.
  
__Pay attention to the structure of this function call__: data and aesthetic mappings are supplied in ggplot(), then layers are added on with `+`. *This is an important pattern*, and as you learn more about ggplot2 you’ll construct increasingly sophisticated plots by adding on more types of components.

``
ggplot(mpg, aes(x = displ, y = hwy)) + geom_point()
``


__Almost every plot maps a variable to x and y, and naming these aesthetics is tedious, so the first two unnamed arguments to aes() will be mapped to x and y.This means that the following code is identical to the example above:__


``
ggplot(mpg, aes(displ, hwy)) + geom_point()
``

When you run either of the above commands, you will see this:  
<img src="/pics/example1.png" width="400">  

## Lets get festive! One more fun plot!
 
