# Example 1, 1D vectors (ONLY `dot` works)

```python
import numpy as np

a = np.array([1, 2, 3])   # shape (3,)
b = np.array([4, 5, 6])   # shape (3,)

print("np.dot:", np.dot(a, b))
print("matmul? ->", end=" ")
try:
    print(np.matmul(a, b))
except Exception as e:
    print("ERROR:", e)
print("@ ? ->")
try:
    print(a @ b)
except Exception as e:
    print("ERROR:", e)
```

### Output

```
np.dot: 32
matmul -> ERROR
@ -> ERROR
```

### Explanation

* This is **vector dot product**: `1*4 + 2*5 + 3*6 = 32`
* `matmul` and `@` expect at least **2D** → they fail here
  ✅ So **use `dot` for pure 1D vector multiplication**

---

# Example 2, 2D Matrices (ALL THREE work)

```python
A = np.array([[1,2],[3,4]])   # shape (2,2)
B = np.array([[5,6],[7,8]])   # shape (2,2)

print("dot:\n", np.dot(A,B))
print("matmul:\n", np.matmul(A,B))
print("@:\n", A @ B)
```

### Output

```
dot:
 [[19 22]
 [43 50]]
matmul:
 [[19 22]
 [43 50]]
@:
 [[19 22]
 [43 50]]
```

### Explanation

* This is real **matrix multiplication** = row × column
* For **2D**, all three behave the same ✅
* In modern code, we normally use `A @ B` because it is cleaner

---

# Example 3, 3D (batch of matrices)

ONLY `matmul` and `@` work ✅
(`dot` will fail ❌)

```python
A = np.ones((3, 2, 3))      # 3 matrices, each 2x3
B = np.full((3, 3, 2), 2)   # 3 matrices, each 3x2

print("matmul:\n", np.matmul(A, B).shape)
print("@:\n", (A @ B).shape)

# Try dot
print("dot:", end=" ")
try:
    print(np.dot(A, B))
except Exception as e:
    print("ERROR:", e)
```

### Output

```
matmul: (3, 2, 2)
@: (3, 2, 2)
dot: ERROR ...
```

### Explanation

* This is **batch matrix multiplication**
* You have 3 matrices multiplying 3 matrices
* Output keeps the batch dimension: `(3, 2, 2)` ✅
* `dot` cannot handle batching — **it fails**

---

# Final Résumé (with examples meaning)

| Case                              | Use             | Why                         |
| --------------------------------- | --------------- | --------------------------- |
| 1D vectors `[1,2,3] · [4,5,6]`    | `np.dot`        | inner product               |
| 2D matrices `A (2x3) x B (3x2)`   | `@` or `matmul` | matrix multiplication       |
| 3D+ tensors `(batch, rows, cols)` | `matmul` or `@` | batch matrix multiplication |