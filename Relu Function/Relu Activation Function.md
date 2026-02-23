## **ReLU (Rectified Linear Unit) Activation Function — Graph সহ ব্যাখ্যা**

![Image](https://www.researchgate.net/publication/343675998/figure/fig3/AS%3A924834280267785%401597509083229/Graph-of-ReLu-activation-function.ppm)

![Image](https://www.researchgate.net/publication/359884439/figure/fig3/AS%3A1147051651932161%401650489833478/ReLU-activation-function-and-its-derivative.png)

![Image](https://www.researchgate.net/publication/354971308/figure/fig1/AS%3A1080246367457377%401634562212739/Curves-of-the-Sigmoid-Tanh-and-ReLu-activation-functions.jpg)

![Image](https://www.researchgate.net/publication/327435257/figure/fig4/AS%3A742898131812354%401554132125449/Activation-Functions-ReLU-Tanh-Sigmoid.ppm)

---

## 🔹 1) ReLU কী?

**ReLU (Rectified Linear Unit)** হলো সবচেয়ে বেশি ব্যবহৃত **activation function** (বিশেষ করে Deep Neural Network-এ)।

গাণিতিকভাবে,

[
\text{ReLU}(x) = \max(0, x)
]

---

## 🔹 2) Output Range

[
\text{Output} \in [0, \infty)
]

* Negative input → **0**
* Positive input → **same value**

---

## 🔹 3) Graph দেখে Intuition (খুব গুরুত্বপূর্ণ)

### (a) x < 0

* Output = 0
* Neuron **inactive**
* Gradient = 0

### (b) x > 0

* Output = x
* Straight line (slope = 1)
* Gradient strong → **fast learning**

👉 Graphটা দেখতে **broken straight line** এর মতো।

---

## 🔹 4) Derivative (Backpropagation-এর জন্য)

[
\text{ReLU}'(x)=
\begin{cases}
0, & x<0\
1, & x>0
\end{cases}
]

(x = 0 এ derivative undefined, বাস্তবে 0 বা 1 ধরা হয়)

---

## 🔹 5) কেন ReLU এত জনপ্রিয়? (Key Intuition)

✔ **Vanishing Gradient নেই** (x>0 হলে)
✔ Very fast computation
✔ Sparse activation (সব neuron একসাথে active হয় না)
✔ Deep network-এ খুব ভালো কাজ করে

👉 তাই আজকাল **hidden layers-এর default choice = ReLU**

---

## 🔹 6) ReLU vs Sigmoid vs Tanh (Graph-based তুলনা)

| Feature            | Sigmoid | Tanh      | ReLU      |
| ------------------ | ------- | --------- | --------- |
| Output range       | (0,1)   | (−1,1)    | [0,∞)     |
| Zero-centered      | ❌       | ✅         | ❌         |
| Vanishing gradient | ❌ High  | ⚠️ Medium | ✅ Low     |
| Computation        | Slow    | Medium    | Very fast |
| Deep networks      | ❌       | ⚠️        | ✅ Best    |

---

## 🔹 7) Dead Neuron Problem (ReLU-এর drawback)

যদি:

* Weight update এমন হয় যে
* neuron সবসময় negative input পায়

তাহলে:
[
x<0 \Rightarrow \text{ReLU}(x)=0
\Rightarrow \text{Gradient}=0
]

👉 Neuron আর শেখে না
👉 একে বলে **Dead ReLU**

---

## 🔹 8) Dead ReLU সমাধান

✔ **Leaky ReLU**
[
f(x)=
\begin{cases}
0.01x,& x<0\
x,& x>0
\end{cases}
]

✔ **Parametric ReLU (PReLU)**
✔ Proper weight initialization (He initialization)

---

## 🔹 9) Small Numerical Example

ধরি:
[
x = -2 \Rightarrow \text{ReLU}(-2)=0
]

[
x = 3 \Rightarrow \text{ReLU}(3)=3
]

Derivative:

* at (x=-2): 0
* at (x=3): 1

---

## 🧠 Memory Trick

> **ReLU = “If negative, kill it; if positive, pass it”**

---

## ✍️ Exam-Ready One Line

> **ReLU is a piecewise linear activation function defined as max(0, x) that accelerates training and avoids vanishing gradients, making it ideal for deep neural networks.**

---


