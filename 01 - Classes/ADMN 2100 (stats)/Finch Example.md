2024/03/30 16:56
Status: #idea
Tags: [[Lesson 24 - t-tests]], [[Null and Alternative Hypothesis]]

# Finch Example

Objective:

**Calculate t-Statistic for a [[Null and Alternative Hypothesis]]**

Imagine over the past 2 years we have an average beak width of finches (a type of bird) that is **6.07 mm**

Question:

*Do finches today have different-sized beak widths than before?*

## Define known Vars

#### Hypothesized Population Mean

$\mu_{0}= 6.07$
#### Hypothesis (null and alternate)

First, select the appropriate alternate hypothesis statement from these choices:


$H_{0}: \mu = \mu_{0}$

$H_{a}:$ $\mu \lt \mu_{0}$
    $\mu \gt \mu_{0}$
     $\mu \ne \mu_{0}$


Based on the question the appropriate hypotheses are:

$H_{0}: \mu = \mu_{0}$
$H_{a}: \mu \ne \mu_{0}$

#### Find sample size (n) and degrees of freedom (n - 1)

n = 500
df = 499

#### Sample mean $\bar{x}$ 

$\bar{x}: 6.47$

#### Sample Standard Deviation $s$

$$s=\sqrt{\frac{\sum\limits(x_i-\bar{x})^2}{n-1}}$$
$s\approx 0.4$


#### t-Statistic

$$t =\frac{\bar{x}-\mu_0}{s/\sqrt{n}}$$

$$t = \frac{6.47-6.07}{0.4/\sqrt{500}}$$

$t = 22.36$


---
# References

- https://docs.google.com/spreadsheet/ccc?key=0Alo47BBiqLE0dEQ3UmVCc0tsRzBmNER1UVFzMG1MN3c&usp=sharing (finch data)
- [[Sample Standard Deviation]]
- [[T-Statistic]]