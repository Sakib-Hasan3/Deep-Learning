## **Binary vs Multiclass Loss — Numerical Example (Step-by-Step, Bangla)**

![Image](https://www.researchgate.net/publication/342520628/figure/fig2/AS%3A907606478553088%401593401655516/Graph-of-Binary-Cross-Entropy-Loss-Function-Here-Entropy-is-defined-on-Y-axis-and.ppm)

![Image](https://gombru.github.io/assets/cross_entropy_loss/softmax_CE_pipeline.png)

![Image](https://www.researchgate.net/publication/342987800/figure/fig1/AS%3A913942624870401%401594912310090/Binary-vs-Multiclass-classification.jpg)

---

# 🔹 Part A: **Binary Classification Loss (Binary Cross-Entropy)**

### 🔸 Problem setup

ধরি একটি **Yes / No** সমস্যা।

* True label:
  [
  y = 1
  ]
* Model prediction (Sigmoid output):
  [
  \hat{y} = 0.8
  ]

---

### 🔸 Binary Cross-Entropy Formula

[
L = -\big[y\log(\hat{y}) + (1-y)\log(1-\hat{y})\big]
]

---

### 🔸 Numerical Calculation

[
L = -\big[1\cdot \log(0.8) + 0\cdot \log(0.2)\big]
]

[
L = -\log(0.8) \approx 0.223
]

✅ **Loss ছোট** → prediction ভালো

---

### ❌ Wrong & Confident Prediction

ধরি,
[
\hat{y} = 0.1
]

[
L = -\log(0.1) \approx 2.302
]

❌ **Loss খুব বড়** → ভুল কিন্তু confident prediction

---

### 🧠 Binary Intuition

* Correct + confident ⇒ loss কম
* Wrong + confident ⇒ loss অনেক বেশি

---

# 🔹 Part B: **Multiclass Classification Loss (Categorical Cross-Entropy)**

### 🔸 Problem setup

ধরি 3টা class:

* Cat
* Dog
* Cow

True class = **Dog**

One-hot encoded label:
[
y = [0,;1,;0]
]

Softmax output:
[
p = [0.2,;0.7,;0.1]
]

---

### 🔸 Categorical Cross-Entropy Formula

[
L = -\sum_{i=1}^{K} y_i \log(p_i)
]

---

### 🔸 Numerical Calculation

[
L = -[0\log(0.2) + 1\log(0.7) + 0\log(0.1)]
]

[
L = -\log(0.7) \approx 0.357
]

✅ **Loss কম** → সঠিক class-এ বেশি probability

---

### ❌ Wrong Prediction Case

ধরি,
[
p = [0.6,;0.3,;0.1]
]

[
L = -\log(0.3) \approx 1.204
]

❌ **Loss বেশি** → true class-এ probability কম

---

# 🔹 Binary vs Multiclass (Side-by-Side)

| Feature         | Binary Loss          | Multiclass Loss           |
| --------------- | -------------------- | ------------------------- |
| Output          | 1 probability        | Multiple probabilities    |
| Activation      | Sigmoid              | Softmax                   |
| Loss            | Binary Cross-Entropy | Categorical Cross-Entropy |
| True label      | 0 or 1               | One-hot vector            |
| Loss depends on | (\hat{y})            | True class probability    |

---

## 🧠 One-Line Memory Trick

> **Binary → one probability → BCE**
> **Multiclass → many probabilities → Softmax + CE**

---

## ✍️ Exam-Ready One Line

> **Binary cross-entropy measures error for two-class problems using sigmoid probabilities, while categorical cross-entropy evaluates multiclass predictions by penalizing low probability assigned to the true class.**

