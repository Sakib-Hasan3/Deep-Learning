নিচে **Softmax + Cross-Entropy Loss** দিয়ে **backpropagation-এর numerical example** (একদম exam-friendly, step-by-step) দিলাম।
👉 এখানে তুমি দেখবে কেন softmax-এর gradient এত সুন্দরভাবে **(p-y)** হয়।

---

# ✅ Example: 3-Class Softmax Backprop (Numerical)

## 1) Given

ধরি 3টা class: **A, B, C**

Model output (logits):
[
z = [z_1, z_2, z_3] = [2,;1,;0]
]

True class = **A**
One-hot target:
[
y=[1,;0,;0]
]

---

# 2) Forward Pass

## Step A: Softmax probabilities

[
p_i=\frac{e^{z_i}}{\sum_{j=1}^{3} e^{z_j}}
]

Compute exponent:

* (e^2=7.389)
* (e^1=2.718)
* (e^0=1)

Sum:
[
S=7.389+2.718+1=11.107
]

Probabilities:
[
p_1=\frac{7.389}{11.107}=0.665
]
[
p_2=\frac{2.718}{11.107}=0.245
]
[
p_3=\frac{1}{11.107}=0.090
]

So,
[
p=[0.665,;0.245,;0.090]
]

---

## Step B: Cross-Entropy Loss

Categorical cross-entropy:
[
L=-\sum_{i=1}^{3} y_i \ln(p_i)
]

যেহেতু (y=[1,0,0]),
[
L=-\ln(p_1)=-\ln(0.665)=0.408
]

---

# 3) Backpropagation (Softmax + CE)

## 🔥 Key result:

Softmax + Cross-Entropy একসাথে নিলে,

[
\frac{\partial L}{\partial z_i}=p_i-y_i
]

So gradients w.r.t. logits:

[
\frac{\partial L}{\partial z_1}=0.665-1=-0.335
]
[
\frac{\partial L}{\partial z_2}=0.245-0=0.245
]
[
\frac{\partial L}{\partial z_3}=0.090-0=0.090
]

**Final:**
[
\nabla_z L = [-0.335,;0.245,;0.090]
]

👉 মানে: true class (A)-এর logit বাড়াতে হবে (negative gradient), অন্যগুলোর কমাতে হবে (positive gradient)।

---

# 4) Weight Update Example (Linear Layer)

ধরি logits আসে একটি linear layer থেকে:

[
z = Wx + b
]

একটা input vector:
[
x=[1,;2]
]

Weights (3 classes × 2 features):
[
W=
\begin{bmatrix}
0.10 & 0.20\
0.00 & 0.10\
-0.10 & 0.10
\end{bmatrix},
\quad
b=[0,;0,;0]
]

Learning rate:
[
\eta=0.1
]

---

## Step A: Gradient for W

Rule:
[
\frac{\partial L}{\partial W_i}=(p_i-y_i),x
]

### Class A (row 1)

[
\frac{\partial L}{\partial W_1}=-0.335[1,2]=[-0.335,;-0.670]
]

### Class B (row 2)

[
\frac{\partial L}{\partial W_2}=0.245[1,2]=[0.245,;0.490]
]

### Class C (row 3)

[
\frac{\partial L}{\partial W_3}=0.090[1,2]=[0.090,;0.180]
]

So,
[
\frac{\partial L}{\partial W}=
\begin{bmatrix}
-0.335 & -0.670\
0.245 & 0.490\
0.090 & 0.180
\end{bmatrix}
]

Bias gradient:
[
\frac{\partial L}{\partial b}=p-y=[-0.335,;0.245,;0.090]
]

---

## Step B: Gradient Descent Update

[
W_{\text{new}}=W-\eta\frac{\partial L}{\partial W}
]
[
b_{\text{new}}=b-\eta\frac{\partial L}{\partial b}
]

### Updated W rows

**Row 1 (A):**
[
[0.10,0.20]-0.1[-0.335,-0.670]=[0.1335,;0.2670]
]

**Row 2 (B):**
[
[0.00,0.10]-0.1[0.245,0.490]=[-0.0245,;0.0510]
]

**Row 3 (C):**
[
[-0.10,0.10]-0.1[0.090,0.180]=[-0.1090,;0.0820]
]

### Updated b

[
b_{\text{new}}=[0,0,0]-0.1[-0.335,0.245,0.090]=[0.0335,;-0.0245,;-0.0090]
]

---

# ⭐ Exam-Ready Summary

* Softmax:
  [
  p_i=\frac{e^{z_i}}{\sum_j e^{z_j}}
  ]
* Cross-Entropy:
  [
  L=-\sum y_i\ln(p_i)
  ]
* **Softmax + CE gradient (most important):**
  [
  \frac{\partial L}{\partial z}=p-y
  ]
* Linear layer update:
  [
  \frac{\partial L}{\partial W}=(p-y)x^T,\quad \frac{\partial L}{\partial b}=p-y
  ]

---

