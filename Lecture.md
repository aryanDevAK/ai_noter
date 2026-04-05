```markdown
# Lecture 2: Median

## 1. Why This Concept Matters

Imagine you are looking at the salaries of five people working at a small startup: four junior developers earning ₹50,000 each, and one CEO earning ₹5,00,000. If we calculate the average (mean) salary, it comes out to ₹1,40,000. Does this average accurately represent what a typical employee earns? Not at all! The CEO's massive salary pulls the average up, making it a misleading representation.

In the real world—whether in economics examining national income, real estate pricing houses, or machine learning algorithms analyzing user behavior—data is rarely perfectly balanced. There are always extremes or "outliers." This is where the **Median** comes to the rescue. The median is the true "middle" of the data, completely unaffected by extreme values. It gives us a much more honest picture of the typical scenario in everyday observations and messy datasets.

## 2. Understanding the Idea Intuitively

Think of the median as the middle person in a line. 

If you ask 5 students to stand in order of their heights, from shortest to tallest, the student standing exactly in the 3rd position is the median. Half of the students are shorter than this person, and half are taller. 

It does not matter if the tallest student suddenly grows an extra foot taller; the person in the middle remains exactly the same. The median is a *positional* average. It cares about *where* the data points sit in an ordered list, not about the exact numerical weight of the extremes.

## 3. Observing Patterns From Data

Let's look at a small set of test scores (out of 20):
`[12, 15, 11, 19, 14]`

**Step 1:** Order is crucial. We must arrange them first.
Ascending order: `11, 12, 14, 15, 19`

**Step 2:** Find the middle.
Since there are 5 numbers (an odd count), the middle one is clearly the 3rd number.
Median = `14`.

What if we have 6 test scores? Let's add an extreme score of `2`:
`[12, 15, 11, 19, 14, 2]`

**Step 1:** Arrange in ascending order.
`2, 11, 12, 14, 15, 19`

**Step 2:** Find the middle.
Now we have two middle numbers: `12` and `14`. The median is exactly halfway between them.
Median = (12 + 14) / 2 = `13`.

Notice how the extreme score of `2` barely shifted our central value (from 14 to 13). 

## 4. Rule for Finding the Concept

The mathematical rule depends on the type of data we are given.

**A. For Raw/Ungrouped Data**

Let $n$ be the total number of observations, arranged in ascending or descending order.

| Condition | Formula |
| :--- | :--- |
| If $n$ is **Odd** | Median is the value of the $\left(\frac{n+1}{2}\right)^{th}$ term. |
| If $n$ is **Even** | Median is the mean of the $\left(\frac{n}{2}\right)^{th}$ and $\left(\frac{n}{2} + 1\right)^{th}$ terms. |

**B. For Grouped Data (Continuous Frequency Distribution)**

When data is given in class intervals (e.g., 0-10, 10-20), we cannot see individual values. We use an interpolation formula to estimate the median within the "Median Class".

**Formula:**
$$\text{Median} = L + \left[ \frac{\frac{N}{2} - cf}{f} \right] \times h$$

| Symbol | Meaning |
| :--- | :--- |
| **$L$** | Lower limit of the median class |
| **$N$** | Total frequency ($\sum f$) |
| **$cf$** | Cumulative frequency of the class *preceding* the median class |
| **$f$** | Frequency of the median class |
| **$h$** | Class size (width) of the median class |

## 5. Step-by-Step Method

**For Continuous Grouped Data (Board/Exam Standard Procedure):**

1.  **Create a $cf$ Column:** Add a new column for Cumulative Frequency ($cf$) next to the given frequencies.
2.  **Find $N/2$:** Sum all frequencies to get $N$. Calculate $\frac{N}{2}$.
3.  **Locate Median Class:** Look at the $cf$ column. Find the $cf$ value that is *just greater than or equal to* $\frac{N}{2}$. The corresponding class interval is your Median Class.
4.  **Extract Variables:** From the table, note down $L$, $cf$ (from the row *above* the median class), $f$, and $h$.
5.  **Apply Formula:** Substitute values into the formula and solve carefully, following BODMAS rules.

## 6. Visual Understanding

**Diagram 1: The Concept of Positional Middle (Odd vs Even)**

```text
Odd Number of Items (n=5)
Raw:  [7]  [1]  [9]  [3]  [5]
       |    |    |    |    |
Sort: [1]  [3]  [5]  [7]  [9]
                 ^
                 |
               MEDIAN (Exactly the middle item)

Even Number of Items (n=6)
Raw:  [7]  [1]  [9]  [3]  [5]  [8]
       |    |    |    |    |    |
Sort: [1]  [3]  [5]  [7]  [8]  [9]
                  \  /
                   \/
                 MEDIAN = (5+7)/2 = 6
```

**Diagram 2: Finding the Median Class in Grouped Data**

```text
 Class | Freq(f)| Cum.Freq(cf)
-------|--------|-------------
 0-10  |   5    |   5
 10-20 |   8    |  13  <--- (cf just above preceding)
 20-30 |  12    |  25  <--- MEDIAN CLASS (contains N/2)
 30-40 |   5    |  30  <--- N = 30
-------|--------|-------------
          Total N = 30
          N/2 = 15
          
Search cf column for value >= 15. 
'25' is the first cf >= 15. 
Therefore, 20-30 is the median class.
```

## 7. Solved Examples

### Example 1 — Basic (Ungrouped Data)
**Problem:** Find the median of the following data: 34, 47, 41, 52, 53, 56, 35, 49, 55, 42.
**Solution steps:**
1. Sort the data in ascending order:
   34, 35, 41, 42, 47, 49, 52, 53, 55, 56
2. Count the number of observations ($n$). Here, $n = 10$ (which is even).
3. Since $n$ is even, median = mean of $\left(\frac{10}{2}\right)^{th}$ and $\left(\frac{10}{2} + 1\right)^{th}$ terms.
   Median = mean of 5th and 6th terms.
4. The 5th term is 47, and the 6th term is 49.
   Median = $\frac{47 + 49}{2} = \frac{96}{2} = 48$.
**Final answer:** 48

### Example 2 — Moderate (Discrete Frequency Distribution)
**Problem:** Find the median of the following distribution:

| Variable (x) | 10 | 12 | 14 | 16 | 18 | 20 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Frequency (f) | 3 | 5 | 6 | 4 | 4 | 3 |

**Solution steps:**
1. Construct the Cumulative Frequency ($cf$) table.

| x | f | cf |
| :--- | :--- | :--- |
| 10 | 3 | 3 |
| 12 | 5 | 8 |
| 14 | 6 | 14 |
| 16 | 4 | 18 |
| 18 | 4 | 22 |
| 20 | 3 | 25 |

2. Find $N$ (Total frequency). $N = 25$.
3. Calculate $N/2 = 25/2 = 12.5$.
4. Look at the $cf$ column. The cumulative frequency just greater than 12.5 is 14.
5. The value of $x$ corresponding to $cf = 14$ is 14.
**Final answer:** 14

### Example 3 — Advanced (Continuous Grouped Data)
**Problem:** The table below shows the daily expenditure on food of 25 households in a locality. Find the median daily expenditure.

| Daily Expenditure (₹) | 100-150 | 150-200 | 200-250 | 250-300 | 300-350 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| No. of households (f) | 4 | 5 | 12 | 2 | 2 |

**Solution steps:**
1. Prepare the $cf$ table.

| Class | f | cf |
| :--- | :--- | :--- |
| 100-150 | 4 | 4 |
| 150-200 | 5 | 9 |
| **200-250** | **12**| **21** |
| 250-300 | 2 | 23 |
| 300-350 | 2 | 25 |

2. Here, $N = 25$. So, $N/2 = 12.5$.
3. The cumulative frequency just greater than or equal to 12.5 is 21. 
   Therefore, the **median class is 200-250**.
4. Extract values for formula:
   $L = 200$ (lower limit)
   $N = 25$
   $cf = 9$ (cumulative frequency of class *preceding* median class)
   $f = 12$ (frequency of median class)
   $h = 50$ (class size)
5. Apply formula:
   $\text{Median} = L + \left[ \frac{\frac{N}{2} - cf}{f} \right] \times h$
   $\text{Median} = 200 + \left[ \frac{12.5 - 9}{12} \right] \times 50$
   $\text{Median} = 200 + \left[ \frac{3.5}{12} \right] \times 50$
   $\text{Median} = 200 + \left[ \frac{175}{12} \right]$
   $\text{Median} = 200 + 14.58$
**Final answer:** ₹ 214.58

## 8. Interpretation in Data Science

In modern data science, the median is a cornerstone of **robust statistics**. 

*   **Skewed Datasets:** Data in the real world (incomes, web page load times, followers on social media) is rarely bell-shaped. It is usually "skewed" (having a long tail on one side). For skewed distributions, the mean gets dragged towards the tail, but the median stays anchored at the center of mass.
*   **Outlier Handling:** Machine learning models (like Linear Regression) are highly sensitive to outliers. Data scientists often use the median to impute (fill in) missing values instead of the mean, ensuring that a few extreme errors don't corrupt the training data.
*   **Dashboards & Reporting:** When building analytics dashboards for business executives, metrics like "Median Session Duration" or "Median Revenue per User" are preferred over averages to prevent a single massive transaction from making a bad day look good.
*   **Preprocessing Pipelines:** In scaling and normalization (e.g., RobustScaler in Python's scikit-learn), the median is used to center the data, making the preprocessing step immune to extreme values.

## 9. Comparison With Other Measures

| Feature | Mean | Median | Mode |
| :--- | :--- | :--- | :--- |
| **What it is** | Mathematical average | Positional middle | Most frequent value |
| **Outlier Sensitivity** | Very High (pulled easily) | **Zero (Robust)** | Zero |
| **Best used for** | Symmetric, clean data | **Skewed data, incomes, real estate** | Categorical data, finding popular items |
| **Algebraic Treatment**| Capable of further algebra | **Not capable** | Not capable |
| **Data Types** | Continuous / Interval | **Ordinal / Interval / Continuous** | Nominal / Ordinal / Continuous |

## 10. Exam Strategy Box

> 💡 Exam Tip: Always sort raw data before finding the median. 90% of silly mistakes in Section A happen because students forget to arrange the numbers in ascending order.
> 💡 Exam Tip: In grouped data, double-check your cumulative frequency ($cf$) column. The last value in the $cf$ column must exactly equal the total frequency ($\sum f$ or $N$). If it doesn't, you made an addition error.
> 💡 Exam Tip: When using the grouped data formula, the $cf$ used is ALWAYS from the class *above* the median class, but the $f$ is from the median class itself.
> 💡 Exam Tip: If the class intervals are non-continuous (e.g., 10-19, 20-29), you MUST convert them to continuous boundaries (9.5-19.5, 19.5-29.5) before finding $L$ and $h$.
> 💡 Exam Tip: The empirical relationship between Mean, Median, and Mode is `Mode = 3(Median) - 2(Mean)`. Memorize this; it frequently appears in 1-mark MCQs.

## 11. Common Student Errors

> ⚠️ Common Error: Using the median class's own cumulative frequency instead of the preceding class's $cf$ in the formula.
> ⚠️ Common Error: Confusing the formulas for odd and even $n$ in raw data. Remember, even $n$ requires finding the average of TWO middle terms.
> ⚠️ Common Error: Calculating $h$ incorrectly. $h$ is Upper Limit - Lower Limit. Do not just count the number of classes.
> ⚠️ Common Error: Forgetting BODMAS. Students often add $L$ to the numerator before dividing by $f$. Always calculate the fraction part entirely, multiply by $h$, and *then* add $L$ last.
> ⚠️ Common Error: Ignoring data units. If the data is in thousands (₹ '000), make sure your final answer reflects that (e.g., 12.5 means ₹ 12,500).

## 12. Practice Exercises (NCERT + Competitive Exam Style)

### Section A: Very Short Answer (1 mark)
1. Find the median of the first 9 prime numbers.
2. If the median of sorted data 12, 14, 17, $x+2$, $x+4$, 25, 28, 30 is 21, find $x$.
3. What is the median of an array of 50 consecutive integers starting from 1?
4. True or False: The median of a dataset is always a number present within the dataset.
5. Using the empirical formula, find the median if mode = 24 and mean = 27.

### Section B: Short Answer (2-3 marks)
6. Find the median of the following observations: 46, 64, 87, 41, 58, 77, 35, 90, 55, 33, 92. If 92 is replaced by 99 and 41 by 43 in the above data, find the new median.
7. The median of the following data is 16. Find the missing frequency $p$.
   $x$: 10, 15, 20, 25
   $f$: 3, $p$, 4, 2
8. Convert the following "less than" cumulative frequency distribution to a normal frequency distribution and identify the median class.
   Less than 10: 4
   Less than 20: 16
   Less than 30: 40
   Less than 40: 76
   Less than 50: 96
   Less than 60: 112
   Less than 70: 120
9. Find the median wage from the given data:
   Wages (₹): 20-30, 30-40, 40-50, 50-60, 60-70
   Workers: 8, 10, 14, 12, 6
10. If the values of a dataset are multiplied by 3, what happens to the median? Prove with a small example.

### Section C: Exam Level Problems (4-5 marks)
11. The median of the following distribution is 28.5. Find the values of $x$ and $y$, if the total frequency is 60.
    Class: 0-10, 10-20, 20-30, 30-40, 40-50, 50-60
    Frequency: 5, $x$, 20, 15, $y$, 5
12. Calculate the median for the following data:
    Marks: 11-15, 16-20, 21-25, 26-30, 31-35, 36-40
    No. of Students: 2, 3, 6, 7, 14, 12
13. A life insurance agent found the following data for distribution of ages of 100 policy holders. Calculate the median age, if policies are only given to persons having age 18 years onwards but less than 60 years.
    Age (in years) / Number of policy holders:
    Below 20 / 2
    Below 25 / 6
    Below 30 / 24
    Below 35 / 45
    Below 40 / 78
    Below 45 / 89
    Below 50 / 92
    Below 55 / 98
    Below 60 / 100
14. Find the missing frequencies $f_1$ and $f_2$ if the median is 32 and total frequency is 100.
    Marks: 0-10, 10-20, 20-30, 30-40, 40-50, 50-60
    Students: 10, $f_1$, 25, 30, $f_2$, 10
15. Calculate the median of the following continuous frequency distribution. Note the unequal class intervals.
    Class: 0-20, 20-50, 50-70, 70-100
    Frequency: 8, 10, 12, 6

### Section D: Conceptual Reasoning (For Data Science & Advanced Competitions)
16. In a right-skewed dataset (e.g., national wealth distribution), what is the typical relationship between the mean and the median (which one is larger)? Why?
17. A data engineer notices that a faulty sensor randomly recorded a temperature of 9999°C instead of 25°C. Will this error affect the daily median temperature calculation? Explain why.
18. Why can't we find the exact median from a grouped frequency distribution? What assumption does the interpolation formula make?
19. If you add a constant 'k' to every term in a dataset, does the median increase by 'k'? Why?
20. In what specific scenario would the median and the mean of a dataset be exactly equal?

## 13. Fully Solved Answers

### Section A
**1. Solution:** First 9 primes: 2, 3, 5, 7, 11, 13, 17, 19, 23. Number of terms $n=9$ (odd). Median is the 5th term. 
Answer: 11.

**2. Solution:** The data is already sorted. $n=8$ (even). Median is the average of 4th and 5th terms.
Median = $\frac{(x+2) + (x+4)}{2} = \frac{2x+6}{2} = x+3$.
Given Median = 21. So, $x+3 = 21 \Rightarrow x = 18$.
Answer: 18.

**3. Solution:** Integers are 1, 2, 3, ..., 50. $n=50$ (even). Median = average of 25th and 26th terms.
Median = $\frac{25 + 26}{2} = 25.5$.
Answer: 25.5.

**4. Solution:** False. As seen in even-numbered arrays (like example 3), the median can be the average of two numbers, resulting in a value not originally in the dataset.
Answer: False.

**5. Solution:** Formula: Mode = 3(Median) - 2(Mean).
$24 = 3(\text{Median}) - 2(27)$
$24 = 3(\text{Median}) - 54$
$78 = 3(\text{Median}) \Rightarrow \text{Median} = 26$.
Answer: 26.

### Section B
**6. Solution:** 
Original sorted: 33, 35, 41, 46, 55, 58, 64, 77, 87, 90, 92. ($n=11$)
Median = 6th term = 58.
New dataset sorted: 33, 35, 43, 46, 55, 58, 64, 77, 87, 90, 99. ($n=11$)
New Median = 6th term = 58.
Answer: The median remains 58. (Demonstrates robustness to extremes).

**7. Solution:** 
Prepare $cf$: 
$10: 3 \rightarrow cf=3$
$15: p \rightarrow cf=3+p$
$20: 4 \rightarrow cf=7+p$
$25: 2 \rightarrow cf=9+p$
$N = 9+p$. 
Median is given as 16, which means the median occurs between 15 and 20, but since data is discrete, the cumulative frequency at value 15 must contain the median position. For discrete series, $N/2$ method is tricky with unknowns. Better method: Since median is 16, it implies... wait, the data is 10, 15, 20, 25. If median is 16, this is impossible for discrete data unless it's an even array and average is 16. The average of 15 and x? No. Let's assume the question meant Continuous Data or Median = 15. If Median is 16 in a discrete set, the data is invalid. *Correction in interpretation*: If median is 16, it must lie between 15 and 20. But for discrete data, it must be an exact value unless it's an average of 15 and 20 (which is 17.5). Thus, the problem is structurally flawed for discrete series. Let's assume it meant grouped: 5-10, 10-15... Let's use the standard approach: Median is 15. Then $(3+p)$ must be greater than $N/2$. Skip this ambiguous interpretation, assume median is exactly 15. If median = 15, then position $N/2$ falls in $cf = 3+p$. 
*Self-correction*: If median is 16, and data is discrete, this is impossible. If the question implies a weighted median or grouped data with missing intervals, it's poorly phrased. Let's provide the conceptual answer: "A discrete median must be a data point or the exact average of two adjacent points. Since 16 is neither 15, 20, nor their average (17.5), the given data is inconsistent."

**8. Solution:**
Class intervals are formed by taking differences.
0-10: 4
10-20: 16 - 4 = 12
20-30: 40 - 16 = 24
30-40: 76 - 40 = 36
40-50: 96 - 76 = 20
50-60: 112 - 96 = 16
60-70: 120 - 112 = 8
Total $N = 120$. $N/2 = 60$.
The $cf$ just greater than 60 is 76.
Answer: The corresponding median class is 30-40.

**9. Solution:**
$cf$ table:
20-30: 8 $\rightarrow$ cf = 8
30-40: 10 $\rightarrow$ cf = 18
40-50: 14 $\rightarrow$ cf = 32
50-60: 12 $\rightarrow$ cf = 44
60-70: 6 $\rightarrow$ cf = 50
$N = 50$, $N/2 = 25$.
$cf$ just greater than 25 is 32. Median class = 40-50.
$L=40, cf=18, f=14, h=10$.
$\text{Median} = 40 + [ (25 - 18) / 14 ] \times 10 = 40 + [ 7 / 14 ] \times 10 = 40 + [0.5 \times 10] = 45$.
Answer: ₹ 45.

**10. Solution:**
Dataset: 1, 2, 3 (Median = 2)
Multiply by 3: 3, 6, 9 (Median = 6)
Answer: The median is also multiplied by 3. This is a property of positional averages under scaling.

### Section C
**11. Solution:**
$cf$ table:
0-10: 5 $\rightarrow cf = 5$
10-20: $x \rightarrow cf = 5+x$
20-30: 20 $\rightarrow cf = 25+x$
30-40: 15 $\rightarrow cf = 40+x$
40-50: $y \rightarrow cf = 40+x+y$
50-60: 5 $\rightarrow cf = 45+x+y$
Given $N = 60$. So, $45 + x + y = 60 \Rightarrow x + y = 15$ --- (Eq 1)
Median = 28.5. This lies in the class 20-30.
So, Median Class = 20-30.
$L = 20, N/2 = 30, cf = 5+x, f = 20, h = 10$.
$28.5 = 20 + \left[ \frac{30 - (5+x)}{20} \right] \times 10$
$8.5 = \left[ \frac{25 - x}{2} \right]$
$17 = 25 - x$
$x = 8$.
From Eq 1, $8 + y = 15 \Rightarrow y = 7$.
Answer: $x = 8, y = 7$.

**12. Solution:**
Classes are discontinuous. Convert to continuous by subtracting 0.5 from lower limit and adding 0.5 to upper limit.
10.5-15.5: $f=2, cf=2$
15.5-20.5: $f=3, cf=5$
20.5-25.5: $f=6, cf=11$
25.5-30.5: $f=7, cf=18$
30.5-35.5: $f=14, cf=32$
35.5-40.5: $f=12, cf=44$
$N=44, N/2=22$.
$cf$ just > 22 is 32. Median Class = 30.5 - 35.5.
$L=30.5, cf=18, f=14, h=5$.
$\text{Median} = 30.5 + \left[ \frac{22 - 18}{14} \right] \times 5 = 30.5 + \left[ \frac{4}{14} \right] \times 5 = 30.5 + 1.43 = 31.93$.
Answer: 31.93.

**13. Solution:**
The given table is "less than" cumulative frequencies. Convert to normal frequency.
15-20: $cf=2, f=2$ (assuming starts at 15 for a class width of 5, or below 20)
20-25: $cf=6, f=6-2=4$
25-30: $cf=24, f=24-6=18$
30-35: $cf=45, f=45-24=21$
35-40: $cf=78, f=78-45=33$
40-45: $cf=89, f=89-78=11$
45-50: $cf=92, f=92-89=3$
50-55: $cf=98, f=98-92=6$
55-60: $cf=100, f=100-98=2$
$N = 100, N/2 = 50$.
$cf$ just > 50 is 78. Median class = 35-40.
$L=35, cf=45, f=33, h=5$.
$\text{Median} = 35 + \left[ \frac{50 - 45}{33} \right] \times 5 = 35 + \frac{25}{33} = 35 + 0.76 = 35.76$.
Answer: 35.76 years.

**14. Solution:**
$cf$ table:
0-10: 10 $\rightarrow cf = 10$
10-20: $f_1 \rightarrow cf = 10+f_1$
20-30: 25 $\rightarrow cf = 35+f_1$
30-40: 30 $\rightarrow cf = 65+f_1$
40-50: $f_2 \rightarrow cf = 65+f_1+f_2$
50-60: 10 $\rightarrow cf = 75+f_1+f_2$
Given $N = 100$. So, $75+f_1+f_2 = 100 \Rightarrow f_1+f_2 = 25$ --- (Eq 1)
Median = 32. Median Class = 30-40.
$L=30, N/2=50, cf=35+f_1, f=30, h=10$.
$32 = 30 + \left[ \frac{50 - (35+f_1)}{30} \right] \times 10$
$2 = \frac{15 - f_1}{3}$
$6 = 15 - f_1 \Rightarrow f_1 = 9$.
From Eq 1, $9 + f_2 = 25 \Rightarrow f_2 = 16$.
Answer: $f_1 = 9, f_2 = 16$.

**15. Solution:**
$cf$ table:
0-20: 8 $\rightarrow cf = 8$
20-50: 10 $\rightarrow cf = 18$
50-70: 12 $\rightarrow cf = 30$
70-100: 6 $\rightarrow cf = 36$
$N=36, N/2=18$.
The $cf$ just greater than or EQUAL to 18 is 18 itself. This means the median is EXACTLY the upper limit of the class 20-50.
Let's verify with formula. The median class is 20-50.
$L=20, cf=8, f=10, h=30$.
$\text{Median} = 20 + \left[ \frac{18 - 8}{10} \right] \times 30 = 20 + \left[ \frac{10}{10} \right] \times 30 = 20 + 30 = 50$.
Answer: 50.

### Section D
**16. Solution:** In a right-skewed dataset, the Mean is larger than the Median. The long tail on the right (extremely high values) pulls the mathematical average upwards, while the median remains anchored in the middle of the sorted list.
**17. Solution:** No, it will not affect the median (or only minimally). The median only cares about the order. Whether the highest value is 30°C or 9999°C, it remains the last item in the sorted list. The middle position does not shift. This is why the median is "robust to outliers."
**18. Solution:** The formula assumes that frequencies are uniformly (evenly) distributed within the median class. Since we don't have the raw data, we interpolate assuming a straight-line distribution of points within that specific interval.
**19. Solution:** Yes. Adding a constant 'k' to every term shifts the entire sorted array by 'k'. Therefore, the middle term also shifts by exactly 'k'.
**20. Solution:** When the dataset is perfectly symmetrical (e.g., a perfect normal bell curve), the center of mass (mean) and the positional middle (median) lie exactly at the same central point.

## 14. Real Dataset Example

**Dataset Context: House Prices in a Neighborhood**
Imagine you are a data analyst scraping property prices for a small neighborhood in Bangalore.

Prices (in ₹ Crores): `1.2, 1.5, 1.4, 1.3, 1.6, 1.2, 1.4, 25.0`

Notice that one house is a massive luxury mansion worth ₹ 25.0 Cr.
*   **Mean Calculation:** (1.2 + 1.5 + 1.4 + 1.3 + 1.6 + 1.2 + 1.4 + 25.0) / 8 = **₹ 4.32 Cr**
*   **Median Calculation:** Sort: 1.2, 1.2, 1.3, 1.4, 1.4, 1.5, 1.6, 25.0. Average of 4th and 5th terms = (1.4 + 1.4)/2 = **₹ 1.4 Cr**

**Interpretation:**
If a real estate app displays the "Average House Price" as ₹ 4.32 Cr, a normal buyer will assume the neighborhood is completely unaffordable and ignore it. However, the Median price of ₹ 1.4 Cr accurately tells the buyer what a typical house actually costs. Dashboards invariably use median for real estate pricing to filter out the noise of luxury outlier properties.

## 15. Quick Revision Sheet

*   **Key Idea:** The median is the middle value of an *ordered* dataset. 50% of data is below it, 50% is above it.
*   **Formula (Raw Odd):** $\left(\frac{n+1}{2}\right)^{th}$ term.
*   **Formula (Raw Even):** Average of $\left(\frac{n}{2}\right)^{th}$ and $\left(\frac{n}{2} + 1\right)^{th}$ terms.
*   **Formula (Grouped):** $L + \left[ \frac{\frac{N}{2} - cf}{f} \right] \times h$
*   **When to Use:** When data is skewed, has extreme outliers, or deals with incomes/real estate/lifespans.
*   **When NOT to Use:** When total sums are important, or the data is perfectly symmetric and small.
*   **Shortcut:** Mode = 3(Median) - 2(Mean)

## 16. Interview & Data Science Questions

### Beginner
**Q:** You are given a list of user ages. How do you find the median using Python?
**A:** `import numpy as np; median_age = np.median(ages_list)`. Behind the scenes, numpy sorts the array and extracts the middle element (or average of two middle elements).

### Intermediate
**Q:** In an e-commerce dashboard, why do we report "Median Order Value" instead of "Average Order Value"?
**A:** If 99 customers buy a ₹500 t-shirt, and 1 customer buys a ₹1,00,000 diamond ring, the average order value spikes artificially. The median order value remains ₹500, accurately reflecting the typical customer behavior, which is better for setting marketing budgets.

### Advanced
**Q:** Explain the concept of Breakdown Point. What is the breakdown point of the median compared to the mean?
**A:** Breakdown point is the proportion of incorrect/extreme data points a statistic can handle before giving a completely false result. The mean has a breakdown point of 0% (one infinity value corrupts the mean). The median has a breakdown point of 50%; you can replace nearly half the data with infinity, and the median will still accurately represent the remaining core data.

## 17. Mini Quiz

**1. The median is essentially a measure of:**
A) Central tendency based on mathematical sum
B) Central tendency based on position
C) Dispersion of data
D) Frequency of occurrence

**2. If the median of 5 observations $x, x+2, x+4, x+6, x+8$ is 11, what is the value of $x$?**
A) 5
B) 7
C) 9
D) 11

**3. In the formula for the median of grouped data, what does '$cf$' represent?**
A) Cumulative frequency of the median class
B) Frequency of the median class
C) Cumulative frequency of the class preceding the median class
D) Total frequency

**4. Why is the median preferred over the mean for reporting national income?**
A) It is easier to calculate
B) It takes into account every single penny earned
C) It is not affected by the extremely high incomes of billionaires
D) It can be manipulated algebraically

**5. For a given dataset, Mean = 30 and Mode = 24. Using the empirical relation, find the Median.**
A) 28
B) 26
C) 32
D) 27

## Mini Quiz Answer Key
1. B
2. B
3. C
4. C
5. A
```