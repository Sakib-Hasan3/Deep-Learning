## **Leaky ReLU & Parametric ReLU (PReLU)**

*(Dead ReLU problem-এর smart solutions — graph + intuition সহ)*

![Image](https://www.researchgate.net/publication/376410479/figure/fig15/AS%3A11431281211482860%401702404866700/A-plot-of-the-leaky-ReLU-activation-function-with-leak-factor-1-10-and-the-ReLU.png)

![Image](https://dl.acm.org/cms/attachment/1c0498a6-7f83-4f52-b3f6-732bbe32126a/image1.jpeg)

![Image](https://www.researchgate.net/publication/358306930/figure/fig2/AS%3A1119417702318091%401643901386378/ReLU-activation-function-vs-LeakyReLU-activation-function.png)

![Image](https://www.researchgate.net/publication/334389306/figure/fig8/AS%3A779352161677313%401562823443351/llustration-of-output-of-ELU-vs-ReLU-vs-Leaky-ReLU-function-with-varying-input-values.ppm)

---

## 🔹 1️⃣ Why Leaky ReLU & PReLU?

**Problem with ReLU:**
[
\text{ReLU}(x)=\max(0,x)
]

* (x<0 \Rightarrow) output = 0
* gradient = 0
  👉 neuron **dead** হয়ে যেতে পারে (আর শেখে না)

**Solution idea:**
👉 Negative side-এ একটু হলেও gradient থাকতে দাও

---

## 🔹 2️⃣ Leaky ReLU (LReLU)

### ✅ Definition

Leaky ReLU negative input-এর জন্য ছোট একটা slope দেয়।

[
\text{LeakyReLU}(x)=
\begin{cases}
x, & x>0\
\alpha x, & x<0
\end{cases}
]

যেখানে সাধারণত,
[
\alpha = 0.01
]

---

### 🔹 Graph-based Intuition

* Positive side → ReLU-এর মতো
* Negative side → হালকা ঢাল (slope = α)
* Gradient **কখনোই 0 হয় না**

👉 Dead neuron সমস্যা অনেক কমে যায়

---

### 🔹 Derivative

[
\frac{d}{dx}=
\begin{cases}
1,& x>0\
\alpha,& x<0
\end{cases}
]

---

### ✅ Advantages (Leaky ReLU)

✔ Dead ReLU সমস্যা কমায়
✔ Simple & fast
✔ ReLU-এর প্রায় সব সুবিধা বজায় রাখে

---

### ❌ Disadvantages (Leaky ReLU)

❌ (\alpha) manually set করতে হয়
❌ Optimal (\alpha) সব dataset-এর জন্য same না

---

## 🔹 3️⃣ Parametric ReLU (PReLU)

### ✅ Definition

PReLU-তে (\alpha) **fixed না**, network নিজেই শেখে।

[
\text{PReLU}(x)=
\begin{cases}
x,& x>0\
\alpha x,& x<0
\end{cases}
\quad\text{where }\alpha\text{ is trainable}
]

---

### 🔹 Intuition

* Model নিজেই ঠিক করে নেয়
  👉 negative side কতটা allow করবে
* বেশি flexible than Leaky ReLU

---

### 🔹 Derivative

[
\frac{d}{dx}=
\begin{cases}
1,& x>0\
\alpha,& x<0
\end{cases}
]
এবং (\alpha) নিজেও gradient দিয়ে update হয়।

---

### ✅ Advantages (PReLU)

✔ Dead neuron প্রায় পুরোপুরি solve
✔ Adaptive (data-driven)
✔ Very good for deep CNNs

---

### ❌ Disadvantages (PReLU)

❌ Extra parameter ⇒ overfitting risk
❌ Slightly more computation
❌ Small datasets-এ ভালো নাও হতে পারে

---

## 🔹 4️⃣ ReLU vs Leaky ReLU vs PReLU (Comparison)

| Feature        | ReLU      | Leaky ReLU   | PReLU      |
| -------------- | --------- | ------------ | ---------- |
| Negative slope | 0         | Fixed (0.01) | Learnable  |
| Dead neuron    | ❌ High    | ⚠️ Low       | ✅ Very low |
| Parameters     | None      | None         | Extra α    |
| Speed          | Very fast | Very fast    | Fast       |
| Flexibility    | Low       | Medium       | High       |

---

## 🧠 Memory Trick

> **ReLU kills negatives, Leaky ReLU lets them whisper, PReLU lets the network decide.**

---

## ✍️ Exam-Ready One Line

* **Leaky ReLU** allows a small, fixed gradient for negative inputs to mitigate dead neurons.
* **PReLU** generalizes Leaky ReLU by learning the negative slope during training, improving flexibility at the cost of extra parameters.

---

