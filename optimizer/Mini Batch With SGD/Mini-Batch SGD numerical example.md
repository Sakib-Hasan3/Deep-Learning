## **Mini-Batch SGD — Numerical Example (Step-by-Step)**

ধরি আমরা **linear regression** train করছি।

### Model

$$
\hat{y} = wx + b
$$

### Loss (per sample)

$$
\ell_i = \frac{1}{2} (y_i - \hat{y}_i)^2
$$

### Mini-batch cost (batch size $m$)

$$
J = \frac{1}{m} \sum_{i=1}^{m} \ell_i
$$
]


### Gradients (single sample)

$$
\frac{\partial \ell}{\partial w} = -(y-\hat{y})x, \qquad
\frac{\partial \ell}{\partial b} = -(y-\hat{y})
$$

Mini-batch gradient = average of the sample gradients.

---

# ✅ Given


Initial:
$$
w = 1, \quad b = 0, \quad \eta = 0.1
$$

Dataset (4 samples):

1. ((x=1,y=2))
2. ((x=2,y=3))
3. ((x=3,y=5))
4. ((x=4,y=4))


Batch size:
$$
m = 2
$$

Batches:

* **Batch-1:** (1,2), (2,3)
* **Batch-2:** (3,5), (4,4)

---

# ✅ Batch-1 Update (Samples 1 & 2)


## Sample 1: (1,2)

$$
\hat{y}_1 = 1 \cdot 1 + 0 = 1, \quad e_1 = y - \hat{y} = 2 - 1 = 1
$$
$$
\frac{\partial \ell_1}{\partial w} = -(1)(1) = -1, \quad
\frac{\partial \ell_1}{\partial b} = -(1) = -1
$$


## Sample 2: (2,3)

$$
\hat{y}_2 = 1 \cdot 2 + 0 = 2, \quad e_2 = 3 - 2 = 1
$$
$$
\frac{\partial \ell_2}{\partial w} = -(1)(2) = -2, \quad
\frac{\partial \ell_2}{\partial b} = -(1) = -1
$$


## Average gradients (divide by $m=2$)

$$
\frac{\partial J}{\partial w} = \frac{-1 + (-2)}{2} = -1.5
$$
$$
\frac{\partial J}{\partial b} = \frac{-1 + (-1)}{2} = -1
$$


## Update

$$
w = 1 - 0.1(-1.5) = 1.15
$$
$$
b = 0 - 0.1(-1) = 0.10
$$

---

# ✅ Batch-2 Update (Samples 3 & 4) using updated (w,b)


Now:
$$
w = 1.15, \quad b = 0.10
$$


## Sample 3: (3,5)

$$
\hat{y}_3 = 1.15 \cdot 3 + 0.10 = 3.55, \quad e_3 = 5 - 3.55 = 1.45
$$
$$
\frac{\partial \ell_3}{\partial w} = -(1.45)(3) = -4.35, \quad
\frac{\partial \ell_3}{\partial b} = -(1.45) = -1.45
$$


## Sample 4: (4,4)

$$
\hat{y}_4 = 1.15 \cdot 4 + 0.10 = 4.70, \quad e_4 = 4 - 4.70 = -0.70
$$
$$
\frac{\partial \ell_4}{\partial w} = -(-0.70)(4) = +2.80, \quad
\frac{\partial \ell_4}{\partial b} = -(-0.70) = +0.70
$$


## Average gradients

$$
\frac{\partial J}{\partial w} = \frac{-4.35 + 2.80}{2} = -0.775
$$
$$
\frac{\partial J}{\partial b} = \frac{-1.45 + 0.70}{2} = -0.375
$$


## Update

$$
w = 1.15 - 0.1(-0.775) = 1.2275
$$
$$
b = 0.10 - 0.1(-0.375) = 0.1375
$$

---


# ✅ Final Parameters (After 1 epoch, batch size 2)

$$
\boxed{w \approx 1.2275, \quad b \approx 0.1375}
$$

---

## 🧠 Key Takeaway

* **SGD:** 1 sample → 1 update
* **Mini-batch SGD:** 2/32/64 samples → **average gradient** → 1 update
* **Batch GD:** all samples → 1 update
