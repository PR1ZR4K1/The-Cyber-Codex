


## As you begin...

You should load this .Rmd file into RStudio or RStudio.cloud. You may find it easier to read if you Knit it first rather than reading the .Rmd file itself. You should have learned how to do these in the [Intro_to_rstudio](https://senanu.github.io/b40/docs/labs/R/intro_to_rstudio.html) and [Intro_to_r](https://senanu.github.io/b40/docs/labs/R/intro_to_r.html) assignments.

If you are having trouble finding the output of your R commands (ie. when you click the green arrow to run a code chunk), this may help: go to the tools menu, choose 'Global options', then in the 'R markdown' menu, UNCHECK the box labeled "Show output inline for all R Markdown documents". This will tell RStudio to put the plot into the viewer sub-window.

# Determining the salt concentration inside cells

```{r setup, include=TRUE, echo=FALSE}
knitr::opts_knit$set(global.device = TRUE) # leave this alone
```

## Import your data into R

1.  Save the data that you collected in your lab manual into a Google spreadsheet **in exactly the same form as in the manual**. In particular, pay attention to the column headings -- I suggest you type them exactly as shown.
2.  Publish your Google spreadsheet as a `.csv` file.
3.  Get your data into R according to methods you learned in previous weeks (use the `read.csv()` command). Save it in a variable called `dat`.
4.  Check that your data looks like you expect. Remember that you can view it by typing the data frame's name (`dat`) on a line of its own.
5.  Once your code runs by pressing the green arrow on the top right, change the `eval=FALSE` to `eval=TRUE`. This will allow the knitting engine to access it so it can be knitted into a final document at the end.

```{r data-import, eval=FALSE, include=TRUE, echo=TRUE}
dat <-
```

# Calculate the % change in weight

Convert your data to represent the percent change in weight. Doing this allows us to have some variation in the weight of the potato core. We will use this formula, but we will ask R to do the work for us! $${{(final\ weight - original\ weight)}\over original\ weight} \times 100 = percent\ weight\ change$$

6.  Get R to do this for you. Save the result in a variable called `percent.change`. If your data table looks exactly like the one in the lab manual (which is highly recommended), then the variables will be called `dat$original.weight` and `dat$final.weight` ([don't include quotes around these objects](https://senanu.github.io/b40/docs/labs/R/r_faq.html#objects-and-quotes-in-r)). Make sure you are careful with precedence -- that is make sure that you use parentheses to tell R which part of the equation you want done first, second, etc. You should also know that the asterix (\*) is the multiplication operator, so you can say `dat$columnA * dat$columnB`. Similarly, the forward slash (/) is for division.
7.  Once your code runs by pressing the green arrow on the top right, change the `eval=FALSE` to `eval=TRUE`.

```{r percent-change, eval=FALSE, include=TRUE, echo=TRUE}
percent.change <-
```

What do you think will be the sign (positive or negative) for potatoes that gained weight? Lost weight? It is important to do this type of mental calculation to make sure that your calculations are doing what you expect them to do. In fact, I recommend doing a single calculation by hand to make sure you got it right.

Your percent change data is now stored as a 'vector' in R. However, it is often easier to 'bind' the column to the original table so that it is part of that table. This command combines 'dat' with 'percent.change' into the variable 'dat'. After doing this, you can refer to it as `dat$percent.change`.

8.  Once your code runs by pressing the green arrow on the top right, change the `eval=FALSE` to `eval=TRUE`.

```{r cbind,  eval=FALSE, include=TRUE, echo=TRUE}
# If your variable names are the same as recommended, you shouldn't need to do anything with this code chunk.
dat <- cbind(dat, percent.change)
```

# Linear regression of data

We can expect that the percent change will be approximately linear with the solution concentration. Therefore, we can do a linear regression. For this, we will use a special R formula using a tilde (\~). The tilde means "is explained by" so `lm(y ~ x)` means that the variable `y` is explained by `x`. In this case, we can read the tilde as part of a formula meaning "percent change is explained by the concentration of the solution". `lm` is the command ('verb') to conduct a 'linear model' regression.

9.  Once your code runs by pressing the green arrow on the top right, change the `eval=FALSE` to `eval=TRUE`.

```{r regression,  eval=FALSE, include=TRUE, echo=TRUE}
# If you used the suggested variable names, you shouldn't need to do anything here.
lin.regression <- lm(dat$percent.change ~ dat$solution)
```

10.  Plot your data. Think about which variable should be on the x-axis and which on the y-axis. Remember, you can refer to them as `dat$solution` and `dat$percent.change`.
11.  Add the necessary pieces to the `plot()` code below. Also adjust the axis and main titles.
12.  Once your code runs by pressing the green arrow on the top right, change the `eval=FALSE` to `eval=TRUE`.

```{r graph,  eval=FALSE, include=TRUE, echo=TRUE}
plot(x=     ,
     y=     ,
     main="Title goes here",
     xlab="x-axis label",
     ylab="y-axis label")
abline(lin.regression)
```

We want to calculate the point on the x-axis where the linear regression crosses that axis (ie. where $y=0$). You can see the basics of the regression just by typing `lin.regression` on a line of its own, or you can see a whole lot of details with `summary(lin.regression)`. Remember that we used this step in the Protein lab, so please refer back to that if necessary.

```{r summary, eval=TRUE, include=TRUE, echo=TRUE}
# Use this space to see the regression (m and b in Y=mX+b)
```

Answer the questions below.

# What to turn in

13.  You will turn in a knitted version of this document. Make sure all of the places where I've asked you to change "eval=FALSE" to "eval=TRUE" have been changed, otherwise you won't get the right output, and there won't be a graph. I will be looking for your graph, which should have a line on it and have labeled axes.

14.  What is the equation for your straight line?

    Replace this text with your answer. For nice formatting, leave the 4 spaces at the beginning of this paragraph, and separate it from the other paragraphs by a blank line above and below.

15.  What value on the X-axis does the regression line cross the X-axis? In other words, What is $X$ when $Y = 0$?

    Replace this text with your answer. For nice formatting, leave the 4 spaces at the beginning of this paragraph, and separate it from the other paragraphs by a blank line above and below.

16.  What is **Biologically** significant about this point? ie. what does this tell us about the tonicity of the potato cells?

    Replace this text with your answer. For nice formatting, leave the 4 spaces at the beginning of this paragraph, and separate it from the other paragraphs by a blank line above and below.
