# Lecture 3: Mode

## 1. Why This Concept Matters

Imagine you own a shoe store and want to restock your inventory. You calculate the arithmetic mean of all the shoe sizes sold last month and get a size of 8.34. Can you order a shoe of size 8.34? No! Even if you round it to 8.5, it might not represent what most people actually buy. Instead, you need to know the _most frequently sold_ shoe size. If size 9 sold the most pairs, that is the size you need to stock up on.

This most popular, most frequent value is called the **Mode**. In business, elections, and data science, we often don't care about the mathematical average or the exact middle; we want to know what happens most often. What is the most common customer complaint? Which product is the bestseller? What is the most common color of cars on the highway? The Mode answers these questions.

## 2. Understanding the Idea Intuitively

Think of the Mode as the winner of a popularity contest.

If you ask 10 friends what their favorite color is, and 6 say Blue, 3 say Red, and 1 says Green, the "Blue" color wins the contest. It has the highest number of votes. It is the Mode.

Unlike the Mean, which requires numbers to add up, or the Median, which requires ordering, the Mode simply looks for repetition. It is the only measure of central tendency that makes perfect sense for non-numerical (categorical) data, like colors, brands, or names.

## 3. Observing Patterns From Data

Let's look at the daily number of coffees consumed by an office worker over 7 days:
`[2, 1, 2, 4, 2, 1, 3]`

**Step 1:** Count how many times each number appears.

- 1 coffee: appears 2 times
- 2 coffees: appears 3 times
- 3 coffees: appears 1 time
- 4 coffees: appears 1 time

**Step 2:** Find the number with the highest count.
The number `2` appears most frequently (3 times).

Therefore, the Mode = 2 coffees.
If another week the data was `[1, 1, 2, 2, 3, 4]`, we would have two modes: 1 and 2. This is called a **bimodal** distribution.

## 4. Rule for Finding the Concept

The calculation of the Mode depends entirely on the form of the data.

**A. For Raw/Ungrouped Data**

Simply count the frequencies of each observation. The observation with the highest frequency is the Mode.

**B. For Grouped Data (Continuous Distribution)**

When data is grouped into class intervals (e.g., 10-20), we cannot see individual values to count them. Instead, we first find the **Modal Class** (the class interval with the highest frequency) and then use an interpolation formula to pinpoint the exact mode within that class.

**Formula:**
$$\text{Mode} = L + \left[ \frac{f_1 - f_0}{2f_1 - f_0 - f_2} \right] \times h$$

| Symbol    | Meaning                                                         |
| :-------- | :-------------------------------------------------------------- |
| **$L$**   | Lower limit of the modal class                                  |
| **$f_1$** | Frequency of the modal class                                    |
| **$f_0$** | Frequency of the class _preceding_ the modal class              |
| **$f_2$** | Frequency of the class _succeeding_ (following) the modal class |
| **$h$**   | Class size (width) of the modal class                           |

**C. The Empirical Formula**
If a distribution is moderately skewed, the Mode can be approximated using the Mean and Median:
$$\text{Mode} = 3 \text{ Median} - 2 \text{ Mean}$$

## 5. Step-by-Step Method

**Algorithm for Grouped Data Mode (Board/Exam Procedure):**

1. **Locate Modal Class:** Look at the frequency column. Find the highest frequency number. The class interval corresponding to this highest frequency is your Modal Class.
2. **Extract Variables:** From the table, identify:
   - $L$: Lower limit of that modal class.
   - $f_1$: The highest frequency itself.
   - $f_0$: The frequency of the row immediately _above_ the modal class.
   - $f_2$: The frequency of the row immediately _below_ the modal class.
   - $h$: The width of the modal class (Upper Limit - Lower Limit).
3. **Verify Continuity:** Ensure class intervals are continuous (e.g., 0-10, 10-20). If they are discontinuous (e.g., 1-10, 11-20), adjust boundaries by 0.5 before finding $L$.
4. **Apply Formula:** Substitute $L, f_1, f_0, f_2$, and $h$ into the formula. Follow BODMAS rules carefully to solve.

## 6. Visual Understanding

**Diagram 1: Data Flow for Finding the Mode**

```text
    Dataset Values
 [2, 5, 2, 7, 2, 8, 5]
          ↓
  Count Frequencies
   2: ||| (3 times)
   5: ||  (2 times)
   7: |   (1 time)
   8: |   (1 time)
          ↓
 Find Highest Frequency
      (3 times)
          ↓
        Mode
          2
```

**Diagram 2: Visualizing the Modal Class (Histogram Concept)**

```text
Freq
 |          [ f1 ]  <-- Highest Bar (Modal Class)
 |          |    |
 |  [ f0 ]  |    |  [ f2 ]
 |  |    |  |    |  |    |
 |__|____|__|____|__|____|____ Classes
   0-10    10-20   20-30
             ^
             L (Lower limit of modal class)

The formula effectively shifts the Mode from the center of the modal class
towards the neighboring class that has a higher frequency (comparing f0 and f2).
```

## 7. Solved Examples

### Example 1 — Basic

**Problem:** Find the mode of the following data: 12, 14, 16, 12, 14, 14, 16, 14, 10, 14, 18, 14.
**Solution steps:**

1. Create a frequency tally.
   - 10 occurs 1 time
   - 12 occurs 2 times
   - 14 occurs 6 times
   - 16 occurs 2 times
   - 18 occurs 1 time
2. Identify the observation with the maximum frequency.
   The value 14 occurs a maximum of 6 times.
   **Final answer:** 14

### Example 2 — Moderate

**Problem:** Calculate the mode for the following frequency distribution:

| Marks    | 0-20 | 20-40 | 40-60 | 60-80 | 80-100 |
| :------- | :--- | :---- | :---- | :---- | :----- |
| Students | 10   | 35    | 52    | 20    | 15     |

**Solution steps:**

1. Look at the frequency row to find the maximum value.
   The maximum frequency is 52.
2. The class corresponding to 52 is 40-60. This is the **Modal Class**.
3. Extract variables for the formula:
   $L = 40$ (lower limit of 40-60)
   $f_1 = 52$ (frequency of modal class)
   $f_0 = 35$ (frequency of class preceding, 20-40)
   $f_2 = 20$ (frequency of class succeeding, 60-80)
   $h = 20$ (class size: $60 - 40$)
4. Apply the formula:
   $\text{Mode} = L + \left[ \frac{f_1 - f_0}{2f_1 - f_0 - f_2} \right] \times h$
   $\text{Mode} = 40 + \left[ \frac{52 - 35}{2(52) - 35 - 20} \right] \times 20$
   $\text{Mode} = 40 + \left[ \frac{17}{104 - 55} \right] \times 20$
   $\text{Mode} = 40 + \left[ \frac{17}{49} \right] \times 20$
   $\text{Mode} = 40 + \frac{340}{49} \approx 40 + 6.94$
   **Final answer:** 46.94

### Example 3 — Advanced

**Problem:** The mode of the following data is 36. Find the missing frequency $x$.

| Class | 0-10 | 10-20 | 20-30 | 30-40 | 40-50 | 50-60 | 60-70 |
| :---- | :--- | :---- | :---- | :---- | :---- | :---- | :---- |
| Freq  | 8    | 10    | $x$   | 16    | 12    | 6     | 7     |

**Solution steps:**

1. We are given $\text{Mode} = 36$.
2. Since 36 lies in the class interval 30-40, the **Modal Class** must be 30-40.
3. Extract variables based on the modal class 30-40:
   $L = 30$
   $f_1 = 16$
   $f_0 = x$ (frequency of preceding class 20-30)
   $f_2 = 12$ (frequency of succeeding class 40-50)
   $h = 10$
4. Use the mode formula:
   $36 = 30 + \left[ \frac{16 - x}{2(16) - x - 12} \right] \times 10$
   $6 = \left[ \frac{16 - x}{32 - x - 12} \right] \times 10$
   $6 = \frac{(16 - x) \times 10}{20 - x}$
5. Cross-multiply:
   $6(20 - x) = 160 - 10x$
   $120 - 6x = 160 - 10x$
   $10x - 6x = 160 - 120$
   $4x = 40 \Rightarrow x = 10$
   **Final answer:** 10

## 8. Interpretation in Data Science

In modern data analytics and machine learning, the mode plays several unique roles that the mean and median cannot fill:

- **Handling Categorical Data:** Machine learning models often receive categorical features (e.g., `City: [Delhi, Mumbai, Delhi, Chennai]`). The mean and median mathematically cannot process strings. The mode is the _only_ central tendency measure that works natively with categorical variables.
- **Preprocessing and Feature Engineering (Mode Imputation):** When datasets have missing values (NaNs) in categorical columns (like "Gender" or "Subscription Tier"), data scientists use **Mode Imputation**. They replace missing values with the most frequently occurring category to maintain data integrity without breaking the pipeline.
- **Dashboards:** In marketing and sales dashboards, the mode is framed as "Top Selling Product," "Most Active User Age Group," or "Peak Traffic Hour."
- **Insensitivity to Outliers:** The mode is absolutely immune to extreme outliers. If a dataset `[2, 3, 3, 3, 5]` suddenly changes to `[2, 3, 3, 3, 500000]`, the mode strictly remains 3.

## 9. Comparison With Other Measures

| Feature                     | Mean                 | Median                      | Mode                                           |
| :-------------------------- | :------------------- | :-------------------------- | :--------------------------------------------- |
| **Mathematical Definition** | Sum divided by count | The middle positional value | Most frequently occurring value                |
| **Data Types**              | Continuous, Interval | Continuous, Ordinal         | **Categorical (Nominal)**, Ordinal, Continuous |
| **Outlier Sensitivity**     | Extremely High       | Zero (Robust)               | **Zero (Robust)**                              |
| **Existence**               | Always exactly one   | Always exactly one          | **Can be None, One, or Multiple (Bimodal)**    |
| **Uses all data points?**   | Yes                  | No                          | No                                             |

## 10. Exam Strategy Box

> 💡 Exam Tip: Always check if the frequency distribution is continuous. If classes are given as 11-20, 21-30, you must convert them to 10.5-20.5, 20.5-30.5 before finding $L$, otherwise your answer will be slightly off.
> 💡 Exam Tip: Be careful identifying $f_0, f_1, f_2$. Think of them in order: 0 comes before 1, and 2 comes after 1. So $f_1$ is the main modal class, $f_0$ is before it, $f_2$ is after it.
> 💡 Exam Tip: Sometimes the highest frequency might occur in the very first or very last class interval. If it's the first class, $f_0 = 0$. If it's the last class, $f_2 = 0$.
> 💡 Exam Tip: The Mode formula evaluates a ratio, meaning the final answer must ALWAYS lie strictly _between_ the lower limit ($L$) and upper limit of your modal class. If your answer falls outside this range, your calculation is mathematically wrong.
> 💡 Exam Tip: If a 1-mark question asks for the Mode given the Mean and Median, immediately jump to the empirical formula: $\text{Mode} = 3\text{Median} - 2\text{Mean}$.

## 11. Common Student Errors

> ⚠️ Common Error: Adding up all the frequencies (finding $\sum f_i$) and trying to use $N/2$ like in the Median. The Mode does not require cumulative frequency or the total sum $N$.
> ⚠️ Common Error: Misidentifying the Modal Class. Always look for the highest number in the _Frequency_ column, not the Class Interval column.
> ⚠️ Common Error: Writing down the highest frequency ($f_1$) as the final answer instead of putting it into the formula.
> ⚠️ Common Error: Messing up the denominator $2f_1 - f_0 - f_2$. Students often subtract $f_0$ but forget to subtract $f_2$, or they multiply $f_1$ incorrectly.
> ⚠️ Common Error: Stating that a dataset with no repeating numbers has a "Mode of 0". If no number repeats, there is **No Mode**. A mode of 0 would mean the number '0' appears the most times.

## 12. Practice Exercises (NCERT + Competitive Exam Style)

### Section A: Very Short Answer (1-2 marks)

1. Find the mode of the data: 5, 7, 9, 5, 8, 7, 5, 9, 10, 5.
2. In a continuous frequency distribution, the modal class is 40-50, its frequency is 20, frequency of preceding class is 12 and succeeding class is 11. Find the mode.
3. If the median of a dataset is 15.6 and the mean is 15.2, what is its approximate mode using the empirical relationship?
4. What is the mode of a dataset where every observation occurs exactly once?
5. Find the mode of the first 10 prime numbers.

### Section B: Short Answer (2-3 marks)

6. A shoe shop sold pairs of shoes of the following sizes in a day: 6, 7, 8, 9, 6, 7, 8, 7, 6, 9, 7, 8, 7, 7. What is the modal shoe size? Why is mode useful here instead of mean?
7. Calculate the mode of the following data:
   $x_i$: 10, 20, 30, 40, 50
   $f_i$: 4, 8, 12, 10, 5
8. Find the mode of the following distribution:
   Marks: 0-10, 10-20, 20-30, 30-40, 40-50
   Students: 5, 12, 20, 11, 4
9. Convert the following discontinuous data into continuous classes and find the modal class and its lower limit ($L$):
   Class: 1-5, 6-10, 11-15, 16-20
   Freq: 3, 8, 15, 6
10. Can a distribution have more than one mode? Give a real-life example where this might happen.

### Section C: Exam Level Problems (4-5 marks)

11. Compute the mode for the following frequency distribution:
    Class: 0-20, 20-40, 40-60, 60-80, 80-100, 100-120
    Frequency: 10, 35, 52, 61, 38, 29
12. Given that the mode of the distribution below is 34.5, find the missing frequency $y$.
    Class: 0-10, 10-20, 20-30, 30-40, 40-50
    Freq: 4, 8, 10, $y$, 8
13. The following data gives the distribution of total monthly household expenditure of 200 families. Find the modal monthly expenditure.
    Expenditure (₹): 1000-1500, 1500-2000, 2000-2500, 2500-3000, 3000-3500, 3500-4000, 4000-4500, 4500-5000
    Families: 24, 40, 33, 28, 30, 22, 16, 7
14. The mode of a grouped frequency distribution is 75 and the modal class is 65-80. The frequency of the class preceding the modal class is 6 and the frequency of the class succeeding the modal class is 8. Find the frequency of the modal class.
15. Calculate the mean, median, and mode for the following data using standard formulas, and verify if the empirical relation $\text{Mode} \approx 3\text{Median} - 2\text{Mean}$ holds true.
    Class: 0-10, 10-20, 20-30, 30-40, 40-50
    Frequency: 3, 4, 7, 4, 2

### Section D: Conceptual Reasoning (For Data Science & Advanced Competitions)

16. Why is Mode Imputation preferred over Mean Imputation when handling missing values in a "Car Brand" column of a dataset?
17. A clothing retailer is looking at last year's sales. The Mean shirt size sold was Medium-Large, the Median was Large, but the Mode was Small. Which metric should dictate their manufacturing order for the next year? Why?
18. If every value in a dataset is multiplied by a constant $k$, what happens to the mode? Prove it conceptually.
19. What happens to the Mode grouped data formula if the maximum frequency is shared by two adjacent classes (e.g., $f_1 = f_0 = 20$)?
20. Why do data scientists plot a histogram or Kernel Density Estimate (KDE) plot to visually inspect for "bimodal" distributions before applying standard linear regression?

## 13. Fully Solved Answers

### Section A

**1. Solution:**
Frequencies: 5 (four times), 7 (two times), 9 (two times), 8, 10 (one time each). Highest frequency is 4, for the value 5.
**Final Answer:** 5.

**2. Solution:**
$L = 40$, $f_1 = 20$, $f_0 = 12$, $f_2 = 11$, $h = 10$.
Mode = $40 + \left[ \frac{20 - 12}{2(20) - 12 - 11} \right] \times 10 = 40 + \left[ \frac{8}{40 - 23} \right] \times 10 = 40 + \left[ \frac{8}{17} \right] \times 10 = 40 + 4.71 = 44.71$.
**Final Answer:** 44.71.

**3. Solution:**
$\text{Mode} = 3\text{Median} - 2\text{Mean} = 3(15.6) - 2(15.2) = 46.8 - 30.4 = 16.4$.
**Final Answer:** 16.4.

**4. Solution:**
If every observation occurs exactly once, there is no value that appears more frequently than the others.
**Final Answer:** No Mode.

**5. Solution:**
First 10 primes: 2, 3, 5, 7, 11, 13, 17, 19, 23, 29. No number repeats.
**Final Answer:** No Mode.

### Section B

**6. Solution:**
Frequencies: 6 (three times), 7 (six times), 8 (three times), 9 (two times). Maximum frequency is 6 for size 7. The mode is useful because a retailer must stock the exact sizes customers buy. You cannot stock an "average" shoe size if it's a fraction.
**Final Answer:** 7.

**7. Solution:**

| $x_i$ | $f_i$  |
| :---- | :----- |
| 10    | 4      |
| 20    | 8      |
| 30    | **12** |
| 40    | 10     |
| 50    | 5      |

Highest frequency is 12, corresponding to $x_i = 30$.
**Final Answer:** 30.

**8. Solution:**

| Marks     | Students ($f_i$) |
| :-------- | :--------------- |
| 0-10      | 5                |
| 10-20     | 12               |
| **20-30** | **20**           |
| 30-40     | 11               |
| 40-50     | 4                |

Modal class = 20-30. $L=20, f_1=20, f_0=12, f_2=11, h=10$.
Mode = $20 + \left[ \frac{20 - 12}{40 - 12 - 11} \right] \times 10 = 20 + \left[ \frac{8}{17} \right] \times 10 = 20 + 4.7 = 24.7$.
**Final Answer:** 24.7.

**9. Solution:**
Convert to continuous boundaries by subtracting 0.5 from lower limit and adding 0.5 to upper limit.

| Cont. Class     | Freq   |
| :-------------- | :----- |
| 0.5 - 5.5       | 3      |
| 5.5 - 10.5      | 8      |
| **10.5 - 15.5** | **15** |
| 15.5 - 20.5     | 6      |

Modal class is 10.5 - 15.5.
**Final Answer:** Modal class is 10.5 - 15.5, $L = 10.5$.

**10. Solution:**
Yes, a distribution can be bimodal or multimodal. A real-life example: The sizes of shoes sold in a store that caters equally to both adult men and adult women. You would likely see a high peak around size 7 (women) and another high peak around size 10 (men).
**Final Answer:** Yes (e.g., Bimodal distribution).

### Section C

**11. Solution:**

| Class     | Frequency |
| :-------- | :-------- |
| 0-20      | 10        |
| 20-40     | 35        |
| 40-60     | 52        |
| **60-80** | **61**    |
| 80-100    | 38        |
| 100-120   | 29        |

Modal Class = 60-80. $L=60, f_1=61, f_0=52, f_2=38, h=20$.
Mode = $60 + \left[ \frac{61 - 52}{2(61) - 52 - 38} \right] \times 20 = 60 + \left[ \frac{9}{122 - 90} \right] \times 20$
Mode = $60 + \left[ \frac{9}{32} \right] \times 20 = 60 + \frac{180}{32} = 60 + 5.625 = 65.625$.
**Final Answer:** 65.625.

**12. Solution:**
Given Mode = 34.5. This value falls in the class 30-40.
Therefore, Modal Class = 30-40.
$L=30, f_1=y, f_0=10, f_2=8, h=10$.
$34.5 = 30 + \left[ \frac{y - 10}{2y - 10 - 8} \right] \times 10$
$4.5 = \left[ \frac{y - 10}{2y - 18} \right] \times 10 \Rightarrow 4.5 = \frac{10y - 100}{2y - 18}$
$4.5(2y - 18) = 10y - 100 \Rightarrow 9y - 81 = 10y - 100$
$100 - 81 = 10y - 9y \Rightarrow y = 19$.
**Final Answer:** $y = 19$.

**13. Solution:**

| Expenditure   | Families |
| :------------ | :------- |
| 1000-1500     | 24       |
| **1500-2000** | **40**   |
| 2000-2500     | 33       |
| 2500-3000     | 28       |
| ...           | ...      |

Max frequency is 40. Modal class is 1500-2000.
$L=1500, f_1=40, f_0=24, f_2=33, h=500$.
Mode = $1500 + \left[ \frac{40 - 24}{80 - 24 - 33} \right] \times 500 = 1500 + \left[ \frac{16}{80 - 57} \right] \times 500 = 1500 + \left[ \frac{16}{23} \right] \times 500$
Mode = $1500 + \frac{8000}{23} \approx 1500 + 347.83 = 1847.83$.
**Final Answer:** ₹ 1847.83.

**14. Solution:**
Given: Mode = 75, Modal class = 65-80, $f_0 = 6, f_2 = 8, L = 65, h = 15$. Find $f_1$.
$75 = 65 + \left[ \frac{f_1 - 6}{2f_1 - 6 - 8} \right] \times 15$
$10 = \left[ \frac{f_1 - 6}{2f_1 - 14} \right] \times 15$
$\frac{10}{15} = \frac{f_1 - 6}{2f_1 - 14} \Rightarrow \frac{2}{3} = \frac{f_1 - 6}{2f_1 - 14}$
$2(2f_1 - 14) = 3(f_1 - 6) \Rightarrow 4f_1 - 28 = 3f_1 - 18$
$4f_1 - 3f_1 = 28 - 18 \Rightarrow f_1 = 10$.
**Final Answer:** 10.

**15. Solution:**

| Class     | $f_i$  | $x_i$ | $f_ix_i$ | $cf$ |
| :-------- | :----- | :---- | :------- | :--- |
| 0-10      | 3      | 5     | 15       | 3    |
| 10-20     | 4      | 15    | 60       | 7    |
| **20-30** | **7**  | 25    | 175      | 14   |
| 30-40     | 4      | 35    | 140      | 18   |
| 40-50     | 2      | 45    | 90       | 20   |
| **Sum**   | $N=20$ |       | 480      |      |

**Mean:** $\bar{x} = 480 / 20 = 24$.
**Median:** $N/2 = 10$. Median class is 20-30. $L=20, cf=7, f=7, h=10$.
Median = $20 + [\frac{10 - 7}{7}] \times 10 = 20 + \frac{30}{7} = 20 + 4.28 = 24.28$.
**Mode:** Modal class is 20-30. $L=20, f_1=7, f_0=4, f_2=4, h=10$.
Mode = $20 + [\frac{7 - 4}{14 - 4 - 4}] \times 10 = 20 + [\frac{3}{6}] \times 10 = 20 + 5 = 25$.
**Verification:** $3\text{Median} - 2\text{Mean} = 3(24.28) - 2(24) = 72.84 - 48 = 24.84$.
Mode (25) $\approx$ Empirical Mode (24.84). The relation holds closely.
**Final Answer:** Mean=24, Median=24.28, Mode=25. Verified.

### Section D

**16. Solution:** "Car Brand" is a categorical variable (e.g., Toyota, Honda, Ford). The mathematical mean of strings does not exist. The mode represents the most frequently occurring brand in the dataset, making it the only logical choice to fill in missing string/categorical data cleanly.
**17. Solution:** They should use the **Mode** (Small). In manufacturing retail, you must produce what people actually buy most often. The mean and median might be skewed by a few extremely large sizes, but if the vast majority of sales transactions are for 'Small' shirts, producing 'Large' shirts will result in unsold inventory.
**18. Solution:** The mode is also multiplied by $k$. If the value '5' appeared the most times in the dataset, and every number is multiplied by 3, the number '15' will now appear the exact same most number of times.
**19. Solution:** If $f_1 = f_0$, the numerator $(f_1 - f_0)$ becomes 0. The formula mathematically results in $\text{Mode} = L + 0 = L$. This physically means the mode sits exactly at the lower boundary separating the two equally high class intervals.
**20. Solution:** Linear regression models and standard metrics often assume data is "normally distributed" (a single bell curve). If data is bimodal (two peaks, like height of mixed men and women), the mean falls right in the empty middle, representing nobody. Data scientists split bimodal datasets into two separate groups before modeling.

## 14. Real Dataset Example

**Dataset Context: User Ratings on a Shopping App**
Let's analyze the 5-star ratings for a newly released mobile phone case.
Ratings data: `[1, 5, 5, 5, 4, 5, 1, 5, 5, 3]`

**Calculations:**

- Mean Rating = (1+5+5+5+4+5+1+5+5+3) / 10 = **3.9 stars**
- Mode Rating = **5 stars** (appears 6 times out of 10)

**Interpretation:**
If a user just looks at the Mean (3.9 stars), they might think the product is mediocre or average. However, the Mode (5 stars) tells a very different story: the vast majority of people absolutely loved the product. The mean was dragged down by just two angry users who left 1-star reviews. For categorical or ordinal data (like 1 to 5 star ratings), dashboards often display the Mode ("Most users rated this 5 stars!") alongside the mean to provide a complete picture of customer sentiment.

## 15. Quick Revision Sheet

- **Definition:** The value that occurs with the maximum frequency.
- **Best Used For:** Categorical data, nominal data, finding popular items, determining inventory.
- **Formula (Grouped):** $L + \left[ \frac{f_1 - f_0}{2f_1 - f_0 - f_2} \right] \times h$
- **Empirical Formula:** $\text{Mode} = 3\text{Median} - 2\text{Mean}$
- **Key Property 1:** Can be calculated for open-ended class intervals.
- **Key Property 2:** Completely unaffected by extreme outliers.
- **Data Science Use:** Mode imputation for replacing missing categorical/string values in data preprocessing pipelines.

## 16. Interview & Data Science Questions

### Beginner

**Q:** Which pandas function in Python would you use to find the mode of a column named 'City'?
**A:** `df['City'].mode()[0]`. Note that `.mode()` returns a series because there can be multiple modes, so `[0]` extracts the first one.

### Intermediate

**Q:** You have a dataset of 1 million salaries. It has a massive right skew (most people make 50k, a few make 10 million). Sort the Mean, Median, and Mode in ascending order.
**A:** Mode < Median < Mean. The mode stays at the absolute peak of the curve (50k). The median is slightly pulled to the right. The mean is pulled aggressively to the right by the multimillionaires.

### Advanced

**Q:** When performing Mode Imputation on a categorical feature in a machine learning pipeline, what is the risk of doing it before performing a Train-Test split?
**A:** Doing it before the split causes **Data Leakage**. The mode of the entire dataset (including the test set) leaks into the training data. Mode imputation must be calculated _only_ on the training set, and that specific value should be used to impute both train and test sets.

## 17. Mini Quiz

**1. The empirical relationship between Mean, Median, and Mode is:**
A) Mean = 3 Median - 2 Mode
B) Mode = 3 Median - 2 Mean
C) Median = 3 Mode - 2 Mean
D) Mode = 2 Median - 3 Mean

**2. Which of the following data types can ONLY be analyzed using the Mode?**
A) Continuous (e.g., Weights)
B) Interval (e.g., Temperatures)
C) Nominal/Categorical (e.g., Hair Color)
D) Ratio (e.g., Distances)

**3. In the formula for grouped Mode, the term $f_0$ refers to:**
A) The lowest frequency in the table
B) The frequency of the modal class
C) The frequency of the class succeeding the modal class
D) The frequency of the class preceding the modal class

**4. A dataset is bimodal. This means:**
A) The mode is equal to the mean
B) The mode is zero
C) The dataset has two values that share the highest frequency
D) The dataset has no mode

**5. If the maximum frequency of a grouped distribution is 25, and both the preceding and succeeding classes have a frequency of 10, where will the Mode lie?**
A) Closer to the lower limit of the modal class
B) Closer to the upper limit of the modal class
C) Exactly in the middle of the modal class
D) Outside the modal class

## Mini Quiz Answer Key

1. B
2. C
3. D
4. C
5. C
