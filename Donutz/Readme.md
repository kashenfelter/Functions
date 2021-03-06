# Functions

## Donutzz

`donutzz` is a function that uses ggplot2 to render donut sytle charts in a very simple way.

To load the `donutzz` function into your main environment directly from RStudio, run this code to create a simple function that loads other functions from git:

```
source_github <- function( url ) {
  # load package
  require(RCurl)
  
  # read script lines from website and evaluate
  script <- getURL(url, ssl.verifypeer = FALSE)
  eval(parse(text = script), envir=.GlobalEnv)
} 

#load the donutzz function using the RAW link
source_github("https://raw.githubusercontent.com/icps86/Functions/master/donutzz.R")
```
Now `donutzz` is available in your global environment for use! 

These are the arguments (and their defualts) for the function:

donutzz <- function (x, lev, xlim = c(0,4), width.max=3, width.min=2, border="white", border.size =1.5,
                     main = "Your Title Here", mar = 1)

* x: the values for each category that will be represented in the donut. Has to be a positive numeric vector. 
* lev: the name of the categories. The function will work with levels of a factor class, but if you input a character vector it will also work. Note that the order of the names will be correlative to the order on the legend.
* width.max / width.min: determines the width of the donut. 
* border / border.size: Color and size of the border of the donut
* main: your title
* mar: changes the size of the x-axis in the plot box. This will interact with the width of the donut and change its size. 
 
Here is a code example to use the donutzz with a dataframe:
```
#Creating the DF
x <- data.frame(MGenre = c("Medieval Metal", "Doom Metal", "Symbolic Metal", "Metal Metal", "Mathematical metal"), Fans  = c(40, 90, 10, 20, 80), row.names = NULL)

# Create the donut chart
donutzz(x = x$Fans, lev = x$MGenre, main = "Composition of Thematic Metal Fans in Iowa" )
```
