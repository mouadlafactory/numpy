## ✅ Shapes

```
(2 × 3)  @  (3 × 2)   →   (2 × 2)
```

Because:

* The **inner dimensions** 3 = 3 ✅
* The **outer dimensions** become the result → (2×2)

---

## ✅ Example

```python
import numpy as np

A = np.array([[1,2,3],
              [4,5,6]])    # shape (2,3)

B = np.array([[1,2],
              [3,4],
              [5,6]])      # shape (3,2)

C = A @ B
print(C)
```

### ✅ Output

```
[[22 28]
 [49 64]]
```

---

## ✅ Why these numbers?

Take **first row of A** and **first column of B**:

```
[1 2 3] · [1 3 5] = 1*1 + 2*3 + 3*5 = 22
```

Then same row · second column:

```
[1 2 3] · [2 4 6] = 1*2 + 2*4 + 3*6 = 28
```

Then second row of A:

```
[4 5 6] · [1 3 5] = 4*1 + 5*3 + 6*5 = 49
[4 5 6] · [2 4 6] = 4*2 + 5*4 + 6*6 = 64
```

So the result matrix is:

```
[ [22, 28],
  [49, 64] ]
```

---

## ✅ Visual Diagram

```
     (2×3)         (3×2)
   ┌────────┐    ┌───────┐
   │1 2 3   │    │1 2    │
A  │4 5 6   │ @  │3 4    │ = (2×2)
   └────────┘    │5 6    │
                 └───────┘
```

---

## ✅ Summary

| A shape | B shape | Valid? | Result |
| ------- | ------- | ------ | ------ |
| (2×3)   | (3×2)   | ✅      | (2×2)  |
