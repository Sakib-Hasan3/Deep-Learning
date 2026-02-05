## **Gradient Descent Optimizers — সহজ ব্যাখ্যা (Intuition + Comparison)**

![Image](https://sebastianraschka.com/images/faq/gradient-optimization/ball.png)

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fp484n1db128m716iomcv.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1000/1%2AX9SaxFM6_sBOAMY9TaGsKw.png)

![Image](https://mdrk.io/content/images/2024/04/momentum_optimization_trajectory-1.png)

---

## 🔹 1) Gradient Descent কী?

**Gradient Descent** হলো এমন একটি optimization পদ্ধতি যা
👉 **loss/cost function কমানোর জন্য parameters (weights, bias) আপডেট করে**।

Basic update rule:
[
\theta \leftarrow \theta - \eta \nabla J(\theta)
]

* (\eta) = learning rate
* (\nabla J) = gradient (ঢাল)

---

## 🔹 2) Types of Gradient Descent (Data ব্যবহারের ভিত্তিতে)

### ✅ **Batch Gradient Descent**

* পুরো dataset একসাথে ব্যবহার
* Stable কিন্তু **slow**

**Use when:** ছোট dataset

---

### ✅ **Stochastic Gradient Descent (SGD)**

* একেকটা sample দিয়ে update
* **Fast কিন্তু noisy**

**Use when:** খুব বড় dataset

---

### ✅ **Mini-batch Gradient Descent**

* ছোট batch (32, 64, 128)
* Speed + stability balanced

**👉 Practical default choice**

---

## 🔹 3) Popular Gradient Descent Optimizers

### 🔸 **SGD (Vanilla)**

[
\theta \leftarrow \theta - \eta \nabla J(\theta)
]

✔ Simple
❌ Zig-zag, slow convergence

---

### 🔸 **Momentum**

আগের gradient-এর দিক ধরে এগোয়।

[
v_t=\beta v_{t-1}+\eta \nabla J
]
[
\theta \leftarrow \theta - v_t
]

✔ Faster
✔ Oscillation কম
❌ Extra hyperparameter

---

### 🔸 **Nesterov Accelerated Gradient (NAG)**

আগে “peek” করে, তারপর update।

✔ Momentum-এর চেয়েও smart
✔ Overshoot কম

---

### 🔸 **Adagrad**

Parameter-wise adaptive learning rate।

[
\theta \leftarrow \theta - \frac{\eta}{\sqrt{G+\epsilon}} \nabla J
]

✔ Sparse data-এ ভালো
❌ Learning rate দ্রুত ছোট হয়ে যায়

---

### 🔸 **RMSProp**

Adagrad-এর সমস্যা ঠিক করে।

✔ Stable
✔ RNN/CNN-এ ভালো
❌ LR tuning দরকার

---

### 🔸 **Adam (Most Popular)**

Momentum + RMSProp একসাথে।

[
m_t=\beta_1 m_{t-1}+(1-\beta_1)g_t
]
[
v_t=\beta_2 v_{t-1}+(1-\beta_2)g_t^2
]

✔ Fast convergence
✔ Default choice
❌ Sometimes overfits / sharp minima

---

### 🔸 **AdamW**

Adam + proper weight decay।

✔ Better generalization
✔ Modern best practice

---

## 🔹 4) Optimizers Comparison Table

| Optimizer | Speed         | Stability | Best Use            |
| --------- | ------------- | --------- | ------------------- |
| SGD       | Slow          | Low       | Simple baseline     |
| Momentum  | Medium        | Medium    | Faster SGD          |
| NAG       | Fast          | High      | Smooth convergence  |
| Adagrad   | Medium        | Medium    | Sparse features     |
| RMSProp   | Fast          | High      | RNN/CNN             |
| **Adam**  | **Very Fast** | **High**  | Default choice      |
| **AdamW** | **Very Fast** | **High**  | Best generalization |

---

## 🔹 5) Which Optimizer to Use — When?

| Situation         | Optimizer      |
| ----------------- | -------------- |
| Just starting     | **Adam**       |
| Overfitting issue | **AdamW**      |
| Sparse data (NLP) | Adagrad / Adam |
| Very large data   | SGD + Momentum |
| RNN unstable      | RMSProp / Adam |

---

## 🧠 Memory Trick

> **SGD walks, Momentum runs, Adam thinks.**

---

## ✍️ Exam-Ready One Line

> **Gradient descent optimizers iteratively update model parameters to minimize loss, with advanced variants like Adam and AdamW improving convergence speed and stability.**

চাও তো আমি পরের ধাপে

* **Adam vs SGD numerical example**,
* **learning rate schedules**,
* বা **exam 5-mark answer (with formulas)**
  তৈরি করে দিতে পারি ✔
