2024/04/13 14:41
Status: #idea
Tags: [[Lesson 24 - t-tests]]

## Full One-Sample t-test 

*Taken from Udacity Course! Imagine that this average represented the entire population.*

**US families spent an average of $151 per week on food in 2012**

- Food Now wants to implement a cost-saving program to reduce the average through different methods.

### Type of t-test to choose

- one-tailed in positive direction
- <mark style="background: #FFF3A3A6;">one-tailed in negative direction</mark>
- two-tailed
- three-tailed

**Choose one-tailed in negative direction because we want the sample's average to be lower than the population.**

## Calculated Values

- $df:\ n-1 = 24$
- $\Delta:\ \bar{x}-\mu=-\$25$
- $SEM:\ \frac{s}{\sqrt{n}} = 10$
- $t_{statistic}:\ \frac{\bar{x}-\mu_0}{s/\sqrt{n}}=-2.5$
- $Cohen's D:\ \frac{\Delta}{s}=-\frac{1}{2}$
- $r^{2}: \frac{t^{2}}{t^{2}+df}=0.21$

- $MoE:\ z\frac{s}{\sqrt{n}} = 2.064*10 = 20.64$
*where z is the t-critical value for a 2-tailed test with CI of 95%*

- $CI: Around sample mean$
	- $lower\ limit:\ (105.36, 126)$
	- $upper\ limit:\ (126, 146.64)$
### Variables 

- Dependent Var: The amount of money spent on food per week.

- Treatment: Cost-Saving Program

- $H_{0}\ (Null\ Hypothesis)$: The program did not change the cost of food
	- $H_0:$ $\bar{x} >= \mu$

- $H_{a}\ (Alt.\ Hypothesis)$: The program reduced the cost of food.
	- $H_a:$ $\bar{x} < \mu$

- $\mu$ : Population mean, \$151
- $\bar{x}$: Sample mean, average cost per week at Food Now, $126.
- $\Delta:\ Mean\ Difference, -\$25$
- $s:$ Sample standard deviation, $50
- $SEM$: Standard Error, 10
- $n$: Sample size, 25.
- $df$: Degrees of freedom, 24.
- $\alpha$: Significance level, 0.05.
- $t_{critical}\ :$ Critical value for t, -1.711 (For one-tailed in negative direction).

- $p-value:$![[Pasted image 20240413151545.png]]


---
# References

- [[Null and Alternative Hypothesis]]
- [[One and Two-Tailed Tests Using Alpha Levels]]
- [[Standard Deviation]]
- [[Sample Standard Deviation]]
- [[Standard Error]]
- [[T-Table]]
- [[T-Statistic]]
- [[Confidence Interval]]
- [[Margin of Error]]
- [[Coefficient of Determination]]