2024/03/29 15:16
Status: #idea
Tags: [[Lesson 24 - t-tests]]

# Sample Standard Deviation

Is the square root of the sum of each value - the sample mean squared and divided by n-1


$$s=\sqrt{\frac{\sum\limits(x_i-\bar{x})^2}{n-1}}$$

## Degrees of Freedom

**In the context of sample standard deviation can be thought of as the number of values in a calculation that are free to vary.**

Example: 

- Imagine you're trying to figure out the average height in a room of 5 people. After finding the average, if you know the heights of 4 people, you could calculate the 5th person's height based on the average you already have. In this sense, only 4 of those heights are "free" to vary if the average is to remain constant. The 5th height is determined by the first 4 and the average.

*When calculating sample std deviation, we use $n-1$ (where $n$ is the number of observations in the sample) as the degrees of freedom*

As the number of degrees of freedom increases the t distribution begins to look more and more like the normal distribution

---
# References
