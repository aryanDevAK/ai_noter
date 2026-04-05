# Lecture 1: Mean

## 1. Why This Concept Matters

If a cricket player scores 50, 100, 0, 10, and 90 runs in five consecutive matches, how do we judge their overall performance? We cannot just look at the 100 and say they are always brilliant, nor can we look at the 0 and call them terrible. We need a single number that represents their "typical" or "average" performance.

In economics, when we talk about the "per capita income" of a country, we are talking about the mean. When a machine learning model predicts the average price of a house in a city based on historical data, it relies fundamentally on the mathematics of the mean. The mean allows us to compress large, complex datasets into a single, digestible summary number. It is the center of gravity for data.

## 2. Understanding the Idea Intuitively

Think of the mean as the concept of "fair share."

Imagine three friends have 2, 5, and 8 chocolates, respectively. They decide to pool all their chocolates together and then divide them equally so everyone has the exact same amount.
Total chocolates = 2 + 5 + 8 = 15.
Divided among 3 friends = 15 / 3 = 5 chocolates each.

This "fair share" value of 5 is the arithmetic mean.

Another way to think of the mean is as a physical **balancing point** (or center of mass) on a seesaw. If you place weights on a number line at positions 2, 5, and 8, the seesaw will perfectly balance if you place the fulcrum exactly at 5.

## 3. Observing Patterns From Data

Let's look at the daily pocket money of 4 students: ₹20, ₹30, ₹40, and ₹70.

To find the central value, we first combine everything:
Total Pool = 20 + 30 + 40 + 70 = ₹160.

Now, distribute this pool equally among the 4 students:
Equal Share = 160 / 4 = ₹40.

The mean pocket money is ₹40. Notice how the mean is influenced by every single value in the dataset. If the last student had ₹110 instead of ₹70, the total pool would be larger, and the mean would shift upwards.

## 4. Rule for Finding the Concept

The rule for calculating the mean depends on how the data is presented to us.

### A. For Raw/Ungrouped Data

If we have $n$ individual observations: $x_1, x_2, x_3, \dots, x_n$

**Formula:**
$$\bar{x} = \frac{x_1 + x_2 + \dots + x_n}{n} = \frac{\sum x_i}{n}$$

### B. For Ungrouped Frequency Distribution (Weighted Mean Intuition)

When certain values repeat, we use frequencies ($f_i$) instead of adding them multiple times.

**Formula:**
$$\bar{x} = \frac{f_1x_1 + f_2x_2 + \dots + f_nx_n}{f_1 + f_2 + \dots + f_n} = \frac{\sum f_ix_i}{\sum f_i}$$

### C. For Grouped Data (Continuous Distribution)

For class intervals (e.g., 10-20), we find the class mark ($x_i$) which is the midpoint of the interval. Then we can use one of three methods:

**1. Direct Method:**
$$\bar{x} = \frac{\sum f_ix_i}{\sum f_i}$$

**2. Assumed Mean Method (Shortcut Method):**
Used when $x_i$ and $f_i$ are large numbers. We assume an arbitrary mean '$a$' from the middle of the $x_i$ column.
$$\bar{x} = a + \frac{\sum f_id_i}{\sum f_i}$$
where $d_i = x_i - a$ (deviation from assumed mean).

**3. Step-Deviation Method:**
Used when the class sizes ($h$) are equal. It simplifies calculations further.
$$\bar{x} = a + \left( \frac{\sum f_iu_i}{\sum f_i} \right) \times h$$
where $u_i = \frac{x_i - a}{h}$.

| Symbol        | Meaning                                         |
| :------------ | :---------------------------------------------- |
| **$\bar{x}$** | Arithmetic Mean (read as "x bar")               |
| **$\sum$**    | Sigma (Summation of)                            |
| **$x_i$**     | Individual observation or Class Mark (midpoint) |
| **$f_i$**     | Frequency of the $i^{th}$ observation           |
| **$a$**       | Assumed Mean                                    |
| **$d_i$**     | Deviation ($x_i - a$)                           |
| **$u_i$**     | Step deviation ($(x_i - a)/h$)                  |
| **$h$**       | Class size / Class width                        |

## 5. Step-by-Step Method

**Algorithm for Grouped Data (Assumed Mean Method):**

1. **Class Mark ($x_i$):** Create a new column for the midpoint of each class interval. $x_i = \frac{\text{Upper Limit} + \text{Lower Limit}}{2}$.
2. **Choose '$a$':** Select a value near the middle of the $x_i$ column to be your Assumed Mean ($a$).
3. **Deviations ($d_i$):** Create a column for $d_i$ by subtracting '$a$' from every $x_i$ value ($d_i = x_i - a$).
4. **Product ($f_id_i$):** Multiply each frequency $f_i$ by its corresponding $d_i$.
5. **Summation:** Find the sum of all frequencies ($\sum f_i$) and the sum of the products ($\sum f_id_i$).
6. **Apply Formula:** Plug the values into $\bar{x} = a + \frac{\sum f_id_i}{\sum f_i}$.

## 6. Visual Understanding

**Diagram 1: Data Flow for Arithmetic Mean**

```text
  [ Dataset Values ]
    2, 5, 8, 9, 11
          |
          v
   [ Total Sum ]
    (2+5+8+9+11) = 35
          |
          v
 [ Divide by Count ]
       (n = 5)
          |
          v
   [ Arithmetic Mean ]
     35 / 5 = 7
```

**Diagram 2: Mean as a Physical Balancing Point (Center of Mass)**

```text
      Values:     2         5         8
                  |         |         |
      Weights:   [x]       [x]       [x]
Number Line: --+--+--+--+--+--+--+--+--+--+--
               1  2  3  4  5  6  7  8  9  10
                           ^
                           |
                        FULCRUM
                       (Mean = 5)
The distance of 2 from 5 is 3 units left (-3).
The distance of 8 from 5 is 3 units right (+3).
The sum of deviations from the mean is always ZERO (-3 + 0 + 3 = 0).
```

## 7. Solved Examples

### Example 1 — Basic

**Problem:** Find the mean of the first 5 prime numbers.
**Solution steps:**

1. Identify the first 5 prime numbers: 2, 3, 5, 7, 11.
2. Count the number of observations ($n$): 5.
3. Calculate the sum of observations ($\sum x_i$): 2 + 3 + 5 + 7 + 11 = 28.
4. Apply the formula for raw data: $\bar{x} = \frac{\sum x_i}{n} = \frac{28}{5}$.
5. $\bar{x} = 5.6$.
   **Final answer:** 5.6

### Example 2 — Moderate

**Problem:** The mean of 5 numbers is 18. If one number is excluded, their mean becomes 16. Find the excluded number.
**Solution steps:**

1. Mean of 5 numbers = 18.
   Therefore, Sum of 5 numbers = $5 \times 18 = 90$.
2. When one number is excluded, 4 numbers remain.
   New mean of 4 numbers = 16.
   Sum of these 4 numbers = $4 \times 16 = 64$.
3. Excluded number = (Sum of 5 numbers) - (Sum of 4 numbers).
   Excluded number = 90 - 64 = 26.
   **Final answer:** 26

### Example 3 — Advanced

**Problem:** Find the mean of the following frequency distribution using the Assumed Mean Method.

| Class Interval    | 0-10 | 10-20 | 20-30 | 30-40 | 40-50 |
| :---------------- | :--- | :---- | :---- | :---- | :---- |
| Frequency ($f_i$) | 7    | 8     | 12    | 13    | 10    |

**Solution steps:**

1. Construct the computation table. Let assumed mean $a = 25$.

| Class Interval | $f_i$               | $x_i$ (Midpoint) | $d_i = x_i - 25$ | $f_id_i$                |
| :------------- | :------------------ | :--------------- | :--------------- | :---------------------- |
| 0-10           | 7                   | 5                | -20              | -140                    |
| 10-20          | 8                   | 15               | -10              | -80                     |
| 20-30          | 12                  | **25** ($a$)     | 0                | 0                       |
| 30-40          | 13                  | 35               | 10               | 130                     |
| 40-50          | 10                  | 45               | 20               | 200                     |
| **Total**      | **$\sum f_i = 50$** |                  |                  | **$\sum f_id_i = 110$** |

2. Apply the Assumed Mean formula: $\bar{x} = a + \frac{\sum f_id_i}{\sum f_i}$
3. Substitute the values: $\bar{x} = 25 + \frac{110}{50}$
4. Simplify: $\bar{x} = 25 + 2.2 = 27.2$.
   **Final answer:** 27.2

## 8. Interpretation in Data Science

In data science, the mean is ubiquitous but must be used with extreme caution.

- **Sensitivity to Outliers:** The mean incorporates every single data point. If you have an income dataset of `[30k, 40k, 50k, 60k]` the mean is 45k. If a billionaire is added `[30k, 40k, 50k, 60k, 100000k]`, the new mean skyrockets to ~20000k. The mean is highly sensitive to extreme values (outliers).
- **Skewed Datasets:** Because of outlier sensitivity, the mean is a poor metric for heavily skewed distributions (like wealth, house prices, or YouTube views). In right-skewed data, the mean is pulled sharply to the right.
- **Preprocessing and Normalization:** In machine learning, algorithms (like Neural Networks or SVMs) prefer data centered around zero. We use the mean for **Standardization (Z-score normalization)**: $z = \frac{x - \mu}{\sigma}$. We subtract the dataset's mean from every feature to center the data at 0.
- **Imputation (Feature Engineering):** When datasets have missing values (NaNs), a common baseline technique is to replace the missing values with the column's mean (Mean Imputation), provided the feature is symmetrically distributed.

## 9. Comparison With Other Measures

| Feature                     | Mean                                                           | Median                             | Mode                                              |
| :-------------------------- | :------------------------------------------------------------- | :--------------------------------- | :------------------------------------------------ |
| **Mathematical Definition** | Sum divided by count                                           | The middle positional value        | Most frequently occurring value                   |
| **Outlier Sensitivity**     | **Extremely High**                                             | Zero / Robust                      | Zero                                              |
| **Uses all data points?**   | **Yes**                                                        | No                                 | No                                                |
| **Best used for**           | Symmetric, clean, continuous data (e.g., heights, test scores) | Skewed data (incomes, real estate) | Categorical data (shoe sizes, most popular color) |
| **Algebraic manipulation**  | **Highly capable** (used in variance, standard deviation)      | Not capable                        | Not capable                                       |

## 10. Exam Strategy Box

> 💡 Exam Tip: Always check if the class intervals are continuous (e.g., 0-10, 10-20). If they are discontinuous (e.g., 1-10, 11-20), convert them to continuous boundaries (0.5-10.5, 10.5-20.5) before finding the class mark $x_i$, although $x_i$ remains mathematically the same either way.
> 💡 Exam Tip: For 1-mark questions, if the mean of $n$ observations is $\bar{x}$, and you add/subtract/multiply/divide every observation by a constant $k$, the new mean is simply $\bar{x} \pm k$ or $\bar{x} \times k$.
> 💡 Exam Tip: Do not waste time using the Step-Deviation method if the frequencies and midpoints are single-digit numbers; the Direct Method will be faster.
> 💡 Exam Tip: The sum of the deviations of all observations from their arithmetic mean is always exactly zero: $\sum (x_i - \bar{x}) = 0$.
> 💡 Exam Tip: When choosing an assumed mean '$a$', pick the $x_i$ value that corresponds to the highest frequency near the center to make your $f_id_i$ calculations as small as possible.

## 11. Common Student Errors

> ⚠️ Common Error: Dividing by the number of classes instead of the total frequency ($\sum f_i$) in grouped data problems.
> ⚠️ Common Error: Adding the class intervals together to find $\sum f_i$. Always sum the _frequency_ column, not the variable column.
> ⚠️ Common Error: Messing up negative signs in the Assumed Mean method. Remember that values smaller than '$a$' will have negative $d_i$ values.
> ⚠️ Common Error: Forgetting to multiply by the class size ($h$) at the very end when using the Step-Deviation method.
> ⚠️ Common Error: Writing the final answer as a fraction instead of converting it to a decimal. Board exams generally prefer answers rounded to two decimal places.

## 12. Practice Exercises (NCERT + Competitive Exam Style)

### Section A: Very Short Answer (1-2 marks)

1. Find the mean of the first 10 natural numbers.
2. The mean of 6, 8, $x$, 12, and 14 is 10. Find the value of $x$.
3. If the mean of 10 observations is 15, what is the sum of all the observations?
4. If every value in a dataset with a mean of 40 is multiplied by 2 and then increased by 5, what is the new mean?
5. What is the algebraic sum of deviations of a frequency distribution from its mean?

### Section B: Short Answer (2-3 marks)

6. The mean weight of 8 students is 45 kg. If a 9th student weighing 54 kg joins the group, what is the new mean weight?
7. The mean of 20 numbers is 18. If 3 is subtracted from each of the first 10 numbers, find the new mean of the 20 numbers.
8. Find the mean of the following distribution:
   $x_i$: 5, 10, 15, 20, 25
   $f_i$: 2, 5, 6, 4, 3
9. The mean of 50 observations was found to be 36. Later it was discovered that one observation, 48, was wrongly read as 23. Find the correct mean.
10. The average salary of 15 male employees is ₹5000 and that of 10 female employees is ₹4000. Find the combined mean salary of all 25 employees.

### Section C: Exam Level Problems (4-5 marks)

11. Calculate the mean of the following data using the Direct Method:
    Classes: 10-20, 20-30, 30-40, 40-50, 50-60
    Frequency: 4, 7, 10, 6, 3
12. Find the missing frequency '$p$' if the mean of the following distribution is 24:
    Classes: 0-10, 10-20, 20-30, 30-40, 40-50
    Frequency: 3, 4, $p$, 3, 2
13. Find the mean of the following data using the Assumed Mean method:
    Classes: 100-120, 120-140, 140-160, 160-180, 180-200
    Frequency: 12, 14, 8, 6, 10
14. The following table gives the literacy rate of 35 cities. Find the mean literacy rate using the step-deviation method.
    Literacy rate (%): 45-55, 55-65, 65-75, 75-85, 85-95
    Number of cities: 3, 10, 11, 8, 3
15. The mean of the following frequency distribution is 50. Find the missing frequencies $f_1$ and $f_2$ if the sum of all frequencies is 120.
    Classes: 0-20, 20-40, 40-60, 60-80, 80-100
    Frequency: 17, $f_1$, 32, $f_2$, 19

### Section D: Conceptual Reasoning (For Data Science & Advanced Competitions)

16. Why does replacing missing values with the column mean (Mean Imputation) artificially reduce the variance (spread) of a dataset?
17. A startup has 10 employees. 9 earn ₹40,000, and the CEO earns ₹4,000,000. Why is the mean a bad metric for an HR report here, and what is a better alternative?
18. Prove conceptually that $\sum (x_i - \bar{x}) = 0$. What does this imply physically?
19. If you scale a dataset (e.g., convert temperatures from Celsius to Fahrenheit $F = 1.8C + 32$), does the mean undergo the exact same transformation? Why?
20. In what specific scenario would the arithmetic mean and the median of a dataset be exactly equal?

## 13. Fully Solved Answers

### Section A

**1. Solution:** First 10 natural numbers: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10.
Sum = $\frac{n(n+1)}{2} = \frac{10 \times 11}{2} = 55$. Mean = $\frac{55}{10} = 5.5$.
**Final Answer:** 5.5.

**2. Solution:** Mean = 10. $n = 5$. Sum = $5 \times 10 = 50$.
$6 + 8 + x + 12 + 14 = 50 \Rightarrow 40 + x = 50 \Rightarrow x = 10$.
**Final Answer:** 10.

**3. Solution:** Sum = Mean $\times$ Total observations = $15 \times 10 = 150$.
**Final Answer:** 150.

**4. Solution:** By the property of means, if $y = ax + b$, then $\bar{y} = a\bar{x} + b$.
New mean = $(40 \times 2) + 5 = 80 + 5 = 85$.
**Final Answer:** 85.

**5. Solution:** The algebraic sum of deviations from the mean is always zero.
**Final Answer:** 0.

### Section B

**6. Solution:**
Original sum of 8 students = $8 \times 45 = 360$ kg.
New sum with 9th student = $360 + 54 = 414$ kg.
New mean = $\frac{414}{9} = 46$ kg.
**Final Answer:** 46 kg.

**7. Solution:**
Original sum of 20 numbers = $20 \times 18 = 360$.
Total subtracted amount = $10 \times 3 = 30$.
New sum = $360 - 30 = 330$.
New mean = $\frac{330}{20} = 16.5$.
**Final Answer:** 16.5.

**8. Solution:**

| $x_i$   | $f_i$           | $f_ix_i$            |
| :------ | :-------------- | :------------------ |
| 5       | 2               | 10                  |
| 10      | 5               | 50                  |
| 15      | 6               | 90                  |
| 20      | 4               | 80                  |
| 25      | 3               | 75                  |
| **Sum** | $\sum f_i = 20$ | $\sum f_ix_i = 305$ |

Mean = $\frac{305}{20} = 15.25$.
**Final Answer:** 15.25.

**9. Solution:**
Incorrect Sum = $50 \times 36 = 1800$.
Correct Sum = Incorrect Sum - Wrong Item + Correct Item = $1800 - 23 + 48 = 1825$.
Correct Mean = $\frac{1825}{50} = 36.5$.
**Final Answer:** 36.5.

**10. Solution:**
Combined Mean $\bar{x}_{12} = \frac{n_1\bar{x}_1 + n_2\bar{x}_2}{n_1 + n_2}$
Sum of male salaries = $15 \times 5000 = 75000$.
Sum of female salaries = $10 \times 4000 = 40000$.
Total sum = $115000$. Total employees = 25.
Combined Mean = $\frac{115000}{25} = 4600$.
**Final Answer:** ₹4600.

### Section C

**11. Solution:**

| Class   | $x_i$ | $f_i$           | $f_ix_i$             |
| :------ | :---- | :-------------- | :------------------- |
| 10-20   | 15    | 4               | 60                   |
| 20-30   | 25    | 7               | 175                  |
| 30-40   | 35    | 10              | 350                  |
| 40-50   | 45    | 6               | 270                  |
| 50-60   | 55    | 3               | 165                  |
| **Sum** |       | $\sum f_i = 30$ | $\sum f_ix_i = 1020$ |

Mean = $\frac{1020}{30} = 34$.
**Final Answer:** 34.

**12. Solution:**

| Class   | $x_i$ | $f_i$  | $f_ix_i$    |
| :------ | :---- | :----- | :---------- |
| 0-10    | 5     | 3      | 15          |
| 10-20   | 15    | 4      | 60          |
| 20-30   | 25    | $p$    | $25p$       |
| 30-40   | 35    | 3      | 105         |
| 40-50   | 45    | 2      | 90          |
| **Sum** |       | $12+p$ | $270 + 25p$ |

Given Mean = 24.
$24 = \frac{270 + 25p}{12 + p}$
$24(12 + p) = 270 + 25p \Rightarrow 288 + 24p = 270 + 25p$
$288 - 270 = 25p - 24p \Rightarrow p = 18$.
**Final Answer:** $p = 18$.

**13. Solution:**
Let Assumed Mean $a = 150$.

| Class   | $f_i$           | $x_i$ | $d_i = x_i - 150$ | $f_id_i$             |
| :------ | :-------------- | :---- | :---------------- | :------------------- |
| 100-120 | 12              | 110   | -40               | -480                 |
| 120-140 | 14              | 130   | -20               | -280                 |
| 140-160 | 8               | 150   | 0                 | 0                    |
| 160-180 | 6               | 170   | 20                | 120                  |
| 180-200 | 10              | 190   | 40                | 400                  |
| **Sum** | $\sum f_i = 50$ |       |                   | $\sum f_id_i = -240$ |

$\bar{x} = a + \frac{\sum f_id_i}{\sum f_i} = 150 + (\frac{-240}{50}) = 150 - 4.8 = 145.2$.
**Final Answer:** 145.2.

**14. Solution:**
Class size $h = 10$. Let Assumed Mean $a = 70$.

| Class   | $f_i$           | $x_i$    | $u_i = \frac{x_i - 70}{10}$ | $f_iu_i$           |
| :------ | :-------------- | :------- | :-------------------------- | :----------------- |
| 45-55   | 3               | 50       | -2                          | -6                 |
| 55-65   | 10              | 60       | -1                          | -10                |
| 65-75   | 11              | 70 ($a$) | 0                           | 0                  |
| 75-85   | 8               | 80       | 1                           | 8                  |
| 85-95   | 3               | 90       | 2                           | 6                  |
| **Sum** | $\sum f_i = 35$ |          |                             | $\sum f_iu_i = -2$ |

$\bar{x} = a + (\frac{\sum f_iu_i}{\sum f_i}) \times h = 70 + (\frac{-2}{35}) \times 10 = 70 - \frac{20}{35} = 70 - 0.57 = 69.43$.
**Final Answer:** 69.43%.

**15. Solution:**

| Class   | $x_i$ | $f_i$                   | $f_ix_i$                         |
| :------ | :---- | :---------------------- | :------------------------------- |
| 0-20    | 10    | 17                      | 170                              |
| 20-40   | 30    | $f_1$                   | $30f_1$                          |
| 40-60   | 50    | 32                      | 1600                             |
| 60-80   | 70    | $f_2$                   | $70f_2$                          |
| 80-100  | 90    | 19                      | 1710                             |
| **Sum** |       | $\sum f_i = 68+f_1+f_2$ | $\sum f_ix_i = 3480+30f_1+70f_2$ |

Given $\sum f_i = 120 \Rightarrow 68 + f_1 + f_2 = 120 \Rightarrow f_1 + f_2 = 52$ --- (Eq 1)
Given Mean = 50.
$50 = \frac{3480 + 30f_1 + 70f_2}{120}$
$6000 = 3480 + 30f_1 + 70f_2 \Rightarrow 2520 = 30f_1 + 70f_2$
Divide by 10: $3f_1 + 7f_2 = 252$ --- (Eq 2)
From Eq 1, $f_1 = 52 - f_2$. Substitute in Eq 2:
$3(52 - f_2) + 7f_2 = 252 \Rightarrow 156 - 3f_2 + 7f_2 = 252$
$4f_2 = 96 \Rightarrow f_2 = 24$.
Then $f_1 = 52 - 24 = 28$.
**Final Answer:** $f_1 = 28, f_2 = 24$.

### Section D

**16. Solution:** Variance measures how spread out data points are from the mean. By replacing missing values with the exact mean itself, you are adding points with zero spread (deviation = 0). This dilutes the overall spread of the data, artificially clustering the distribution closer to the center than it naturally is.
**17. Solution:** The CEO's extreme salary is an outlier that pulls the mean upwards dramatically. The mean salary would be roughly ₹436,000, which is over 10x what 90% of the company actually earns. It is highly misleading. The Median (₹40,000) is a much better, robust metric for typical pay.
**18. Solution:** $\sum (x_i - \bar{x}) = \sum x_i - \sum \bar{x} = n\bar{x} - n\bar{x} = 0$. Physically, this means the mean acts as the exact center of gravity/mass of the dataset. The total "pull" of the values above the mean perfectly cancels out the total "pull" of the values below it.
**19. Solution:** Yes, the mean is affected by both changes in scale (multiplication) and changes in origin (addition). Since the transformation is linear ($y = mx + c$), the mean transforms exactly the same way: $\bar{F} = 1.8\bar{C} + 32$.
**20. Solution:** They are exactly equal when the dataset's distribution is perfectly symmetrical (e.g., a perfect normal distribution curve like `[10, 20, 30, 40, 50]`). There is no skewness to pull the mean away from the median center.

## 14. Real Dataset Example

**Dataset Context: House Prices in a Neighborhood**
Let's analyze the prices of 5 houses recently sold in a suburban neighborhood.
Prices (in ₹ Crores): `1.0, 1.2, 1.1, 1.3, 10.4`

**Mean Calculation:**
Sum = $1.0 + 1.2 + 1.1 + 1.3 + 10.4 = 15.0$ Cr.
Mean = $\frac{15.0}{5} = \textbf{₹ 3.0 Cr}$.

**Interpretation:**
The arithmetic mean suggests the average house price is ₹3.0 Cr. However, looking at the data, 4 out of 5 houses cost around ₹1.1 Cr. The ₹10.4 Cr house is a massive luxury mansion (an outlier). This demonstrates the primary weakness of the mean in data science: **it is highly sensitive to extreme values.** In business dashboards for real estate, displaying this mean would mislead buyers into thinking the neighborhood is unaffordable.

## 15. Quick Revision Sheet

- **Definition:** The arithmetic average; sum of values divided by count.
- **Formula (Raw):** $\bar{x} = \frac{\sum x_i}{n}$
- **Formula (Direct Grouped):** $\bar{x} = \frac{\sum f_ix_i}{\sum f_i}$
- **Formula (Assumed Mean):** $\bar{x} = a + \frac{\sum f_id_i}{\sum f_i}$
- **Key Property 1:** The sum of deviations from the mean is 0.
- **Key Property 2:** If $y_i = a \cdot x_i + b$, then $\bar{y} = a \cdot \bar{x} + b$.
- **Weakness:** Severely distorted by outliers and skewed data.
- **Data Science Use:** Used heavily for feature scaling (Z-score standardization) and base imputation for symmetric data.

## 16. Interview & Data Science Questions

### Beginner

**Q:** How do you handle missing values in a machine learning dataset containing human heights?
**A:** Because human height follows a symmetric normal distribution with few extreme outliers, replacing missing values with the column's mean (Mean Imputation) is a safe and standard approach.

### Intermediate

**Q:** Why do we use Mean Squared Error (MSE) instead of Mean Absolute Error (MAE) in training regression models?
**A:** While both rely on the mean of errors, MSE squares the differences, which punishes large outliers much more heavily than MAE. Furthermore, squaring makes the cost function smooth and differentiable everywhere, which is mathematically necessary for gradient descent optimization algorithms.

### Advanced

**Q:** Explain the impact of standardization ($z = (x - \mu)/\sigma$) on the arithmetic mean of a feature.
**A:** Standardization guarantees that the new arithmetic mean of the transformed feature will be exactly zero. By subtracting the original mean ($\mu$) from every point, the entire distribution shifts along the number line so that its center of mass now perfectly balances at the origin (0).

## 17. Mini Quiz

**1. The mean of 11 observations is 50. If the first 6 observations have a mean of 49 and the last 6 observations have a mean of 52, what is the 6th observation?**
A) 56
B) 50
C) 48
D) 45

**2. Which measure of central tendency is calculated by considering the magnitude of every single item in the series?**
A) Mode
B) Median
C) Arithmetic Mean
D) Range

**3. In the assumed mean method formula $\bar{x} = a + \frac{\sum f_id_i}{\sum f_i}$, what does $d_i$ represent?**
A) $f_i - a$
B) $x_i - a$
C) $a - x_i$
D) $x_i / a$

**4. A dataset contains house prices, heavily right-skewed by a few luxury mansions. Which metric will report the highest numerical value?**
A) Mean
B) Median
C) Mode
D) They will be equal

**5. If $\sum_{i=1}^{n} (x_i - 12) = 0$, then the arithmetic mean of the dataset is:**
A) 0
B) $12n$
C) 12
D) Cannot be determined

## Mini Quiz Answer Key

1. A
2. C
3. B
4. A
5. C
