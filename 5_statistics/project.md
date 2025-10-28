## Salary Example (Mean vs Median)

Suppose we have the following monthly salaries (in $):

```python
salaries = np.array([3000, 3200, 3500, 4000, 4200, 5000, 12000])
```

### Let’s compute mean & median

```python
import numpy as np

salaries = np.array([3000, 3200, 3500, 4000, 4200, 5000, 12000])

print("Mean Salary:", np.mean(salaries))
print("Median Salary:", np.median(salaries))
```

### Output

```
Mean Salary  =  5200
Median Salary = 4000
```

| Statistic     | Value                            | Meaning           |
| ------------- | -------------------------------- | ----------------- |
| Mean = 5200   | looks like most people earn 5200 | ❌ skewed by 12000 |
| Median = 4000 | typical salary of the group      | ✅ more realistic  |

The **mean is lying** because of ONE high outlier (12000).

This is **exactly** why MEDIAN is used in salary reports in real life.

---

## `var()` — Variance (how spread out is data)

```python
print("Variance:", np.var(salaries))
```

Variance = **average of squared distance from mean**
(Standard deviation is sqrt(variance)

---

## `argmin()` & `argmax()` — index of smallest/largest salary

```python
print("Index of lowest salary:", np.argmin(salaries))
print("Index of highest salary:", np.argmax(salaries))
```

Output:

```
Index of lowest salary: 0   (3000)
Index of highest salary: 6  (12000)
```

This is very useful for datasets → “which employee has the highest salary?”

---

## `percentile()` — Used in ML for normalization & handling outliers

```python
print("25th percentile:", np.percentile(salaries, 25))
print("50th percentile (median):", np.percentile(salaries, 50))
print("75th percentile:", np.percentile(salaries, 75))
```

Output:

```
25th percentile ≈ ~3350
50th percentile = median = 4000
75th percentile ≈ ~4600
```

Meaning:

| Percentile | Meaning                  |
| ---------- | ------------------------ |
| 25%        | 25% earn ≤ this amount   |
| 50%        | 50% earn ≤ this (median) |
| 75%        | top 25% earn above this  |

Used heavily in ML for scaling, detecting **outliers**, robust statistics.

