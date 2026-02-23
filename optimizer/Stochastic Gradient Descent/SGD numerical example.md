<<<<<<< HEAD
## **SGD (Stochastic Gradient Descent) — Numerical Example (Step-by-Step)**

![Image](https://miro.medium.com/1%2Af9Wbr-pYMZ2AEzS2yp8EtQ.jpeg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AhJSLxZMjYVzgF5A_MoqeVQ.jpeg)

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fp484n1db128m716iomcv.jpg)

আমরা একটা **simple linear regression** নিয়ে SGD দেখাবো।

---

## 🔹 1️⃣ Problem Setup

Model:
[
\hat{y} = wx + b
]

Loss (single sample):
[
\ell = \frac{1}{2}(y-\hat{y})^2
]

---

## 🔹 2️⃣ Given Values

* Initial weight: (w = 1)
* Initial bias: (b = 0)
* Learning rate: (\eta = 0.1)

Training samples (একটা একটা করে ব্যবহার হবে):

1. ((x_1=1,; y_1=2))
2. ((x_2=2,; y_2=3))

---

# ✅ SGD Step-1 (Sample 1 ব্যবহার করে)

### 🔸 Forward pass

[
\hat{y}_1 = (1)(1) + 0 = 1
]

### 🔸 Error

[
e_1 = y_1 - \hat{y}_1 = 2 - 1 = 1
]

### 🔸 Gradients

[
\frac{\partial \ell}{\partial w} = -e_1 x_1 = -1 \cdot 1 = -1
]
[
\frac{\partial \ell}{\partial b} = -e_1 = -1
]

### 🔸 Update (SGD)

[
w = 1 - 0.1(-1) = 1.1
]
[
b = 0 - 0.1(-1) = 0.1
]

---

# ✅ SGD Step-2 (Sample 2 ব্যবহার করে)

### 🔸 Forward pass

[
\hat{y}_2 = (1.1)(2) + 0.1 = 2.3
]

### 🔸 Error

[
e_2 = 3 - 2.3 = 0.7
]

### 🔸 Gradients

[
\frac{\partial \ell}{\partial w} = -e_2 x_2 = -0.7 \cdot 2 = -1.4
]
[
\frac{\partial \ell}{\partial b} = -e_2 = -0.7
]

### 🔸 Update

[
w = 1.1 - 0.1(-1.4) = 1.24
]
[
b = 0.1 - 0.1(-0.7) = 0.17
]

---

## 🔹 3️⃣ Parameters After One Epoch (SGD)

[
\boxed{w = 1.24,\quad b = 0.17}
]

👉 লক্ষ্য করো:

* প্রতিটা **data point দিয়েই সাথে সাথে update** হয়েছে
* এইটাই **Stochastic Gradient Descent**

---

## 🔹 4️⃣ Why This Is “Stochastic”?

* প্রতিটা sample আলাদা direction দেখায়
* Update path **zig-zag** করে
* কিন্তু average direction ঠিক থাকে

---

## 🧠 Memory Trick

> **SGD = one sample → one update**

---

## ✍️ Exam-Ready One Line

> **In SGD, model parameters are updated after computing the loss gradient for each individual training example, resulting in fast but noisy convergence.**

=======
## **SGD (Stochastic Gradient Descent) — Numerical Example (Step-by-Step)**

![Image](https://miro.medium.com/1%2Af9Wbr-pYMZ2AEzS2yp8EtQ.jpeg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AhJSLxZMjYVzgF5A_MoqeVQ.jpeg)

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fp484n1db128m716iomcv.jpg)

আমরা একটা **simple linear regression** নিয়ে SGD দেখাবো।

---

## 🔹 1️⃣ Problem Setup

Model:
[
\hat{y} = wx + b
]

Loss (single sample):
[
\ell = \frac{1}{2}(y-\hat{y})^2
]

---

## 🔹 2️⃣ Given Values

* Initial weight: (w = 1)
* Initial bias: (b = 0)
* Learning rate: (\eta = 0.1)

Training samples (একটা একটা করে ব্যবহার হবে):

1. ((x_1=1,; y_1=2))
2. ((x_2=2,; y_2=3))

---

# ✅ SGD Step-1 (Sample 1 ব্যবহার করে)

### 🔸 Forward pass

[
\hat{y}_1 = (1)(1) + 0 = 1
]

### 🔸 Error

[
e_1 = y_1 - \hat{y}_1 = 2 - 1 = 1
]

### 🔸 Gradients

[
\frac{\partial \ell}{\partial w} = -e_1 x_1 = -1 \cdot 1 = -1
]
[
\frac{\partial \ell}{\partial b} = -e_1 = -1
]

### 🔸 Update (SGD)

[
w = 1 - 0.1(-1) = 1.1
]
[
b = 0 - 0.1(-1) = 0.1
]

---

# ✅ SGD Step-2 (Sample 2 ব্যবহার করে)

### 🔸 Forward pass

[
\hat{y}_2 = (1.1)(2) + 0.1 = 2.3
]

### 🔸 Error

[
e_2 = 3 - 2.3 = 0.7
]

### 🔸 Gradients

[
\frac{\partial \ell}{\partial w} = -e_2 x_2 = -0.7 \cdot 2 = -1.4
]
[
\frac{\partial \ell}{\partial b} = -e_2 = -0.7
]

### 🔸 Update

[
w = 1.1 - 0.1(-1.4) = 1.24
]
[
b = 0.1 - 0.1(-0.7) = 0.17
]

---

## 🔹 3️⃣ Parameters After One Epoch (SGD)

[
\boxed{w = 1.24,\quad b = 0.17}
]

👉 লক্ষ্য করো:

* প্রতিটা **data point দিয়েই সাথে সাথে update** হয়েছে
* এইটাই **Stochastic Gradient Descent**

---

## 🔹 4️⃣ Why This Is “Stochastic”?

* প্রতিটা sample আলাদা direction দেখায়
* Update path **zig-zag** করে
* কিন্তু average direction ঠিক থাকে

---

## 🧠 Memory Trick

> **SGD = one sample → one update**

---

## ✍️ Exam-Ready One Line

> **In SGD, model parameters are updated after computing the loss gradient for each individual training example, resulting in fast but noisy convergence.**

>>>>>>> f45ebbad1686e699afe9932c4175eeff501d254b
